---
title: "Black screen in Xubuntu"
date: 2014-01-28
forum: General Help
---

### Post by Hvidemose on 2014-01-28
Hey.


When opening Xubuntu 13.10 I have a problem withblack screen, followed by the light going a bit up and down (noimage). The problem occurred after using hdmi and an update, don'tknow what cost the problem.


Does anybody know how to fix this?
The mashine is a Acer aspire 1 (d 270-26)

---

### Post by ubudog on 2014-01-28
Hi,

Are you able to reach a console by typing CTRL+ALT+F2?

---

### Post by joey8 on 2014-01-28
If you are able to switch to a terminal try resetting the resolution  ```
xfconf-query -c displays -p /Default/Screen_0/Resolution -r
```

---

### Post by Hvidemose on 2014-01-29
I was able to enter the console ([COLOR=#000000]by typing CTRL+ALT+F2?[/COLOR]).
When i type the code:
```
[COLOR=#000000][FONT=Ubuntu Mono]xfconf-query -c displays -p /Default/Screen_0/Resolution -r[/FONT][/COLOR]
```
The system replied: Failed to init libxfconf: Unable to autolaunch  a dbus-deamon without a $DISPLAY for X11.

So the problem is unfortunately still there.

---

### Post by ubudog on 2014-01-29
Maybe getting a look at the Xorg log would be helpful.

While in the console, run these commands:
```
sudo apt-get install pastebinit
sudo cat /var/log/Xorg.0.log | pastebinit -b http://paste.ubuntu.com
```

This should put your Xorg log up on the [Ubuntu Pastebin]("http://paste.ubuntu.com/"), and return a URL to it.

---

### Post by Hvidemose on 2014-01-29
Thanks.

Well this is what i got: (On this link: [http://paste.ubuntu.com/6840805/](http://paste.ubuntu.com/6840805/))

```
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
 85
 86
 87
 88
 89
 90
 91
 92
 93
 94
 95
 96
 97
 98
 99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245
246
247
248
249
250
251
252
253
254
255
256
257
258
259
260
261
262
263
264
265
266
267
268
269
270
271
272
273
274
275
276
277
278
279
280
281
282
283
284
285
286
287
288
289
290
291
292
293
294
295
296
297
298
299
300
301
302
303
304
305
306
307
308
309
310
311
312
313
314
315
316
317
318
319
320
321
322
323
324
325
326
327
328
329
330
331
332
333
334
335
336
337
338
339
340
341
342
343
344
345
346
347
348
349
350
351
352
353
354
355
356
357
358
359
360
361
362
363
364
365
366
367
368
369
370
371
372
373
374
375
376
377
378
379
380
381
382
383
384
385
386
387
388
389
390
391
392[/TD]
[TD="class: code"][COLOR=#000000][    22.040] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[    22.040] X Protocol Version 11, Revision 0
[    22.040] Build Operating System: Linux 3.2.0-54-generic i686 Ubuntu
[    22.040] Current Operating System: Linux diana-AOD270 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:16:27 UTC 2013 i686
[    22.040] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=d250db3c-a789-4f1a-a84e-a27b6bd3209e ro quiet splash vt.handoff=7
[    22.040] Build Date: 17 December 2013  10:03:52AM
[    22.040] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see http://www.ubuntu.com/support) 
[    22.040] Current version of pixman: 0.30.2
[    22.040]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    22.041] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.041] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jan 30 00:24:49 2014
[    22.061] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.062] (==) No Layout section.  Using the first Screen section.
[    22.062] (==) No screen section available. Using defaults.
[    22.062] (**) |-->Screen "Default Screen Section" (0)
[    22.062] (**) |   |-->Monitor "<default monitor>"
[    22.063] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    22.063] (==) Automatically adding devices
[    22.063] (==) Automatically enabling devices
[    22.063] (==) Automatically adding GPU devices
[    22.063] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.063]     Entry deleted from font path.
[    22.063] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.063]     Entry deleted from font path.
[    22.064] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.064]     Entry deleted from font path.
[    22.064] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.064]     Entry deleted from font path.
[    22.064] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.064]     Entry deleted from font path.
[    22.064] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    22.064] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.064] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.064] (II) Loader magic: 0xb77886a0
[    22.064] (II) Module ABI versions:
[    22.064]     X.Org ANSI C Emulation: 0.4
[    22.064]     X.Org Video Driver: 14.1
[    22.064]     X.Org XInput driver : 19.1
[    22.064]     X.Org Server Extension : 7.0
[    22.065] (II) xfree86: Adding drm device (/dev/dri/card0)
[    22.068] (--) PCI:*(0:0:2:0) 8086:0be1:1025:061f rev 9, Mem @ 0x86000000/1048576, I/O @ 0x000050d0/8
[    22.068] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.069] Initializing built-in extension Generic Event Extension
[    22.069] Initializing built-in extension SHAPE
[    22.069] Initializing built-in extension MIT-SHM
[    22.069] Initializing built-in extension XInputExtension
[    22.069] Initializing built-in extension XTEST
[    22.069] Initializing built-in extension BIG-REQUESTS
[    22.069] Initializing built-in extension SYNC
[    22.069] Initializing built-in extension XKEYBOARD
[    22.069] Initializing built-in extension XC-MISC
[    22.069] Initializing built-in extension SECURITY
[    22.069] Initializing built-in extension XINERAMA
[    22.069] Initializing built-in extension XFIXES
[    22.069] Initializing built-in extension RENDER
[    22.069] Initializing built-in extension RANDR
[    22.069] Initializing built-in extension COMPOSITE
[    22.069] Initializing built-in extension DAMAGE
[    22.069] Initializing built-in extension MIT-SCREEN-SAVER
[    22.070] Initializing built-in extension DOUBLE-BUFFER
[    22.070] Initializing built-in extension RECORD
[    22.070] Initializing built-in extension DPMS
[    22.070] Initializing built-in extension X-Resource
[    22.070] Initializing built-in extension XVideo
[    22.070] Initializing built-in extension XVideo-MotionCompensation
[    22.070] Initializing built-in extension SELinux
[    22.070] Initializing built-in extension XFree86-VidModeExtension
[    22.070] Initializing built-in extension XFree86-DGA
[    22.070] Initializing built-in extension XFree86-DRI
[    22.070] Initializing built-in extension DRI2
[    22.070] (II) "glx" will be loaded by default.
[    22.070] (WW) "xmir" is not to be loaded by default. Skipping.
[    22.070] (II) LoadModule: "dri2"
[    22.070] (II) Module "dri2" already built-in
[    22.070] (II) LoadModule: "glamoregl"
[    22.093] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    22.294] (II) Module glamoregl: vendor="X.Org Foundation"
[    22.294]     compiled for 1.14.3, module version = 0.5.1
[    22.294]     ABI class: X.Org ANSI C Emulation, version 0.4
[    22.294] (II) LoadModule: "glx"
[    22.295] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.295] (II) Module glx: vendor="X.Org Foundation"
[    22.295]     compiled for 1.14.5, module version = 1.0.0
[    22.296]     ABI class: X.Org Server Extension, version 7.0
[    22.296] (==) AIGLX enabled
[    22.296] Loading extension GLX
[    22.296] (==) Matched vesa as autoconfigured driver 0
[    22.296] (==) Matched modesetting as autoconfigured driver 1
[    22.296] (==) Matched fbdev as autoconfigured driver 2
[    22.296] (==) Assigned the driver to the xf86ConfigLayout
[    22.296] (II) LoadModule: "vesa"
[    22.297] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.297] (II) Module vesa: vendor="X.Org Foundation"
[    22.297]     compiled for 1.14.1, module version = 2.3.2
[    22.297]     Module class: X.Org Video Driver
[    22.297]     ABI class: X.Org Video Driver, version 14.1
[    22.297] (II) LoadModule: "modesetting"
[    22.298] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    22.298] (II) Module modesetting: vendor="X.Org Foundation"
[    22.298]     compiled for 1.14.1, module version = 0.8.0
[    22.298]     Module class: X.Org Video Driver
[    22.298]     ABI class: X.Org Video Driver, version 14.1
[    22.299] (II) LoadModule: "fbdev"
[    22.299] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.300] (II) Module fbdev: vendor="X.Org Foundation"
[    22.300]     compiled for 1.14.1, module version = 0.4.3
[    22.300]     Module class: X.Org Video Driver
[    22.300]     ABI class: X.Org Video Driver, version 14.1
[    22.300] (II) VESA: driver for VESA chipsets: vesa
[    22.300] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    22.300] (II) FBDEV: driver for framebuffer: fbdev
[    22.300] (++) using VT number 7

[    22.301] vesa: Ignoring device with a bound kernel driver
[    22.301] (WW) Falling back to old probe method for vesa
[    22.301] (II) modesetting(1): using drv /dev/dri/card0
[    22.301] (WW) Falling back to old probe method for fbdev
[    22.301] (II) Loading sub module "fbdevhw"
[    22.301] (II) LoadModule: "fbdevhw"
[    22.302] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.302] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.302]     compiled for 1.14.5, module version = 0.0.2
[    22.302]     ABI class: X.Org Video Driver, version 14.1
[    22.302] (EE) Screen 0 deleted because of no matching config section.
[    22.302] (II) UnloadModule: "vesa"
[    22.302] (II) modesetting(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    22.302] (==) modesetting(0): Depth 24, (==) framebuffer bpp 32
[    22.302] (==) modesetting(0): RGB weight 888
[    22.303] (==) modesetting(0): Default visual is TrueColor
[    22.303] (II) modesetting(0): ShadowFB: preferred NO, enabled NO
[    22.364] (II) modesetting(0): Output VGA-0 has no monitor section
[    22.428] (II) modesetting(0): Output LVDS-0 has no monitor section
[    22.437] (II) modesetting(0): Output DVI-0 has no monitor section
[    22.438] (II) modesetting(0): Output DisplayPort-0 has no monitor section
[    22.500] (II) modesetting(0): EDID for output VGA-0
[    22.564] (II) modesetting(0): EDID for output LVDS-0
[    22.564] (II) modesetting(0): Manufacturer: AUO  Model: 60d2  Serial#: 0
[    22.564] (II) modesetting(0): Year: 2009  Week: 0
[    22.564] (II) modesetting(0): EDID Version: 1.3
[    22.564] (II) modesetting(0): Digital Display Input
[    22.564] (II) modesetting(0): Max Image Size [cm]: horiz.: 22  vert.: 13
[    22.564] (II) modesetting(0): Gamma: 2.20
[    22.564] (II) modesetting(0): No DPMS capabilities specified
[    22.564] (II) modesetting(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    22.564] (II) modesetting(0): First detailed timing is preferred mode
[    22.564] (II) modesetting(0): redX: 0.590 redY: 0.345   greenX: 0.325 greenY: 0.540
[    22.564] (II) modesetting(0): blueX: 0.150 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    22.564] (II) modesetting(0): Manufacturer's mask: 0
[    22.564] (II) modesetting(0): Supported detailed timing:
[    22.564] (II) modesetting(0): clock: 49.8 MHz   Image Size:  222 x 125 mm
[    22.564] (II) modesetting(0): h_active: 1024  h_sync: 1072  h_sync_end 1104 h_blank_end 1338 h_border: 0
[    22.565] (II) modesetting(0): v_active: 600  v_sync: 602  v_sync_end 608 v_blanking: 620 v_border: 0
[    22.565] (II) modesetting(0): Unknown vendor-specific block f
[    22.565] (II) modesetting(0):  AUO
[    22.565] (II) modesetting(0):  B101AW06 V0
[    22.565] (II) modesetting(0): EDID (in hex):
[    22.565] (II) modesetting(0):     00ffffffffffff0006afd26000000000
[    22.565] (II) modesetting(0):     0013010380160d780a15859758538a26
[    22.565] (II) modesetting(0):     25505400000001010101010101010101
[    22.565] (II) modesetting(0):     0101010101017413003a415814203020
[    22.565] (II) modesetting(0):     2600de7d000000180000000f00000000
[    22.565] (II) modesetting(0):     00000000000000000020000000fe0041
[    22.565] (II) modesetting(0):     554f0a202020202020202020000000fe
[    22.565] (II) modesetting(0):     004231303141573036205630200a002b
[    22.566] (II) modesetting(0): Printing probed modes for output LVDS-0
[    22.566] (II) modesetting(0): Modeline "1024x600"x60.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz eP)
[    22.566] (II) modesetting(0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    22.566] (II) modesetting(0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[    22.566] (II) modesetting(0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[    22.566] (II) modesetting(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    22.566] (II) modesetting(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    22.566] (II) modesetting(0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[    22.566] (II) modesetting(0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[    22.566] (II) modesetting(0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[    22.566] (II) modesetting(0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    22.566] (II) modesetting(0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    22.566] (II) modesetting(0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[    22.566] (II) modesetting(0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[    22.566] (II) modesetting(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    22.566] (II) modesetting(0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[    22.566] (II) modesetting(0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    22.566] (II) modesetting(0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[    22.567] (II) modesetting(0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    22.567] (II) modesetting(0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[    22.567] (II) modesetting(0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[    22.567] (II) modesetting(0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    22.576] (II) modesetting(0): EDID for output DVI-0
[    22.577] (II) modesetting(0): EDID for output DisplayPort-0
[    22.577] (II) modesetting(0): Output VGA-0 disconnected
[    22.577] (II) modesetting(0): Output LVDS-0 connected
[    22.577] (II) modesetting(0): Output DVI-0 disconnected
[    22.577] (II) modesetting(0): Output DisplayPort-0 disconnected
[    22.577] (II) modesetting(0): Using exact sizes for initial modes
[    22.577] (II) modesetting(0): Output LVDS-0 using initial mode 1024x600
[    22.577] (II) modesetting(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    22.577] (==) modesetting(0): DPI set to (96, 96)
[    22.577] (II) Loading sub module "fb"
[    22.577] (II) LoadModule: "fb"
[    22.578] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.578] (II) Module fb: vendor="X.Org Foundation"
[    22.578]     compiled for 1.14.5, module version = 1.0.0
[    22.578]     ABI class: X.Org ANSI C Emulation, version 0.4
[    22.578] (II) UnloadModule: "fbdev"
[    22.578] (II) Unloading fbdev
[    22.578] (II) UnloadSubModule: "fbdevhw"
[    22.578] (II) Unloading fbdevhw
[    22.579] (==) Depth 24 pixmap format is 32 bpp
[    22.579] (==) modesetting(0): Backing store disabled
[    22.579] (==) modesetting(0): Silken mouse enabled
[    22.579] (II) modesetting(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    22.580] (==) modesetting(0): DPMS enabled
[    22.667] (--) RandR disabled
[    22.687] (II) SELinux: Disabled on system
[    22.690] (II) AIGLX: Screen 0 is not DRI2 capable
[    22.690] (II) AIGLX: Screen 0 is not DRI capable
[    22.963] (II) AIGLX: Loaded and initialized swrast
[    22.963] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    23.044] (II) modesetting(0): Damage tracking initialized
[    23.044] (II) modesetting(0): Setting screen physical size to 270 x 158
[    23.074] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.083] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    23.083] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.083] (II) LoadModule: "evdev"
[    23.084] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.100] (II) Module evdev: vendor="X.Org Foundation"
[    23.100]     compiled for 1.14.1, module version = 2.7.3
[    23.100]     Module class: X.Org XInput Driver
[    23.100]     ABI class: X.Org XInput driver, version 19.1
[    23.100] (II) Using input driver 'evdev' for 'Power Button'
[    23.100] (**) Power Button: always reports core events
[    23.101] (**) evdev: Power Button: Device: "/dev/input/event3"
[    23.101] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.101] (--) evdev: Power Button: Found keys
[    23.101] (II) evdev: Power Button: Configuring as keyboard
[    23.101] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    23.101] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    23.101] (**) Option "xkb_rules" "evdev"
[    23.102] (**) Option "xkb_model" "pc105"
[    23.102] (**) Option "xkb_layout" "dk"
[    23.109] (II) XKB: reuse xkmfile /var/lib/xkb/server-709407198873F5BF4583E7D562E34285659E3DFF.xkm
[    23.111] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    23.111] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    23.111] (II) Using input driver 'evdev' for 'Video Bus'
[    23.111] (**) Video Bus: always reports core events
[    23.111] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    23.111] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    23.111] (--) evdev: Video Bus: Found keys
[    23.111] (II) evdev: Video Bus: Configuring as keyboard
[    23.112] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5/event5"
[    23.112] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    23.112] (**) Option "xkb_rules" "evdev"
[    23.112] (**) Option "xkb_model" "pc105"
[    23.112] (**) Option "xkb_layout" "dk"
[    23.114] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.114] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.114] (II) Using input driver 'evdev' for 'Power Button'
[    23.114] (**) Power Button: always reports core events
[    23.114] (**) evdev: Power Button: Device: "/dev/input/event0"
[    23.114] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.114] (--) evdev: Power Button: Found keys
[    23.114] (II) evdev: Power Button: Configuring as keyboard
[    23.114] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    23.114] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    23.114] (**) Option "xkb_rules" "evdev"
[    23.114] (**) Option "xkb_model" "pc105"
[    23.114] (**) Option "xkb_layout" "dk"
[    23.116] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    23.116] (II) No input driver specified, ignoring this device.
[    23.116] (II) This device may have been added with another device file.
[    23.117] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    23.117] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    23.117] (II) Using input driver 'evdev' for 'Sleep Button'
[    23.117] (**) Sleep Button: always reports core events
[    23.117] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    23.117] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    23.117] (--) evdev: Sleep Button: Found keys
[    23.117] (II) evdev: Sleep Button: Configuring as keyboard
[    23.117] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    23.117] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    23.118] (**) Option "xkb_rules" "evdev"
[    23.118] (**) Option "xkb_model" "pc105"
[    23.118] (**) Option "xkb_layout" "dk"
[    23.119] (II) config/udev: Adding drm device (/dev/dri/card0)
[    23.119] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    23.120] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event10)
[    23.120] (II) No input driver specified, ignoring this device.
[    23.120] (II) This device may have been added with another device file.
[    23.121] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event11)
[    23.121] (II) No input driver specified, ignoring this device.
[    23.121] (II) This device may have been added with another device file.
[    23.122] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event9)
[    23.122] (II) No input driver specified, ignoring this device.
[    23.122] (II) This device may have been added with another device file.
[    23.123] (II) config/udev: Adding input device WebCam (/dev/input/event6)
[    23.123] (**) WebCam: Applying InputClass "evdev keyboard catchall"
[    23.123] (II) Using input driver 'evdev' for 'WebCam'
[    23.123] (**) WebCam: always reports core events
[    23.123] (**) evdev: WebCam: Device: "/dev/input/event6"
[    23.123] (--) evdev: WebCam: Vendor 0x64e Product 0xd214
[    23.123] (--) evdev: WebCam: Found keys
[    23.123] (II) evdev: WebCam: Configuring as keyboard
[    23.123] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/input/input6/event6"
[    23.123] (II) XINPUT: Adding extended input device "WebCam" (type: KEYBOARD, id 10)
[    23.123] (**) Option "xkb_rules" "evdev"
[    23.123] (**) Option "xkb_model" "pc105"
[    23.123] (**) Option "xkb_layout" "dk"
[    23.125] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    23.125] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.125] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    23.125] (**) AT Translated Set 2 keyboard: always reports core events
[    23.125] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    23.125] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    23.126] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    23.126] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    23.126] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    23.126] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    23.126] (**) Option "xkb_rules" "evdev"
[    23.126] (**) Option "xkb_model" "pc105"
[    23.126] (**) Option "xkb_layout" "dk"
[    23.127] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event12)
[    23.127] (**) ETPS/2 Elantech Touchpad: Applying InputClass "evdev touchpad catchall"
[    23.128] (**) ETPS/2 Elantech Touchpad: Applying InputClass "touchpad catchall"
[    23.128] (**) ETPS/2 Elantech Touchpad: Applying InputClass "Default clickpad buttons"
[    23.128] (II) LoadModule: "synaptics"
[    23.128] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    23.129] (II) Module synaptics: vendor="X.Org Foundation"
[    23.129]     compiled for 1.14.2, module version = 1.7.1
[    23.129]     Module class: X.Org XInput Driver
[    23.129]     ABI class: X.Org XInput driver, version 19.1
[    23.129] (II) Using input driver 'synaptics' for 'ETPS/2 Elantech Touchpad'
[    23.129] (**) ETPS/2 Elantech Touchpad: always reports core events
[    23.129] (**) Option "Device" "/dev/input/event12"
[    23.196] (--) synaptics: ETPS/2 Elantech Touchpad: x-axis range 0 - 2320 (res 0)
[    23.196] (--) synaptics: ETPS/2 Elantech Touchpad: y-axis range 0 - 928 (res 0)
[    23.196] (--) synaptics: ETPS/2 Elantech Touchpad: pressure range 0 - 255
[    23.197] (--) synaptics: ETPS/2 Elantech Touchpad: finger width range 0 - 15
[    23.197] (--) synaptics: ETPS/2 Elantech Touchpad: buttons: left right double triple
[    23.197] (--) synaptics: ETPS/2 Elantech Touchpad: Vendor 0x2 Product 0xe
[    23.197] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    23.197] (**) ETPS/2 Elantech Touchpad: always reports core events
[    23.248] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input12/event12"
[    23.248] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 12)
[    23.248] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MinSpeed is now constant deceleration 2.5
[    23.249] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) MaxSpeed is now 1.75
[    23.249] (**) synaptics: ETPS/2 Elantech Touchpad: (accel) AccelFactor is now 0.080
[    23.249] (**) ETPS/2 Elantech Touchpad: (accel) keeping acceleration scheme 1
[    23.249] (**) ETPS/2 Elantech Touchpad: (accel) acceleration profile 1
[    23.249] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[    23.250] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[    23.250] (--) synaptics: ETPS/2 Elantech Touchpad: touchpad found
[    23.250] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[    23.251] (**) ETPS/2 Elantech Touchpad: Ignoring device from InputClass "touchpad ignore duplicates"
[    23.257] (II) config/udev: Adding input device Acer WMI hotkeys (/dev/input/event7)
[    23.257] (**) Acer WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    23.257] (II) Using input driver 'evdev' for 'Acer WMI hotkeys'
[    23.257] (**) Acer WMI hotkeys: always reports core events
[    23.257] (**) evdev: Acer WMI hotkeys: Device: "/dev/input/event7"
[    23.257] (--) evdev: Acer WMI hotkeys: Vendor 0 Product 0
[    23.257] (--) evdev: Acer WMI hotkeys: Found keys
[    23.257] (II) evdev: Acer WMI hotkeys: Configuring as keyboard
[    23.257] (**) Option "config_info" "udev:/sys/devices/virtual/input/input7/event7"
[    23.258] (II) XINPUT: Adding extended input device "Acer WMI hotkeys" (type: KEYBOARD, id 13)
[    23.258] (**) Option "xkb_rules" "evdev"
[    23.258] (**) Option "xkb_model" "pc105"
[    23.258] (**) Option "xkb_layout" "dk"
[    23.259] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/event8)
[    23.259] (II) No input driver specified, ignoring this device.
[    23.259] (II) This device may have been added with another device file.
[    23.260] (II) config/udev: Adding input device Acer BMA150 accelerometer (/dev/input/js0)
[    23.260] (II) No input driver specified, ignoring this device.
[    23.260] (II) This device may have been added with another device file.
[    25.856] (II) modesetting(0): EDID vendor "AUO", prod id 24786
[    25.856] (II) modesetting(0): Printing DDC gathered Modelines:
[    25.856] (II) modesetting(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz eP)
[    26.230] (II) modesetting(0): Allocate new frame buffer 960x600 stride
[    27.644] (II) modesetting(0): EDID vendor "AUO", prod id 24786
[    27.644] (II) modesetting(0): Printing DDC gathered Modelines:
[    27.644] (II) modesetting(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz eP)
[    27.785] (II) modesetting(0): EDID vendor "AUO", prod id 24786
[    27.785] (II) modesetting(0): Printing DDC gathered Modelines:
[    27.785] (II) modesetting(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz eP)[/COLOR][/TD]
[/TR]
[/TABLE]

```

---

### Post by ubudog on 2014-01-29
What do you get when you run:
```
startx
```
from the console?

---

### Post by Hvidemose on 2014-01-29
After 5 min, I still have black screen on that command...

---

### Post by ubudog on 2014-01-29
> **Hvidemose said:**
> After 5 min, I still have black screen on that command...

Hmm, did you get any output from it?

---

### Post by jeanjd63 on 2014-01-30
Hello 
You can try this in a console (CTRL+ALT+F1) and become root :
**sudo -i**
1) stop lightdm :
**service lightdm stop**
2) create a xorg.conf :
**Xorg -configure**
3) modifie the xorg.conf.new generated 
**nano xorg.conf.new**
4) you keep only the first  Section "Device"  and you change :
 Driver   "xxxx"
