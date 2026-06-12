---
title: "OpenShot Crashes when importing videos."
date: 2023-04-30
forum: General Help
---

### Post by arius88 on 2023-04-30
I've recently installed OpenShot Editor for the first time. Unfortunately the program keeps crashing when I import videos. Certain videos (a select few) seem to work okay, but the rest just immediately cause the program to crash. There's no obvious difference between the videos that work and the ones that don't, but the ones that work always work and the ones that don't always don't.   I've done some googling;  it seems like this is an extremely common problem, but unfortunately I haven't found a solution that works for me. I increased the cache to 2048MB. No improvement. I tried installing a recent build, but that didn't work either. I uninstalled it and reinstalled from Discovery, same problem.   Any advice?  I'm using Lubuntu 22.04 on a Lenovo ThinkCentre circa 2012.   Probably going to have to go with my #2 choice for a video editing program if I can't get OpenShot to work.

---

### Post by ajgreeny on 2023-05-01
Are the videos different file types, eg mpg, mp4, mkv, webm? What versions of Openshot have you tried?
I am using the PPA version 3.0.2 I think but I'm on another computer at the moment so not certain of the version but whatever it is works perfectly on my 10 year old desktop running Xubuntu 22.04 with 8G ram.

Also show us the output from command ```
inxi -Fzx
```using code tags please to show details of your hardware.

---

### Post by Holger_Gehrke on 2023-05-01
Have you tried running the program from the command line ? Most programs on Linux send diagnostic messages and errors to standard output and / or standard error. These aren't shown when starting a program graphically, but when you start them from a terminal you can see them in that terminal. This can give you an idea what is going wrong.

Holger

---

