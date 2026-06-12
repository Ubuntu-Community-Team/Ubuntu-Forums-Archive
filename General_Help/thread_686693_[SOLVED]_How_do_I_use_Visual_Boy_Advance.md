---
title: "[SOLVED] How do I use Visual Boy Advance?"
date: 2008-02-03
forum: General Help
---

### Post by WarMonkey on 2008-02-03
I installed visual boy advance and its gtk gui (visualboyadvance-gtk), but when I try to load a rom it just shows a grey box where the game should be. I read somewhere that the gtk package has a lot of bugs in it, so now I'm trying to run it from the command line. However, when the help screen comes up, I can't find an option to choose the location for a rom.

```
VisualBoyAdvance version 1.8.0 [SDL]
Searching for file VisualBoyAdvance.cfg
Searching current directory: /usr/share/menu
Searching home directory: /home/yitzhak/.vba
Searching system config directory: /etc
Reading configuration file.
Missing image name
VisualBoyAdvance [option ...] file

Options:
  -1, --video-1x               1x
  -2, --video-2x               2x
  -3, --video-3x               3x
  -4, --video-4x               4x
  -F, --fullscreen             Full screen
  -G, --gdb=PROTOCOL           GNU Remote Stub mode:
                                tcp      - use TCP at port 55555
                                tcp:PORT - use TCP at port PORT
                                pipe     - use pipe transport
  -N, --no-debug               Don't parse debug information
  -S, --flash-size=SIZE        Set the Flash size
      --flash-64k               0 -  64K Flash
      --flash-128k              1 - 128K Flash
  -T, --throttle=THROTTLE      Set the desired throttle (5...1000)
  -Y, --yuv=TYPE               Use YUV overlay for drawing:
                                0 - YV12
                                1 - UYVY
                                2 - YVYU
                                3 - YUY2
                                4 - IYUV
  -b, --bios=BIOS              Use given bios file
  -c, --config=FILE            Read the given configuration file
  -d, --debug                  Enter debugger
  -f, --filter=FILTER          Select filter:
      --filter-normal            0 - normal mode
      --filter-tv-mode           1 - TV Mode
      --filter-2xsai             2 - 2xSaI
      --filter-super-2xsai       3 - Super 2xSaI
      --filter-super-eagle       4 - Super Eagle
      --filter-pixelate          5 - Pixelate
      --filter-motion-blur       6 - Motion Blur
      --filter-advmame           7 - AdvanceMAME Scale2x
      --filter-simple2x          8 - Simple2x
      --filter-bilinear          9 - Bilinear
      --filter-bilinear+        10 - Bilinear Plus
      --filter-scanlines        11 - Scanlines
      --filter-hq2x             12 - hq2x
      --filter-lq2x             13 - lq2x
  -h, --help                   Print this help
  -i, --ips=PATCH              Apply given IPS patch
  -p, --profile=[HERTZ]        Enable profiling
  -s, --frameskip=FRAMESKIP    Set frame skip (0...9)
  -t, --save-type=TYPE         Set the available save type
      --save-auto               0 - Automatic (EEPROM, SRAM, FLASH)
      --save-eeprom             1 - EEPROM
      --save-sram               2 - SRAM
      --save-flash              3 - FLASH
      --save-sensor             4 - EEPROM+Sensor
      --save-none               5 - NONE
  -v, --verbose=VERBOSE        Set verbose logging (trace.log)
                                  1 - SWI
                                  2 - Unaligned memory access
                                  4 - Illegal memory write
                                  8 - Illegal memory read
                                 16 - DMA 0
                                 32 - DMA 1
                                 64 - DMA 2
                                128 - DMA 3
                                256 - Undefined instruction
                                512 - AGBPrint messages

Long options only:
      --agb-print              Enable AGBPrint support
      --auto-frameskip         Enable auto frameskipping
      --ifb-none               No interframe blending
      --ifb-motion-blur        Interframe motion blur
      --ifb-smart              Smart interframe blending
      --no-agb-print           Disable AGBPrint support
      --no-auto-frameskip      Disable auto frameskipping
      --no-ips                 Do not apply IPS patch
      --no-mmx                 Disable MMX support
      --no-pause-when-inactive Don't pause when inactive
      --no-rtc                 Disable RTC support
      --no-show-speed          Don't show emulation speed
      --no-throttle            Disable thrrotle
      --pause-when-inactive    Pause when inactive
      --rtc                    Enable RTC support
      --show-speed-normal      Show emulation speed
      --show-speed-detailed    Show detailed speed data

```

I am a newbie so please bear with me. Thanks!

---

### Post by c0rdawg on 2008-02-18
try getting vbaexpress. It's a nice GUI for working with vba...

---

### Post by WarMonkey on 2008-02-23
> **c0rdawg said:**
> try getting vbaexpress. It's a nice GUI for working with vba...

Thanks! It works nicely. Problem Solved.

---