by
Driver  "fglrx"
you save (CTRL+O) and quit (CTRL+X) 
5) you validate the new xorg.conf
**mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old **   no trouble if error message
[B]cp  xorg.conf.new  /etc/X11/xorg.conf
[/B]6) you restart computer
**reboot**
7) If there is no change, you suppress the file xorg.conf on a console :
[B]sudo  rm  /etc/X11/xorg.conf

[/B]Good luck

---

### Post by Hvidemose on 2014-01-30
```
[COLOR=#000000]Hmm, did you get any output from it?[/COLOR]
```
Unfortunately there was no output.

```
[COLOR=#000000]You can try this in a console (CTRL+ALT+F1) and become root :[/COLOR]
[B]sudo -i
1) stop lightdm :
[B]service lightdm stop
2) create a xorg.conf :
[B]Xorg -configure
3) modifie the xorg.conf.new generated 
[B]nano xorg.conf.new
4) you keep only the first Section "Device" and you change :
Driver "xxxx"
by
Driver "fglrx"
you save (CTRL+O) and quit (CTRL+X) 
5) you validate the new xorg.conf
[B]mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old no trouble if error message
[B]cp xorg.conf.new /etc/X11/xorg.conf
6) you restart computer
[B]reboot
7) If there is no change, you suppress the file xorg.conf on a console :
**sudo rm /etc/X11/xorg.conf**[/B][/B][/B][/B][/B][/B][/B]
```