### Post by arius88 on 2023-05-09
Thank you for the suggestions, and sorry for the slow reply. It's been a busy week.    I ran inxi -Fzx and got the following:  System:   Kernel: 5.19.0-41-generic x86_64 bits: 64 compiler: N/A     Desktop: LXQt 0.17.1 Distro: Ubuntu 22.04.2 LTS (Jammy Jellyfish) Machine:   Type: Desktop System: LENOVO product: 0401U3U v: ThinkCentre A70z     serial:    Mobo: LENOVO model: N/A serial:  BIOS: LENOVO     v: 98KT26AUS date: 03/21/2011 Battery:   Device-1: apple_mfi_fastcharge model: N/A charge: N/A status: N/A CPU:   Info: dual core model: Intel Core2 Duo E7500 bits: 64 type: MCP     arch: Core Yorkfield rev: A cache: L1: 128 KiB L2: 3 MiB   Speed (MHz): avg: 1599 high: 1603 min/max: 1603/2936 cores: 1: 1596     2: 1603 bogomips: 11705   Flags: ht lm nx pae sse sse2 sse3 sse4_1 ssse3 vmx Graphics:   Device-1: Intel 4 Series Integrated Graphics vendor: Lenovo driver: i915     v: kernel bus-ID: 00:02.0   Device-2: Chicony USB 2.0 Camera type: USB driver: uvcvideo bus-ID: 1-2:2   Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: modesetting     unloaded: fbdev,vesa gpu: i915 resolution: 1440x900~60Hz   OpenGL: renderer: Mesa Intel G41 (ELK) v: 2.1 Mesa 22.2.5     direct render: Yes Audio:   Device-1: Intel NM10/ICH7 Family High Definition Audio vendor: Lenovo     driver: snd_hda_intel v: kernel bus-ID: 00:1b.0   Sound Server-1: ALSA v: k5.19.0-41-generic running: yes   Sound Server-2: PulseAudio v: 15.99.1 running: yes   Sound Server-3: PipeWire v: 0.3.48 running: yes Network:   Device-1: Broadcom BCM43225 802.11b/g/n driver: bcma-pci-bridge v: N/A     bus-ID: 02:00.0   Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet     vendor: Lenovo driver: r8169 v: kernel port: e800 bus-ID: 03:00.0   IF: enp3s0 state: down mac:    IF-ID-1: wlp2s0b1 state: up mac:  Drives:   Local Storage: total: 465.76 GiB used: 17.67 GiB (3.8%)   ID-1: /dev/sda vendor: Seagate model: ST3500418AS size: 465.76 GiB Partition:   ID-1: / size: 195.5 GiB used: 17.67 GiB (9.0%) fs: ext4 dev: /dev/sda4 Swap:   ID-1: swap-1 type: file size: 512 MiB used: 0 KiB (0.0%) file: /swapfile Sensors:   System Temperatures: cpu: 47.0 C mobo: N/A   Fan Speeds (RPM): N/A Info:   Processes: 174 Uptime: 1h 29m Memory: 7.64 GiB used: 1.53 GiB (20.1%)   Init: systemd runlevel: 5 Compilers: gcc: 11.3.0 Packages: 2109 Shell: Bash   v: 5.1.16 inxi: 3.3.13    ------  I ran openshot-qt from terminal, and imported one video no problem, then imported a few videos at once and it crashed (I couldn’t remember which videos make it crash and which ones don’t, so I just tried to open a few at once knowing that would definitely cause the problem.) This is the output I got from the time it started opening OpenShot to the moment it crashed:  ------  Loaded modules from: /usr/lib/python3/dist-packages/openshot_qt INFO app: ------------------------------------------------ INFO app:             Tue May  9 09:16:47 2023             INFO app:               Starting new session               INFO app: ------------------------------------------------ INFO app:             OpenShot (version 3.1.1)             INFO app: ------------------------------------------------ INFO app: openshot-qt version: 3.1.1 INFO app: libopenshot version: 0.3.2 INFO app: platform: Linux-5.19.0-41-generic-x86_64-with-glibc2.35 INFO app: processor: x86_64 INFO app: machine: x86_64 INFO app: python version: 3.10.6 INFO app: qt5 version: 5.15.3 INFO app: pyqt5 version: 5.15.6 INFO project_data: Setting profile to HD 720p 30 fps INFO project_data: Apply default audio playback settings: 44100, 2 channels INFO app: checking babl_ext_path: /usr/lib/python3/dist-packages/openshot_qt/lib/babl-ext Screen VGA-1    devicePixelRatio: 1.0    logicalDotsPerInch: 96.02521008403362    physicalDotsPerInch: 89.6470588235294    availableSizes: PyQt5.QtCore.QSize(1440, 868) INFO language: Qt Detected Languages: ['en-CA'] INFO language: LANG Environment Variable: en_CA.UTF-8 INFO language: LOCALE Environment Variable:  INFO language: OpenShot Preference Language: Default INFO app: Setting font to /usr/lib/python3/dist-packages/openshot_qt/images/fonts/Ubuntu-R.ttf INFO app: Setting custom dark theme INFO logger_libopenshot: Connecting to libopenshot with debug port: 5556 INFO ui_util: Initializing UI for MainWindow INFO thumbnail: Starting thumbnail server listening on ('127.0.0.1', 37515) Sandboxing disabled by user. INFO webengine: WebEngine backend initializing INFO version: Found current version: {'error_rate_stable': 0.5, 'trans_rate_unstable': 0.001, 'error_rate_unstable': 0.05, 'openshot_version': '3.1.1', 'trans_rate_stable': 0.01} INFO transition_model: updating transitions model. INFO effects_model: updating effects model. INFO emoji_model: updating emoji model. INFO sentry: Sentry initialized for 'production': 0.5 sample rate, 0.01 transaction rate INFO main_window: InitCacheSettings INFO main_window: cache-mode: CacheMemory INFO main_window: cache-limit-mb: 2048 INFO main_window: cache-ahead-percent: 0.7 INFO main_window: cache-preroll-min-frames: 24 INFO main_window: cache-preroll-max-frames: 48 INFO main_window: cache-max-frames: 600 INFO main_window: Creating CacheMemory object with 2147483648 byte limit INFO preview_thread: QThread Start Method Invoked INFO main_window: Cleared temporary files: /home/arius/.openshot_qt/thumbnail INFO main_window: Cleared temporary files: /home/arius/.openshot_qt/blender INFO main_window: Cleared temporary files: /home/arius/.openshot_qt/title INFO main_window: updateStatusChanged INFO main_window: recover_backup INFO project_data: Setting profile to HD 720p 30 fps INFO project_data: Apply default audio playback settings: 44100, 2 channels INFO video_widget: Load: Set video widget display aspect ratio to: 1.7777777910232544 INFO video_widget: Set video widget pixel aspect ratio to: 1.0 INFO main_window: updateStatusChanged INFO timeline: Adjusting max size of preview image: PyQt5.QtCore.QSize(594, 334) INFO webengine: Registering WebChannel connection with WebEngine WARNING webengine: WebEngine backend still not ready after 5 retries. WARNING webengine: WebEngine backend still not ready after 5 retries. WARNING webengine: WebEngine backend still not ready after 5 retries. WARNING webengine: WebEngine backend still not ready after 5 retries. WARNING webengine: WebEngine backend still not ready after 5 retries. WARNING webengine: WebEngine backend still not ready after 5 retries. WARNING webengine: WebEngine backend still not ready after 5 retries. WARNING webengine: WebEngine backend still not ready after 5 retries. WARNING webengine: WebEngine backend still not ready after 5 retries. WARNING webengine: WebEngine backend still not ready after 5 retries. WARNING webengine: WebEngine backend still not ready after 10 retries. WARNING webengine: WebEngine backend still not ready after 10 retries. WARNING webengine: WebEngine backend still not ready after 10 retries. WARNING webengine: WebEngine backend still not ready after 10 retries. WARNING webengine: WebEngine backend still not ready after 10 retries. WARNING webengine: WebEngine backend still not ready after 10 retries. WARNING webengine: WebEngine backend still not ready after 10 retries. WARNING webengine: WebEngine backend still not ready after 10 retries. Property 'modal'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'windowModality'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'enabled'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'geometry'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'frameGeometry'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'normalGeometry'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'x'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'y'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'pos'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'frameSize'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'size'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'width'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'height'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'rect'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'childrenRect'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'childrenRegion'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'sizePolicy'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'minimumSize'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'maximumSize'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'minimumWidth'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'minimumHeight'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'maximumWidth'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'maximumHeight'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'sizeIncrement'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'baseSize'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'palette'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'font'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'cursor'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'mouseTracking'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'tabletTracking'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'isActiveWindow'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'focusPolicy'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'focus'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'contextMenuPolicy'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'updatesEnabled'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'visible'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'minimized'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'maximized'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'fullScreen'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'sizeHint'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'minimumSizeHint'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'acceptDrops'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'windowOpacity'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'windowModified'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'toolTip'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'toolTipDuration'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'statusTip'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'whatsThis'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'accessibleName'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'accessibleDescription'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'layoutDirection'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'autoFillBackground'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'styleSheet'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'locale'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'windowFilePath'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'inputMethodHints'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'title'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'url'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'selectedText'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'hasSelection'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! Property 'zoomFactor'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken! WARNING webengine: WebEngine backend still not ready after 10 retries. WARNING webengine: WebEngine backend still not ready after 10 retries. INFO webview: Qt Ready INFO webview: Angular Ready ffmpegthumbnailer -i '/home/arius/Videos/Water Bear - Thrive Session 3.MOV' -o /home/arius/.cache/thumbnails/normal/aabfbd50d5e13853bfab0eb6df1db7aa.png -s 128 -f [mov,mp4,m4a,3gp,3g2,mj2 @ 0x556411a71c80] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible! [mov,mp4,m4a,3gp,3g2,mj2 @ 0x556411a71c80] moov atom not found                                                                                 Error: Could not open input file: /home/arius/Videos/Water Bear - Thrive Session 3.MOV                                                         ffmpegthumbnailer -i '/home/arius/Videos/Water Bear - Thrive Session - Tom Dancing.MOV' -o /home/arius/.cache/thumbnails/normal/4afe94863c44acfe9e19a66e32e7317e.png -s 128 -f [mov,mp4,m4a,3gp,3g2,mj2 @ 0x557c8a3d2c00] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible! [mov,mp4,m4a,3gp,3g2,mj2 @ 0x557c8a3d2c00] moov atom not found                                                                                 Error: Could not open input file: /home/arius/Videos/Water Bear - Thrive Session - Tom Dancing.MOV                                             ffmpegthumbnailer -i '/home/arius/Videos/Thrive - Live in Craig'\''s Basement, March 11, 2023.MOV' -o /home/arius/.cache/thumbnails/normal/4b28ae10f9ecfa41f36865be51b0c502.png -s 128 -f [mov,mp4,m4a,3gp,3g2,mj2 @ 0x5587b4112c80] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible! [mov,mp4,m4a,3gp,3g2,mj2 @ 0x5587b4112c80] moov atom not found                                                                                 Error: Could not open input file: /home/arius/Videos/Thrive - Live in Craig's Basement, March 11, 2023.MOV                                     ffmpegthumbnailer -i '/home/arius/Videos/IMG_6944.MOV' -o /home/arius/.cache/thumbnails/normal/82fad2ea1e4ad8c35f4becba619b16b8.png -s 128 -f [mov,mp4,m4a,3gp,3g2,mj2 @ 0x558495703c80] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible! [mov,mp4,m4a,3gp,3g2,mj2 @ 0x558495703c80] moov atom not found                                                                                 Error: Could not open input file: /home/arius/Videos/IMG_6944.MOV                                                                              INFO files_model: Imported media file /home/arius/Videos/IMG_6940.MOV INFO main_window: updateStatusChanged ffmpegthumbnailer -i '/home/arius/Videos/Water Bear - Thrive Session 3.MOV' -o /home/arius/.cache/thumbnails/normal/aabfbd50d5e13853bfab0eb6df1db7aa.png -s 128 -f [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55edf958ec80] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible! [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55edf958ec80] moov atom not found                                                                                 Error: Could not open input file: /home/arius/Videos/Water Bear - Thrive Session 3.MOV                                                         ffmpegthumbnailer -i '/home/arius/Videos/Water Bear - Thrive Session - Tom Dancing.MOV' -o /home/arius/.cache/thumbnails/normal/4afe94863c44acfe9e19a66e32e7317e.png -s 128 -f [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55c89eaa3c00] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible! [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55c89eaa3c00] moov atom not found                                                                                 Error: Could not open input file: /home/arius/Videos/Water Bear - Thrive Session - Tom Dancing.MOV                                             ffmpegthumbnailer -i '/home/arius/Videos/Thrive - Live in Craig'\''s Basement, March 11, 2023.MOV' -o /home/arius/.cache/thumbnails/normal/4b28ae10f9ecfa41f36865be51b0c502.png -s 128 -f [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55f9bce52c80] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible! [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55f9bce52c80] moov atom not found                                                                                 Error: Could not open input file: /home/arius/Videos/Thrive - Live in Craig's Basement, March 11, 2023.MOV                                     ffmpegthumbnailer -i '/home/arius/Videos/IMG_6944.MOV' -o /home/arius/.cache/thumbnails/normal/82fad2ea1e4ad8c35f4becba619b16b8.png -s 128 -f [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55a85a549c80] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible! [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55a85a549c80] moov atom not found                                                                                 Error: Could not open input file: /home/arius/Videos/IMG_6944.MOV                                                                              INFO files_model: Imported media file /home/arius/Videos/IMG_6941.MOV Caught signal 11 (SIGSEGV) ---- Unhandled Exception: Stack Trace ----   /usr/lib/python3/dist-packages/_openshot.cpython-310-x86_64-linux-gnu.so ( swig::SwigPyForwardIteratorOpen_T::value() const  + 0x16  )  [0x7f13bfbaf9a6]   /usr/lib/python3/dist-packages/_openshot.cpython-310-x86_64-linux-gnu.so (                                           + 0xbcf6d)  [0x7f13bfabcf6d]   /usr/bin/python3               (                                           + 0x15c3a4)  [0x55f62652f3a4]   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x2a40)  [0x55f62651aaf0]   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x81b )  [0x55f6265188cb]   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x6d5 )  [0x55f626518785]   /usr/bin/python3               (                                           + 0x16ac31)  [0x55f62653dc31]   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x6d5 )  [0x55f626518785]   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x81b )  [0x55f6265188cb]   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x81b )  [0x55f6265188cb]   /usr/bin/python3               ( _PyObject_FastCallDictTstate              + 0xc4  )  [0x55f626525634]   /usr/bin/python3               (                                           + 0x166e94)  [0x55f626539e94]   /usr/bin/python3               ( _PyObject_MakeTpCall                      + 0x1fc )  [0x55f62652644c]   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x6db6)  [0x55f62651ee66]   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x81b )  [0x55f6265188cb]   /usr/bin/python3               (                                           + 0x16ad7e)  [0x55f62653dd7e]   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x2a40)  [0x55f62651aaf0]   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x2a40)  [0x55f62651aaf0]   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x63b2)  [0x55f62651e462]   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x81b )  [0x55f6265188cb]   /usr/bin/python3               (                                           + 0x16ae91)  [0x55f62653de91]   /usr/bin/python3               (                                           + 0x296e5b)  [0x55f626669e5b]   /usr/bin/python3               (                                           + 0x28cf58)  [0x55f62665ff58]   /lib/x86_64-linux-gnu/libc.so.6 (                                           + 0x94b43)  [0x7f13c0c94b43]   /lib/x86_64-linux-gnu/libc.so.6 (                                           + 0x126a00)  [0x7f13c0d26a00] ---- End of Stack Trace ---- QSocketNotifier: Socket notifiers cannot be enabled or disabled from another thread QObject::~QObject: Timers cannot be stopped from another thread    ----  All the videos I have tried to import are from the same phone and recorded in the same format. I have no clue why some of them seem to work fine while others reliably cause the program to crash. There is no correlation regarding the size of the video, which is to say that it’s not the larger files that are causing the problem.  There does seem to be a lot going wrong in the output... any idea why?

