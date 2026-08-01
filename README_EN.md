======================================================================
PORTABLE EDGESTREAM READER (ESR) v1.8.5-beta — FINAL DOCUMENTATION
======================================================================
Software Developers: timurer & Guy (Google AI)
Release Date: July 2026
License: MIT License (Free & open-source use)
Platform: Windows 11 / 10 (x64)
----------------------------------------------------------------------

1. PROJECT PASSPORT & BACKGROUND
EdgeStream Reader (ESR) is a portable, fault-tolerant application 
for reading e-books and documents with an integrated asynchronous 
streaming text-to-speech (TTS) engine. Developed as an efficient 
alternative to bloated readers, it combines a minimal CustomTkinter 
GUI with advanced text preprocessing algorithms.

2. ARCHITECTURE & CODE STRUCTURE (5 CORE BLOCKS)
The codebase is strictly structured and divided into isolated zones:
• BLOCK 1: Main GUI & Environment Initialization. Handles layouts, 
adaptive widgets, context menus, and secure icon.ico asset allocation 
for both primary and secondary frames.
• BLOCK 1.2: Settings Tab Manager. Coordinates Light/Dark modes, background 
sub-layer presets ("Book Sepia", "Night OLED"), and houses release records 
with clickable README redirections.
• BLOCK 1.3: Interactive Accent Dictionary & Bookmark Module. Dispatches 
child Toplevel instances, processes click vectors, and outputs saved coordinates 
in real-time utilizing global JSON chunk indexes.
• BLOCK 2: Universal Parser & Text Normalizer. Integrates document text 
extractors, the surgical "Notepad++ Killer" cleanup logic, E/Ё letter mapping, 
and numerical quantity decline tables.
• BLOCK 3: Streaming Player & Async RAM Prefetcher. Controls background 
audio buffering straight into io.BytesIO memory arrays (diskless), handles sequential 
playback, and propagates colors to the active reading window (ESRReaderWindow).
• BLOCK 4: Energy-Saving "Smart Pause" & Exporter. Pins execution lines, 
manages button states, flushes RAM blocks on stop, and splices consecutive 
MP3 streams together for bulk exports.
• BLOCK 5: JSON State Serialization Logic. Maintains and coldly restores 
runtime metrics (file path, active pointer, system theme, color palettes, and tempo).

3. KEY FUNCTION OF v1.8.5-beta
• Universal Format Support: Direct extraction of raw files (.txt), 
e-books (.fb2, .epub), and Microsoft Word files (.docx).
• "Notepad++ Killer" Parsing: Intelligent structural optimization, stripping 
OCR scan debris, multiple tabs, trailing ellipses, and broken brackets 
that disrupt speaker intonation.
• Intelligent Declanations: Automatically parses and inflects calendar years, 
cities, and metric abbreviations (kg, km, m, rub) with accurate grammar 
cases adjusted to the leading integer.
• Cutting-Edge RAM-Caching (Diskless): Complete elimination of physical disk 
temp writes. Audio stream tracks feed straight to RAM via BytesIO, mitigating 
SSD hardware wear and micro-stutters.
• Asynchronous Prefetching Queue: A proactive worker thread caches up to 
4 chunks ahead directly into memory, providing gapless transitions between paragraphs.
• Synchronized Prompter Module: Auxiliary reader viewport (ESRReaderWindow) 
dynamically mirrors core framework style maps and firmly locks the icon.ico target.
• Hardened Bookmark Core: Structural fixes blocking KeyError exceptions upon 
loading fresh files, paired with native bm_display mapping and index-based drops.
• Contextual E/Ё Calibration: Resolves critical homographs (все -> всё, еще -> ещё) 
to ensure optimal speech production.
• Local Accent Dictionary: Custom esr_user_dict.json file allows manual override 
of uncommon nouns and names, preserving strict case registers.

3.1. "EXPORT AUDIO" FUNCTION SPECIFICATION & FORMATS
The application supports advanced high-speed text-to-audio export capabilities:
• Online Engine (Edge-TTS) — performs batch scanning, splices memory streams 
  inside RAM, and exports the final audio strictly in MP3 format.
• Offline Engine (SAPI5) — executes paragraph-by-paragraph rendering via 
  native Windows codecs and exports the output file in uncompressed WAV format.

Audio generation can be executed using four flexible operational modes:
1. Full Export — converts the entire document text from the absolute beginning 
   to the very end (runs silently in the background, without triggering playback).
2. Export from Pause — converts text starting exactly from the active playback 
   pause position up to the end of the file.
3. Export from Marker — processes text from a manually designated location 
   all the way to the end of the book.
4. Export Selection Only — generates an audio track strictly for the portion of 
   text currently highlighted by the user's cursor.

🔥 IMPORTANT: Setting the reading marker for the third mode is executed in 
a single action — LEFT-CLICK (LMB) on any desired paragraph within the 
main text interface to instantly snap and lock the target marker!

4. CONTROL HOTKEYS & PLAYER NAVIGATION
• "► Speak" Button — Launches speech production from the active line.
• "⏸ Pause / ► Resume" Button — Suspends speech while recording current positions. 
Turns green upon cold boot to signify wake readiness.
• "⬛ Stop" Button — Resets current milestones, wipes RAM arrays, and unloads books 
while saving visual presets and global speech tempo.
• List Click Actions — Selects targeted lines for pointer relocation or data drops.
• ⚠ Warning: Altering the tempo slider during active listening propagates down 
the stream within 3-4 chunks due to the running prefetch index.

5. SYSTEM REQUIREMENTS & DEPENDENCIES
To deploy the portable iteration from the raw source code, ensure:
• Python Interpreter 3.14+
• Libraries: customtkinter, edge-tts, pygame-ce, beautifulsoup4, 
lxml, ebooklib, python-docx.
• Active internet access (required for Microsoft Cloud Speech API).
• Offline Synthesis Specification (SAPI5):
    - To enable voice production and file exporting via the offline engine, 
      the "SAPI 5 TTS" offline voices (Dariya, Dmitry, Svetlana, Ekaterina) 
      must be installed in your operating system.
    - To use advanced high-quality Microsoft Native voices, you must install 
      the NaturalVoiceSAPIAdapter utility:
      * Download and unpack the archive into a separate folder (do not delete 
        or relocate this directory as long as the voices are active in your system).
      * Launch the Installer.exe file, configure your desired settings, 
        and click both the "Install 32-bit" and "Install 64-bit" buttons.

----------------------------------------------------------------------
Software is distributed for FREE, on an "AS IS" basis. The developers 
assume no liability for application failures. All legal naming rights 
concerning "timurer" are protected by the IT community.
======================================================================