I started on this, but when i come to the 4. point I have a problem. You say to keep only the first section, but mine does not seem to have any content.
Am i forgetting to press something?

---

### Post by jeanjd63 on 2014-01-30
Have you a file xorg.conf.new created ?
**sudo  ls  -l xorg.conf.new**
If yes can you give the contents ?
```
**sudo cat xorg.conf.new | pastebinit -b [http://paste.ubuntu.com](http://paste.ubuntu.com)**
```

---

### Post by Hvidemose on 2014-01-30
Oh, I thought step 3 did that. So no. Should i go back to console and do that?

---

### Post by jeanjd63 on 2014-01-30
You can do :
[B]Xorg -configure

[/B]What is the return ?

---

### Post by Hvidemose on 2014-01-30
```
[COLOR=#000000]You can do :[/COLOR]
[B]Xorg -configure

What is the return ?[/B]
```

Te response:
```
(EE)
Fatal server error:
(EE) Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock
and start again.
(EE)
(EE)
Please consult the The X.Org Foundation support
at http://wiki.x.org
for help.
(EE)
```

---

### Post by jeanjd63 on 2014-01-30
Have you first stop the service lightdm in root mode ?
**service lightdm  stop** 
what is the return ?

---

### Post by Hvidemose on 2014-01-30
I had to write it from the screen to my other computer. But hopefully no errors.