---

### Post by arius88 on 2023-05-09
Jesus. Sorry for the wall of text... i can't figure out how to retain the formatting. I write in neat little paragraphs, and then press Post Quick Reply and it pastes it as one big word salad. Any tips?

---

### Post by coffeecat on 2023-05-09
> **arius88 said:**
> Any tips?

Identify and disable whichever browser add-on/extension you are using which is breaking forum functionality. A good start in finding the offender is anything that interferes with javascript.

Then...

Please enclose terminal output in BBCode code tags. Link in my sig if you need it.

---

### Post by arius88 on 2023-05-09
Thanks! It turns out my NoScript add-on was the culprit. Should be working great now. Will repost my message once I figure out what the heck a BBCode is.

---

### Post by arius88 on 2023-05-09
Thank you for the suggestions, and sorry for the slow reply. It's been a busy week. I ran inxi -Fzx and got the following: 

```


 
 
 System:

   Kernel: 5.19.0-41-generic x86_64 bits: 64 compiler: N/A
     Desktop: LXQt 0.17.1 Distro: Ubuntu 22.04.2 LTS (Jammy Jellyfish)
 Machine:
   Type: Desktop System: LENOVO product: 0401U3U v: ThinkCentre A70z
     serial: <superuser required>
   Mobo: LENOVO model: N/A serial: <superuser required> BIOS: LENOVO

     v: 98KT26AUS date: 03/21/2011

 Battery:
   Device-1: apple_mfi_fastcharge model: N/A charge: N/A status: N/A
 CPU:
   Info: dual core model: Intel Core2 Duo E7500 bits: 64 type: MCP
     arch: Core Yorkfield rev: A cache: L1: 128 KiB L2: 3 MiB
   Speed (MHz): avg: 1599 high: 1603 min/max: 1603/2936 cores: 1: 1596
     2: 1603 bogomips: 11705

   Flags: ht lm nx pae sse sse2 sse3 sse4_1 ssse3 vmx

 Graphics:

   Device-1: Intel 4 Series Integrated Graphics vendor: Lenovo driver: i915

     v: kernel bus-ID: 00:02.0

   Device-2: Chicony USB 2.0 Camera type: USB driver: uvcvideo bus-ID: 1-2:2
   Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: modesetting
     unloaded: fbdev,vesa gpu: i915 resolution: 1440x900~60Hz
   OpenGL: renderer: Mesa Intel G41 (ELK) v: 2.1 Mesa 22.2.5
     direct render: Yes
 Audio:

   Device-1: Intel NM10/ICH7 Family High Definition Audio vendor: Lenovo

     driver: snd_hda_intel v: kernel bus-ID: 00:1b.0
   Sound Server-1: ALSA v: k5.19.0-41-generic running: yes
   Sound Server-2: PulseAudio v: 15.99.1 running: yes
   Sound Server-3: PipeWire v: 0.3.48 running: yes
 Network:
   Device-1: Broadcom BCM43225 802.11b/g/n driver: bcma-pci-bridge v: N/A

     bus-ID: 02:00.0

   Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
     vendor: Lenovo driver: r8169 v: kernel port: e800 bus-ID: 03:00.0
   IF: enp3s0 state: down mac: <filter>
   IF-ID-1: wlp2s0b1 state: up mac: <filter>
 Drives:
   Local Storage: total: 465.76 GiB used: 17.67 GiB (3.8%)
   ID-1: /dev/sda vendor: Seagate model: ST3500418AS size: 465.76 GiB

 Partition:
   ID-1: / size: 195.5 GiB used: 17.67 GiB (9.0%) fs: ext4 dev: /dev/sda4
 Swap:
   ID-1: swap-1 type: file size: 512 MiB used: 0 KiB (0.0%) file: /swapfile
 Sensors:
   System Temperatures: cpu: 47.0 C mobo: N/A

   Fan Speeds (RPM): N/A

 Info:
   Processes: 174 Uptime: 1h 29m Memory: 7.64 GiB used: 1.53 GiB (20.1%)
   Init: systemd runlevel: 5 Compilers: gcc: 11.3.0 Packages: 2109 Shell: Bash
   v: 5.1.16 inxi: 3.3.13
 
 
 
```

 
 
 ------
 
 
 Then I ran openshot-qt from terminal, and imported one video no problem, then imported a few videos at once and it crashed (I couldn&#8217;t remember which videos make it crash and which ones don&#8217;t, so I just tried to open a few at once knowing that would definitely cause the problem.) This is the output I got from the time it started opening OpenShot to the moment it crashed:

 
 
 ------
 
 
 ```


 
 
 Loaded modules from: /usr/lib/python3/dist-packages/openshot_qt
 INFO app: ------------------------------------------------

 INFO app:             Tue May  9 09:16:47 2023             

 INFO app:               Starting new session               

 INFO app: ------------------------------------------------

 INFO app:             OpenShot (version 3.1.1)             

 INFO app: ------------------------------------------------
 INFO app: openshot-qt version: 3.1.1
 INFO app: libopenshot version: 0.3.2

 INFO app: platform: Linux-5.19.0-41-generic-x86_64-with-glibc2.35

 INFO app: processor: x86_64

 INFO app: machine: x86_64

 INFO app: python version: 3.10.6

 INFO app: qt5 version: 5.15.3
 INFO app: pyqt5 version: 5.15.6
 INFO project_data: Setting profile to HD 720p 30 fps
 INFO project_data: Apply default audio playback settings: 44100, 2 channels
 INFO app: checking babl_ext_path: /usr/lib/python3/dist-packages/openshot_qt/lib/babl-ext
 Screen VGA-1

    devicePixelRatio: 1.0

    logicalDotsPerInch: 96.02521008403362
    physicalDotsPerInch: 89.6470588235294
    availableSizes: PyQt5.QtCore.QSize(1440, 868)
 INFO language: Qt Detected Languages: ['en-CA']
 INFO language: LANG Environment Variable: en_CA.UTF-8
 INFO language: LOCALE Environment Variable:  
 INFO language: OpenShot Preference Language: Default

 INFO app: Setting font to /usr/lib/python3/dist-packages/openshot_qt/images/fonts/Ubuntu-R.ttf

 INFO app: Setting custom dark theme
 INFO logger_libopenshot: Connecting to libopenshot with debug port: 5556
 INFO ui_util: Initializing UI for MainWindow
 INFO thumbnail: Starting thumbnail server listening on ('127.0.0.1', 37515)
 Sandboxing disabled by user.
 INFO webengine: WebEngine backend initializing

 INFO version: Found current version: {'error_rate_stable': 0.5, 'trans_rate_unstable': 0.001, 'error_rate_unstable': 0.05, 'openshot_version': '3.1.1', 'trans_rate_stable': 0.01}

 INFO transition_model: updating transitions model.
 INFO effects_model: updating effects model.
 INFO emoji_model: updating emoji model.
 INFO sentry: Sentry initialized for 'production': 0.5 sample rate, 0.01 transaction rate
 INFO main_window: InitCacheSettings
 INFO main_window: cache-mode: CacheMemory
 INFO main_window: cache-limit-mb: 2048

 INFO main_window: cache-ahead-percent: 0.7

 INFO main_window: cache-preroll-min-frames: 24
 INFO main_window: cache-preroll-max-frames: 48
 INFO main_window: cache-max-frames: 600
 INFO main_window: Creating CacheMemory object with 2147483648 byte limit
 INFO preview_thread: QThread Start Method Invoked
 INFO main_window: Cleared temporary files: /home/arius/.openshot_qt/thumbnail
 INFO main_window: Cleared temporary files: /home/arius/.openshot_qt/blender

 INFO main_window: Cleared temporary files: /home/arius/.openshot_qt/title

 INFO main_window: updateStatusChanged
 INFO main_window: recover_backup
 INFO project_data: Setting profile to HD 720p 30 fps
 INFO project_data: Apply default audio playback settings: 44100, 2 channels
 INFO video_widget: Load: Set video widget display aspect ratio to: 1.7777777910232544
 INFO video_widget: Set video widget pixel aspect ratio to: 1.0

 INFO main_window: updateStatusChanged

 INFO timeline: Adjusting max size of preview image: PyQt5.QtCore.QSize(594, 334)
 INFO webengine: Registering WebChannel connection with WebEngine
 WARNING webengine: WebEngine backend still not ready after 5 retries.
 WARNING webengine: WebEngine backend still not ready after 5 retries.
 WARNING webengine: WebEngine backend still not ready after 5 retries.
 WARNING webengine: WebEngine backend still not ready after 5 retries.
 WARNING webengine: WebEngine backend still not ready after 5 retries.

 WARNING webengine: WebEngine backend still not ready after 5 retries.

 WARNING webengine: WebEngine backend still not ready after 5 retries.
 WARNING webengine: WebEngine backend still not ready after 5 retries.
 WARNING webengine: WebEngine backend still not ready after 5 retries.
 WARNING webengine: WebEngine backend still not ready after 5 retries.
 WARNING webengine: WebEngine backend still not ready after 10 retries.
 WARNING webengine: WebEngine backend still not ready after 10 retries.

 WARNING webengine: WebEngine backend still not ready after 10 retries.

 WARNING webengine: WebEngine backend still not ready after 10 retries.
 WARNING webengine: WebEngine backend still not ready after 10 retries.
 WARNING webengine: WebEngine backend still not ready after 10 retries.
 WARNING webengine: WebEngine backend still not ready after 10 retries.
  WARNING webengine: WebEngine backend still not ready after 10 retries.
 Property 'modal'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'windowModality'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'enabled'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'geometry'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'frameGeometry'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'normalGeometry'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'x'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'y'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'pos'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'frameSize'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'size'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'width'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'height'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'rect'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'childrenRect'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'childrenRegion'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'sizePolicy'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'minimumSize'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'maximumSize'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'minimumWidth'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'minimumHeight'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'maximumWidth'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'maximumHeight'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'sizeIncrement'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'baseSize'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'palette'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'font'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'cursor'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'mouseTracking'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'tabletTracking'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'isActiveWindow'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'focusPolicy'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'focus'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'contextMenuPolicy'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'updatesEnabled'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'visible'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'minimized'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'maximized'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'fullScreen'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'sizeHint'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'minimumSizeHint'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'acceptDrops'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'windowOpacity'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'windowModified'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'toolTip'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'toolTipDuration'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'statusTip'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'whatsThis'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'accessibleName'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'accessibleDescription'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'layoutDirection'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'autoFillBackground'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'styleSheet'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'locale'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'windowFilePath'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'inputMethodHints'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'title'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'url'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'selectedText'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
 Property 'hasSelection'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 Property 'zoomFactor'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!

 WARNING webengine: WebEngine backend still not ready after 10 retries.
 WARNING webengine: WebEngine backend still not ready after 10 retries.
 INFO webview: Qt Ready
 INFO webview: Angular Ready
 ffmpegthumbnailer -i '/home/arius/Videos/Water Bear - Thrive Session 3.MOV' -o /home/arius/.cache/thumbnails/normal/aabfbd50d5e13853bfab0eb6df1db7aa.png -s 128 -f
 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x556411a71c80] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible!
 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x556411a71c80] moov atom not found                                                                                 

 Error: Could not open input file: /home/arius/Videos/Water Bear - Thrive Session 3.MOV                                                         

 ffmpegthumbnailer -i '/home/arius/Videos/Water Bear - Thrive Session - Tom Dancing.MOV' -o /home/arius/.cache/thumbnails/normal/4afe94863c44acfe9e19a66e32e7317e.png -s 128 -f
 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x557c8a3d2c00] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible!
 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x557c8a3d2c00] moov atom not found                                                                                 
 Error: Could not open input file: /home/arius/Videos/Water Bear - Thrive Session - Tom Dancing.MOV                                             
 ffmpegthumbnailer -i '/home/arius/Videos/Thrive - Live in Craig'\''s Basement, March 11, 2023.MOV' -o /home/arius/.cache/thumbnails/normal/4b28ae10f9ecfa41f36865be51b0c502.png -s 128 -f
 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x5587b4112c80] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible!

 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x5587b4112c80] moov atom not found                                                                                 

 Error: Could not open input file: /home/arius/Videos/Thrive - Live in Craig's Basement, March 11, 2023.MOV                                     
 ffmpegthumbnailer -i '/home/arius/Videos/IMG_6944.MOV' -o /home/arius/.cache/thumbnails/normal/82fad2ea1e4ad8c35f4becba619b16b8.png -s 128 -f
 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x558495703c80] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible!
 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x558495703c80] moov atom not found                                                                                 
 Error: Could not open input file: /home/arius/Videos/IMG_6944.MOV                                                                              
 INFO files_model: Imported media file /home/arius/Videos/IMG_6940.MOV
 INFO main_window: updateStatusChanged

 ffmpegthumbnailer -i '/home/arius/Videos/Water Bear - Thrive Session 3.MOV' -o /home/arius/.cache/thumbnails/normal/aabfbd50d5e13853bfab0eb6df1db7aa.png -s 128 -f

 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55edf958ec80] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible!
 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55edf958ec80] moov atom not found                                                                                 
 Error: Could not open input file: /home/arius/Videos/Water Bear - Thrive Session 3.MOV                                                         
 ffmpegthumbnailer -i '/home/arius/Videos/Water Bear - Thrive Session - Tom Dancing.MOV' -o /home/arius/.cache/thumbnails/normal/4afe94863c44acfe9e19a66e32e7317e.png -s 128 -f
 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55c89eaa3c00] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible!
 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55c89eaa3c00] moov atom not found                                                                                 

 Error: Could not open input file: /home/arius/Videos/Water Bear - Thrive Session - Tom Dancing.MOV                                             

 ffmpegthumbnailer -i '/home/arius/Videos/Thrive - Live in Craig'\''s Basement, March 11, 2023.MOV' -o /home/arius/.cache/thumbnails/normal/4b28ae10f9ecfa41f36865be51b0c502.png -s 128 -f
 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55f9bce52c80] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible!
 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55f9bce52c80] moov atom not found                                                                                 
 Error: Could not open input file: /home/arius/Videos/Thrive - Live in Craig's Basement, March 11, 2023.MOV                                     
 ffmpegthumbnailer -i '/home/arius/Videos/IMG_6944.MOV' -o /home/arius/.cache/thumbnails/normal/82fad2ea1e4ad8c35f4becba619b16b8.png -s 128 -f
 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55a85a549c80] Format mov,mp4,m4a,3gp,3g2,mj2 detected only with low score of 1, misdetection possible!
 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x55a85a549c80] moov atom not found                                                                                 

 Error: Could not open input file: /home/arius/Videos/IMG_6944.MOV                                                                              
 INFO files_model: Imported media file /home/arius/Videos/IMG_6941.MOV
 Caught signal 11 (SIGSEGV)
 ---- Unhandled Exception: Stack Trace ----
   /usr/lib/python3/dist-packages/_openshot.cpython-310-x86_64-linux-gnu.so ( swig::SwigPyForwardIteratorOpen_T<std::_Rb_tree_iterator<std::pair<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > > >, std::pair<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > >, swig::from_oper<std::pair<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >::value() const  + 0x16  )  [0x7f13bfbaf9a6]

   /usr/lib/python3/dist-packages/_openshot.cpython-310-x86_64-linux-gnu.so (                                           + 0xbcf6d)  [0x7f13bfabcf6d]
   /usr/bin/python3               (                                           + 0x15c3a4)  [0x55f62652f3a4]
   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x2a40)  [0x55f62651aaf0]
   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]
   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x81b )  [0x55f6265188cb]

   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]

   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x6d5 )  [0x55f626518785]
   /usr/bin/python3               (                                           + 0x16ac31)  [0x55f62653dc31]
   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x6d5 )  [0x55f626518785]
   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]
   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x81b )  [0x55f6265188cb]
   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]
   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x81b )  [0x55f6265188cb]

   /usr/bin/python3               ( _PyObject_FastCallDictTstate              + 0xc4  )  [0x55f626525634]

   /usr/bin/python3               (                                           + 0x166e94)  [0x55f626539e94]
   /usr/bin/python3               ( _PyObject_MakeTpCall                      + 0x1fc )  [0x55f62652644c]
   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x6db6)  [0x55f62651ee66]
   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]
   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x81b )  [0x55f6265188cb]
   /usr/bin/python3               (                                           + 0x16ad7e)  [0x55f62653dd7e]

   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x2a40)  [0x55f62651aaf0]

   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]
   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x2a40)  [0x55f62651aaf0]
   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]
   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x63b2)  [0x55f62651e462]
   /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x55f6265301ec]
   /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x81b )  [0x55f6265188cb]
   /usr/bin/python3               (                                           + 0x16ae91)  [0x55f62653de91]

   /usr/bin/python3               (                                           + 0x296e5b)  [0x55f626669e5b]

   /usr/bin/python3               (                                           + 0x28cf58)  [0x55f62665ff58]
   /lib/x86_64-linux-gnu/libc.so.6 (                                           + 0x94b43)  [0x7f13c0c94b43]
   /lib/x86_64-linux-gnu/libc.so.6 (                                           + 0x126a00)  [0x7f13c0d26a00]
 ---- End of Stack Trace ----
 QSocketNotifier: Socket notifiers cannot be enabled or disabled from another thread
 QObject::~QObject: Timers cannot be stopped from another thread
 
 
 
```

 
 
 ----
 
 
 All the videos I have tried to import are from the same phone and recorded in the same format. I have no clue why some of them seem to work fine while others reliably cause the program to crash. There is no correlation regarding the size of the video, which is to say that it&#8217;s not the larger files that are causing the problem.
 
 
 There does seem to be a lot going wrong in the output... any idea why?

---

### Post by arius88 on 2023-05-09
Apparently another person on GitHub was experiencing the "WebEngine backend still not ready after 10 retries" error and was advised to "add --no-sandbox" - but nobody in that thread specified adding "no sandbox" to WHAT exactly; it's an old dead thread from several months ago and I don't have an account there.  Any ideas?

---

### Post by Holger_Gehrke on 2023-05-10
Looks like several tools / libraries called by openshot have a problem with your .mov files specifically with finding the moov-atom. This is a block of data containing information like framerate, run-time, interleave factors, resolution etc. Since this information is only completely available when the recording is finished, it will often be written at the end of the file by older recording applications / cameras. A lot of programs scan the beginning of the file for it (where more modern programs put it so you can do http-pseudo-streaming with the file). There is a small tool named 'qt-faststart' which will rewrite the file with the moov-atom at the beginning. It's part of the package ffmpeg.

Holger

---

### Post by arius88 on 2023-05-10
Brilliant, thanks! I'll give that a shot and report back if it fixes my problem. I am using an iPhone 6s, which I suppose is pretty old by modern standards.

---

### Post by arius88 on 2023-05-10
Okay. Installed FFMpeg and used qt-faststart to move the moov-atom for one of my crashy video files. It did the conversion and spat out a newly named video file. I ran openshot-qt from terminal and tried to import the new and improved file, which immediately caused OpenShot to crash, as per usual. 

```


$ openshot-qt
Loaded modules from: /usr/lib/python3/dist-packages/openshot_qt
INFO app: ------------------------------------------------
INFO app:             Wed May 10 20:18:03 2023            
INFO app:               Starting new session              
INFO app: ------------------------------------------------
INFO app:             OpenShot (version 3.1.1)            
INFO app: ------------------------------------------------
INFO app: openshot-qt version: 3.1.1
INFO app: libopenshot version: 0.3.2
INFO app: platform: Linux-5.19.0-41-generic-x86_64-with-glibc2.35
INFO app: processor: x86_64
INFO app: machine: x86_64
INFO app: python version: 3.10.6
INFO app: qt5 version: 5.15.3
INFO app: pyqt5 version: 5.15.6
INFO project_data: Setting profile to HD 720p 30 fps
INFO project_data: Apply default audio playback settings: 44100, 2 channels
INFO app: checking babl_ext_path: /usr/lib/python3/dist-packages/openshot_qt/lib/babl-ext
Screen VGA-1
   devicePixelRatio: 1.0
   logicalDotsPerInch: 96.02521008403362
   physicalDotsPerInch: 89.6470588235294
   availableSizes: PyQt5.QtCore.QSize(1440, 868)
INFO language: Qt Detected Languages: ['en-CA']
INFO language: LANG Environment Variable: en_CA.UTF-8
INFO language: LOCALE Environment Variable: 
INFO language: OpenShot Preference Language: Default
INFO app: Setting font to /usr/lib/python3/dist-packages/openshot_qt/images/fonts/Ubuntu-R.ttf
INFO app: Setting custom dark theme
INFO logger_libopenshot: Connecting to libopenshot with debug port: 5556
INFO ui_util: Initializing UI for MainWindow
INFO thumbnail: Starting thumbnail server listening on ('127.0.0.1', 50457)
Sandboxing disabled by user.
INFO webengine: WebEngine backend initializing
INFO transition_model: updating transitions model.
INFO version: Found current version: {'error_rate_unstable': 0.05, 'openshot_version': '3.1.1', 'trans_rate_unstable': 0.001, 'error_rate_stable': 0.5, 'trans_rate_stable': 0.01}
INFO effects_model: updating effects model.
INFO emoji_model: updating emoji model.
INFO sentry: Sentry initialized for 'production': 0.5 sample rate, 0.01 transaction rate
INFO main_window: InitCacheSettings
INFO main_window: cache-mode: CacheMemory
INFO main_window: cache-limit-mb: 2048
INFO main_window: cache-ahead-percent: 0.7
INFO main_window: cache-preroll-min-frames: 24
INFO main_window: cache-preroll-max-frames: 48
INFO main_window: cache-max-frames: 600
INFO main_window: Creating CacheMemory object with 2147483648 byte limit
INFO preview_thread: QThread Start Method Invoked
ERROR main_window: Unhandled crash detected: linux-/usr/lib/python3/dist-packages/_openshot.cpython-310-x86_64-linux-gnu.so swig::SwigPyForwardIteratorOpen_T<std::_Rb_tree_iterator<std::pair<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > > >, std::pair<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > >, swig::from_oper<std::pair<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >::value const 0x16 [0x7f59a27af9a6]
INFO main_window: updateStatusChanged
INFO main_window: recover_backup
INFO project_data: Setting profile to HD 720p 30 fps
INFO project_data: Apply default audio playback settings: 44100, 2 channels
INFO video_widget: Load: Set video widget display aspect ratio to: 1.7777777910232544
INFO video_widget: Set video widget pixel aspect ratio to: 1.0
INFO main_window: updateStatusChanged
INFO timeline: Adjusting max size of preview image: PyQt5.QtCore.QSize(446, 250)
qt.svg: Invalid path data; path truncated.
INFO webengine: Registering WebChannel connection with WebEngine
INFO timeline: Adjusting max size of preview image: PyQt5.QtCore.QSize(594, 334)
Property 'modal'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'windowModality'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'enabled'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'geometry'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'frameGeometry'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'normalGeometry'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'x'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'y'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'pos'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'frameSize'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'size'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'width'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'height'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'rect'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'childrenRect'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'childrenRegion'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'sizePolicy'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'minimumSize'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'maximumSize'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'minimumWidth'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'minimumHeight'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'maximumWidth'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'maximumHeight'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'sizeIncrement'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'baseSize'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'palette'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'font'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'cursor'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'mouseTracking'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'tabletTracking'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'isActiveWindow'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'focusPolicy'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'focus'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'contextMenuPolicy'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'updatesEnabled'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'visible'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'minimized'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'maximized'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'fullScreen'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'sizeHint'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'minimumSizeHint'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'acceptDrops'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'windowOpacity'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'windowModified'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'toolTip'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'toolTipDuration'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'statusTip'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'whatsThis'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'accessibleName'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'accessibleDescription'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'layoutDirection'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'autoFillBackground'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'styleSheet'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'locale'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'windowFilePath'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'inputMethodHints'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'title'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'url'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'selectedText'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'hasSelection'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
Property 'zoomFactor'' of object 'TimelineWebView' has no notify signal and is not constant, value updates in HTML will be broken!
INFO webview: Qt Ready
INFO webview: Angular Ready
INFO files_listview: Processing drop event for 1 urls
INFO files_model: Imported media file /home/arius/Videos/FIXED1.MOV
Caught signal 11 (SIGSEGV)
---- Unhandled Exception: Stack Trace ----
  /usr/lib/python3/dist-packages/_openshot.cpython-310-x86_64-linux-gnu.so ( swig::SwigPyForwardIteratorOpen_T<std::_Rb_tree_iterator<std::pair<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > > >, std::pair<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > >, swig::from_oper<std::pair<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >::value() const  + 0x16  )  [0x7fdb3f5af9a6]
  /usr/lib/python3/dist-packages/_openshot.cpython-310-x86_64-linux-gnu.so (                                           + 0xbcf6d)  [0x7fdb3f4bcf6d]
  /usr/bin/python3               (                                           + 0x15c3a4)  [0x560fb9bf83a4]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x2a40)  [0x560fb9be3af0]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x560fb9bf91ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x81b )  [0x560fb9be18cb]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x560fb9bf91ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x6d5 )  [0x560fb9be1785]
  /usr/bin/python3               (                                           + 0x16ac31)  [0x560fb9c06c31]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x6d5 )  [0x560fb9be1785]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x560fb9bf91ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x81b )  [0x560fb9be18cb]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x560fb9bf91ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x81b )  [0x560fb9be18cb]
  /usr/bin/python3               ( _PyObject_FastCallDictTstate              + 0xc4  )  [0x560fb9bee634]
  /usr/bin/python3               (                                           + 0x166e94)  [0x560fb9c02e94]
  /usr/bin/python3               ( _PyObject_MakeTpCall                      + 0x1fc )  [0x560fb9bef44c]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x6db6)  [0x560fb9be7e66]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x560fb9bf91ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x81b )  [0x560fb9be18cb]
  /usr/bin/python3               (                                           + 0x16ad7e)  [0x560fb9c06d7e]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x2a40)  [0x560fb9be3af0]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x560fb9bf91ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x2a40)  [0x560fb9be3af0]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x560fb9bf91ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x63b2)  [0x560fb9be7462]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x560fb9bf91ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x81b )  [0x560fb9be18cb]
  /usr/bin/python3               (                                           + 0x16ae91)  [0x560fb9c06e91]
  /usr/bin/python3               (                                           + 0x296e5b)  [0x560fb9d32e5b]
  /usr/bin/python3               (                                           + 0x28cf58)  [0x560fb9d28f58]
  /lib/x86_64-linux-gnu/libc.so.6 (                                           + 0x94b43)  [0x7fdb40694b43]
  /lib/x86_64-linux-gnu/libc.so.6 (                                           + 0x126a00)  [0x7fdb40726a00]
---- End of Stack Trace ----
QSocketNotifier: Socket notifiers cannot be enabled or disabled from another thread
QObject::~QObject: Timers cannot be stopped from another thread


```

Not sure what "Unhandled Exception: Stack Trace" means, but I assume that might be the problem? In defense of qt-faststart, this output looks significantly less error-riddled (at least to my computer illiterate eyes) than the previous output from before I converted the file. So I guess we're making progress? I'm starting to get the impression that OpenShot is a bit of a delicate flower.

One thought I had - it seems like this particular video was shot in portrait instead of landscape. Could that be causing OpenShot to crash? Seems like the program should just warn me that it's an inappropriate file though, and I'm pretty sure I've successfully imported other files that were in portrait before.

---

### Post by arius88 on 2023-05-11
Did some googling regarding all the TimelineWebView messages. [Someone][[https://stackoverflow.com/questions/33704128/undefined-properties-and-return-types-when-using-qwebchannel]](https://stackoverflow.com/questions/33704128/undefined-properties-and-return-types-when-using-qwebchannel]) said that communication between Qt and JS (JavaScript) in Qt5 is asynchronous. Not sure what that means, and the explanation for how to fix it was over my head and probably not applicable to OpenShot. 

Thoughts?

---

### Post by arius88 on 2023-05-18
Update: I've given up and installed ShotCut instead. I don't like it as much, but it works, so it wins.

---

### Post by richardth on 2023-07-06
I have a similar problem with OpenShot 3.1.1

After dropping a video - after successfully adding several to my project, I get an immediate crash:

```

INFO main_window: Loaded project /home/jude/Perth2023.osp
INFO files_listview: Processing drop event for 1 urls
INFO files_model: Imported media file /home/jude/Perth2023/WhatsApp Video 2023-06-29 at 15.45.25 (3).mp4
Caught signal 11 (SIGSEGV)
---- Unhandled Exception: Stack Trace ----
  /usr/lib/python3/dist-packages/_openshot.cpython-310-x86_64-linux-gnu.so ( swig::SwigPyForwardIteratorOpen_T<std::_Rb_tree_iterator<std::pair<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > > >, std::pair<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > >, swig::from_oper<std::pair<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >::value() const  + 0x16  )  [0x7fc53e9b0446]
  /usr/lib/python3/dist-packages/_openshot.cpython-310-x86_64-linux-gnu.so (                                           + 0xbd6fd)  [0x7fc53e8bd6fd]
  /usr/bin/python3               (                                           + 0x15c6b4)  [0x563797b786b4]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x2a37)  [0x563797b63d87]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x563797b794ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x8c4 )  [0x563797b61c14]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x563797b794ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x6cd )  [0x563797b61a1d]
  /usr/bin/python3               (                                           + 0x16af11)  [0x563797b86f11]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x6cd )  [0x563797b61a1d]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x563797b794ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x8c4 )  [0x563797b61c14]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x563797b794ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x8c4 )  [0x563797b61c14]
  /usr/bin/python3               ( _PyObject_FastCallDictTstate              + 0xc4  )  [0x563797b6e8b4]
  /usr/bin/python3               (                                           + 0x167184)  [0x563797b83184]
  /usr/bin/python3               ( _PyObject_MakeTpCall                      + 0x1fc )  [0x563797b6f6cc]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x6d97)  [0x563797b680e7]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x563797b794ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x8c4 )  [0x563797b61c14]
  /usr/bin/python3               (                                           + 0x16b05e)  [0x563797b8705e]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x2a37)  [0x563797b63d87]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x563797b794ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x2a37)  [0x563797b63d87]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x563797b794ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x640a)  [0x563797b6775a]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x563797b794ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x8c4 )  [0x563797b61c14]
  /usr/bin/python3               (                                           + 0x16b171)  [0x563797b87171]
  /usr/bin/python3               (                                           + 0x296b4a)  [0x563797cb2b4a]
  /usr/bin/python3               (                                           + 0x28c998)  [0x563797ca8998]
  /lib/x86_64-linux-gnu/libc.so.6 (                                           + 0x94b43)  [0x7fc53fa94b43]
  /lib/x86_64-linux-gnu/libc.so.6 (                                           + 0x126a00)  [0x7fc53fb26a00]
---- End of Stack Trace ----
QObject::~QObject: Timers cannot be stopped from another thread



```

---

### Post by richardth on 2023-07-07
I've also reported this in another thread - see [here]("https://github.com/OpenShot/openshot-qt/issues/4743#issuecomment-1625691061") with a little more information:

```

OpenShot 3.1.1 on Ubuntu 22.04 Jammy Jellyfish (x86-64)
Cinnamon version 5.2.7
Linux Kernel: 5.19.0-46-generic
Processor: Intel© Core™ i7-10750H CPU @ 2.60GHz × 6
Memory: 7.5 GiB
Graphics cards: 
         Intel Corporation CometLake-H GT2 [UHD Graphics]
         NVIDIA Corporation TU116M [GeForce GTX 1660 Ti Mobile]

```

and the `--debug` output:

```

INFO files_listview: Processing drop event for 1 urls
DEBUG files_model: Importing file list: ['/home/jude/Perth2023/WhatsApp Video 2023-06-29 at 15.45.25 (2).mp4']
INFO files_model: Imported media file /home/jude/Perth2023/WhatsApp Video 2023-06-29 at 15.45.25 (2).mp4
DEBUG project_data: _set key: ['files'], values: {'acodec': 'aac', 'audio_bit_rate': 192087, 'audio_stream_index': 1, 'audio_timebase': {'den': 48000, 'num': 1}, 'channel_layout': 3, 'channels': 2, 'display_ratio': {'den': 20, 'num': 11}, 'duration': 34.58177185058594, 'file_size': '6688342', 'fps': {'den': 12, 'num': 355}, 'has_audio': True, 'has_single_image': False, 'has_video': True, 'height': 640, 'interlaced_frame': False, 'metadata': {'compatible_brands': 'mp42isom', 'language': 'und', 'major_brand': 'mp42', 'minor_version': '0', 'rotate': '270', 'vendor_id': '[0][0][0][0]'}, 'path': '/home/jude/Perth2023/WhatsApp Video 2023-06-29 at 15.45.25 (2).mp4', 'pixel_format': 0, 'pixel_ratio': {'den': 1, 'num': 1}, 'sample_rate': 48000, 'top_field_first': True, 'type': 'FFmpegReader', 'vcodec': 'h264', 'video_bit_rate': 193406, 'video_length': '1023', 'video_stream_index': 0, 'video_timebase': {'den': 90000, 'num': 1}, 'width': 352, 'media_type': 'video', 'id': 'FBSQ08EX20'}, add: True, remove: False
DEBUG webview: Skipping unneeded webview update for 'files'
DEBUG files_model: updating files model.
DEBUG thumbnail: Processing thumbnail request for FBSQ08EX20 frame 1
Caught signal 11 (SIGSEGV)
---- Unhandled Exception: Stack Trace ----
  /usr/lib/python3/dist-packages/_openshot.cpython-310-x86_64-linux-gnu.so ( swig::SwigPyForwardIteratorOpen_T<std::_Rb_tree_iterator<std::pair<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > > >, std::pair<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > >, swig::from_oper<std::pair<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > > > >::value() const  + 0x16  )  [0x7f32c57b0446]
  /usr/lib/python3/dist-packages/_openshot.cpython-310-x86_64-linux-gnu.so (                                           + 0xbd6fd)  [0x7f32c56bd6fd]
  /usr/bin/python3               (                                           + 0x15c6b4)  [0x556ffa0096b4]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x2a37)  [0x556ff9ff4d87]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x556ffa00a4ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x8c4 )  [0x556ff9ff2c14]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x556ffa00a4ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x6cd )  [0x556ff9ff2a1d]
  /usr/bin/python3               (                                           + 0x16af11)  [0x556ffa017f11]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x6cd )  [0x556ff9ff2a1d]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x556ffa00a4ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x8c4 )  [0x556ff9ff2c14]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x556ffa00a4ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x8c4 )  [0x556ff9ff2c14]
  /usr/bin/python3               ( _PyObject_FastCallDictTstate              + 0xc4  )  [0x556ff9fff8b4]
  /usr/bin/python3               (                                           + 0x167184)  [0x556ffa014184]
  /usr/bin/python3               ( _PyObject_MakeTpCall                      + 0x1fc )  [0x556ffa0006cc]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x6d97)  [0x556ff9ff90e7]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x556ffa00a4ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x8c4 )  [0x556ff9ff2c14]
  /usr/bin/python3               (                                           + 0x16b05e)  [0x556ffa01805e]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x2a37)  [0x556ff9ff4d87]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x556ffa00a4ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x2a37)  [0x556ff9ff4d87]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x556ffa00a4ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x640a)  [0x556ff9ff875a]
  /usr/bin/python3               ( _PyFunction_Vectorcall                    + 0x7c  )  [0x556ffa00a4ec]
  /usr/bin/python3               ( _PyEval_EvalFrameDefault                  + 0x8c4 )  [0x556ff9ff2c14]
  /usr/bin/python3               (                                           + 0x16b171)  [0x556ffa018171]
  /usr/bin/python3               (                                           + 0x296b4a)  [0x556ffa143b4a]
  /usr/bin/python3               (                                           + 0x28c998)  [0x556ffa139998]
  /lib/x86_64-linux-gnu/libc.so.6 (                                           + 0x94b43)  [0x7f32c6894b43]
  /lib/x86_64-linux-gnu/libc.so.6 (                                           + 0x126a00)  [0x7f32c6926a00]
---- End of Stack Trace ----
QObject::~QObject: Timers cannot be stopped from another thread
[1]+  Exit 11                 openshot-qt

```

---