```
X.Org X Server 1.14.5Release Date: 2013-12-12
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-54-generic i686 ubuntu
Current Operating System: Linux diana-AOD270 3.11.0-15-generic#23-Ubuntu SMP Mon Dec 9 18:16:27 UTC 2013 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-genericroot=UUID=d250db3c-a789-4f1a-a84e-a27b6bd3209e ro quiet splashvt.handoff=7
Build Data: 18 December 2013 10:0351AM
xorg-server 2:1.14.5-1[COLOR=#000000][FONT=Times New Roman, serif]ubuntu2[/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]~saucy1[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman, serif][SIZE=3](Fortechnical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]Currentversion of pixman: 0.30.2[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]Beforereporting problems, check [http://wiki.x.org]("http://wiki.x.org/")[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]tomake sure that you have the latest version.[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]Makers:(–) probed, (**) from config file, (==) default settings,[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3](++)from command line, (!!) notice, (II) informational,[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3](WW)warning, (EE) error, (NI) not implemented, (??) unknown.[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3](==)Log file: ”/var/log/Xorg.0.log”, Time: Thu Jan 30 11:57:24 2014[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]Listof vidio drivers:[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]qxl[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]neomagic[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]openchrome[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]savage[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]mga[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]radeon[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]ati[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]siliconmotion[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]sis[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]mach64[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]intel[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]sisusb[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]vesa[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]vmvare[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]s3[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]modesetting[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]tdfx[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]cirrus[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]nouveau[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]r128[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]trident[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]fbdev[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3](++)Using config file: ”/root/xorg/.conf.new”[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3](==)Using system config directory ”/usr/share/X11/xorg.conf.d”[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]vesa:Ignoring device with a bound kernel driver[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]Numberof created screens does not match number of detected devices.[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]Configurationfailed.[/SIZE][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman](EE)Server terminated with error (2). Closing log file.[/FONT][/COLOR]
```

---

### Post by jeanjd63 on 2014-01-30
You can try :
```
cat [COLOR=#000000][FONT=Times New Roman]/root/xorg/.conf.new [/FONT][/COLOR]| pastebinit -b http://paste.ubuntu.com
```

---

### Post by Hvidemose on 2014-01-30
[COLOR=#000000]> [/COLOR][COLOR=#000000]You can try :
[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]cat [/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono][FONT=Times New Roman]/root/xorg/.conf.new [/FONT][/FONT][/COLOR][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]| pastebinit -b http://paste.ubuntu.com[/FONT][/COLOR]
```[COLOR=#000000]
I guess that this would mean I shall create a xorg.conf.new? - By typing: [/COLOR][B]sudo ls -l xorg.conf.new
[/B]But the response to that is:
```
Sudo: ls-l: command not found
```

---

### Post by jeanjd63 on 2014-01-30
The file created by **Xorg -configure** seems be **/root/xorg/.conf.new **and no **/root/xorg.conf.new**.
So the command post #20 will list the contains of this file.

---

### Post by Hvidemose on 2014-01-30
Cool :-) Here it is:

```
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"] 1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
 85
 86
 87
 88
 89
 90
 91
 92
 93
 94
 95
 96
 97
 98
 99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245
246
247
248
249
250
251
252
253
254
255
256
257
258
259
260
261
[/TD]
[TD="class: code"][COLOR=#000000]Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	Screen      2  "Screen2" RightOf "Screen1"
	Screen      3  "Screen3" RightOf "Screen2"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor2"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor3"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "Backlight"          	# <str>
        #Option     "DRI"                	# <str>
        #Option     "ColorKey"           	# <i>
        #Option     "VideoKey"           	# <i>
        #Option     "Tiling"             	# [<bool>]
        #Option     "LinearFramebuffer"  	# [<bool>]
        #Option     "VSync"              	# [<bool>]
        #Option     "PageFlip"           	# [<bool>]
        #Option     "SwapbuffersWait"    	# [<bool>]
        #Option     "TripleBuffer"       	# [<bool>]
        #Option     "XvPreferOverlay"    	# [<bool>]
        #Option     "HotPlug"            	# [<bool>]
        #Option     "ReprobeOutputs"     	# [<bool>]
        #Option     "XvMC"               	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
        #Option     "VirtualHeads"       	# <i>
        #Option     "TearFree"           	# [<bool>]
        #Option     "PerCrtcPixmaps"     	# [<bool>]
        #Option     "FallbackDebug"      	# [<bool>]
        #Option     "DebugFlushBatches"  	# [<bool>]
        #Option     "DebugFlushCaches"   	# [<bool>]
        #Option     "DebugWait"          	# [<bool>]
        #Option     "BufferCache"        	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card1"
	Driver      "vesa"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "kmsdev"             	# <str>
        #Option     "ShadowFB"           	# [<bool>]
	Identifier  "Card2"
	Driver      "modesetting"
	BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card3"
	Driver      "fbdev"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen2"
	Device     "Card2"
	Monitor    "Monitor2"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen3"
	Device     "Card3"
	Monitor    "Monitor3"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection[/COLOR]
[/TD]
[/TR]
[/TABLE]

```

---

### Post by jeanjd63 on 2014-01-30
You edit the file :
**nano  /root/xorg/.conf.new**
and in section Device you change :
[COLOR=#000000][FONT=Ubuntu Mono]**Driver      "intel"**
[/FONT][/COLOR]by
[COLOR=#000000][FONT=Ubuntu Mono]**Driver      "fglrx"**
[/FONT][/COLOR]
And in section Monitor, Device and Screen you keep only the first one as this.

```

[COLOR=#000000][FONT=Ubuntu Mono]Section "Monitor"    
Identifier   "Monitor0"    
VendorName   "Monitor Vendor"    
ModelName    "Monitor Model"EndSection[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]Section "Device"
    Identifier  "Card0"
    [B]Driver      "fglrx"
[/B]    BusID       "PCI:0:2:0"
EndSection

[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]


```

You save (CTRL+O) and quit (CTRL+X) it and do :

**mv  /etc/X11/xorg.conf  /etc/X11/xorg.conf.old**     if return error not a problem then :
[B]cp  /root/xorg/.conf.new  /etc/X11/xorg.conf

[/B]then you reboot :

[B]reboot

[/B]If don't work you can try to modify in xorg.conf :
[B]
sudo  nano  /etc/X11/xorg.conf
[/B]You change :
[COLOR=#000000][FONT=Ubuntu Mono]**Driver      "fglrx"**
[/FONT][/COLOR]by[B]
[COLOR=#000000][FONT=Ubuntu Mono]Driver      "intel"

[/FONT][/COLOR][/B][COLOR=#000000][FONT=Ubuntu Mono]You save and reboot.
If nothing work you can suppress xorg.conf :
**sudo  mv  /etc/X11/xorg.conf **[/FONT][/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono]/etc/X11/xorg.conf.bad[/FONT][/COLOR]**

---

### Post by Hvidemose on 2014-01-30
Unfortunately it did not work... :-(

---

### Post by jeanjd63 on 2014-01-30
You can try :
[B]sudo  apt-get  update
sudo  apt-get  dist-upgrade

[/B]I see nothing more to help you.

---

### Post by Hvidemose on 2014-01-30
Hmm, not really. But Thanks mate!

---

