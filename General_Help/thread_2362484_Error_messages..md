---
title: "Error messages."
date: 2017-05-29
forum: General Help
---

### Post by Furycd001 on 2017-05-29
HI Guys

As of today I receive the following error messages each time I open PINTA or GIMP. I can get past these error messages and continue to use both apps as normal, but it does bother me a little. Can anyone help me fix / remove these error messages in both apps. I have already tried ducking & googling with no success. Many thanks in advanced. 

[ATTACH=CONFIG]275344[/ATTACH]
[ATTACH=CONFIG]275345[/ATTACH]

---

### Post by ktat on 2017-05-29
Hi, it looks like the apps are trying to open a file at start up.

Are you launching them from the command line or from the start up menu?

---

### Post by kc1di on 2017-05-29
Hi seems like it's trying to open a file on a cd called fury had you at one time been running using that file for gimp?
if infact this is a file on the cd you would have to have the cd mounted prior to launching gimp. 
I'm not sure why it would be calling for that file on launch though.
According to the gimp error message it's looking for this file in your home  folder.  did you download a file from a cd and then tell gimp to you that file?

---

### Post by Furycd001 on 2017-05-29
I'm launching them from either xfce4-panel in xfce or from the main menu inside openbox. Either way I launch I still receive this error...

---

### Post by Furycd001 on 2017-05-29
I don't use cd's on this computer as the disk drive is broken. Any file that I open in PINTA or GIMP I always close before exiting the program. Also I never store files directly inside my home folder. Images are usually inside the pictures folder or another folder that I have in my home directory...

---

### Post by ajgreeny on 2017-05-29
Does the same error appear if you start gimp or pinta with terminal?

What is the command that starts these two applications from the menu, or the command in their respective launchers in the panel?

---

### Post by #&amp;thj^% on 2017-05-29
Some more information might be needed:
Lets see if we can get it to show some more, run this in a terminal:
```
gimp --verbose
```
And paste back here using Code tags Please!
Nin'jed by ajgrenny :)

---

### Post by Impavidus on 2017-05-29
Those file names, %F and %U, don't really look like filenames, but more like placeholders as used in .desktop files. They exist so that programs like thunar know where to put the filename when you want to open a file by double clicking it in the file manager. If you just start the application without instructing it to open a file directly, the %F or %U should not be included on the command line. So something must be going wrong in the processing of the .desktop files for those applications.

---

### Post by Furycd001 on 2017-05-30
In xfce PINTA is run as **pinta %F **&GIMP is run as [B]gimp-2.8 %
[/B]In openbox PINTA is run as **pinta **& GIMP is run as **&#8203;gimp**

[B]
PINTA
[/B]```
furycd001 >> pinta --verbosePinta: System.FormatException: Unsupported file format
  at Pinta.Core.WorkspaceManager.OpenFile (System.String file, Gtk.Window parent) <0x4051c3d0 + 0x000d7> in <filename unknown>:0 
```

[B]
GIMP
[/B]```
furycd001 >> gimp --verboseINIT: gimp_load_config
Parsing '/home/furycd001/.gimp-2.8/unitrc'
Parsing '/etc/gimp/2.0/gimprc'
Parsing '/home/furycd001/.gimp-2.8/gimprc'
gimp_composite: verbose=no
Processor instruction sets: +mmx +sse +sse2 -3dnow -altivec -vis


(gimp:1755): GLib-GObject-WARNING **: g_object_set_valist: object class 'GeglConfig' has no property named 'cache-size'


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAA9C0 from "gimp:point-layer-mode" to "gimp:dissolve-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAAE90 from "gimp:point-layer-mode" to "gimp:behind-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAB520 from "gimp:point-layer-mode" to "gimp:multiply-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAB8F0 from "gimp:point-layer-mode" to "gimp:screen-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AABCE0 from "gimp:point-layer-mode" to "gimp:overlay-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAC110 from "gimp:point-layer-mode" to "gimp:difference-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAC4D0 from "gimp:point-layer-mode" to "gimp:addition-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAC910 from "gimp:point-layer-mode" to "gimp:subtract-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AACCD0 from "gimp:point-layer-mode" to "gimp:darken-only-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAD120 from "gimp:point-layer-mode" to "gimp:lighten-only-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAD530 from "gimp:point-layer-mode" to "gimp:hue-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAD860 from "gimp:point-layer-mode" to "gimp:saturation-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AADCC0 from "gimp:point-layer-mode" to "gimp:color-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAE130 from "gimp:point-layer-mode" to "gimp:value-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAE8F0 from "gimp:point-layer-mode" to "gimp:divide-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAED40 from "gimp:point-layer-mode" to "gimp:dodge-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAF0B0 from "gimp:point-layer-mode" to "gimp:burn-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAF500 from "gimp:point-layer-mode" to "gimp:hardlight-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAF8A0 from "gimp:point-layer-mode" to "gimp:softlight-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AAFCA0 from "gimp:point-layer-mode" to "gimp:grain-extract-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AB0100 from "gimp:point-layer-mode" to "gimp:grain-merge-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AB04B0 from "gimp:point-layer-mode" to "gimp:color-erase-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AB08A0 from "gimp:point-layer-mode" to "gimp:erase-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AB0CC0 from "gimp:point-layer-mode" to "gimp:replace-mode"


(gimp:1755): GEGL-gegl-operation.c-WARNING **: Cannot change name of operation class 0x2AB1090 from "gimp:point-layer-mode" to "gimp:anti-erase-mode"
Adding theme 'Small' (/usr/share/gimp/2.0/themes/Small)
Adding theme 'Default' (/usr/share/gimp/2.0/themes/Default)
Writing '/home/furycd001/.gimp-2.8/themerc'
Trying splash '/home/furycd001/.gimp-2.8/gimp-splash.png' ... failed
Trying splash '/usr/share/gimp/2.0/images/gimp-splash.png' ... OK
INIT: gimp_initialize
INIT: gimp_real_initialize
INIT: gui_initialize_after_callback
INIT: gimp_restore
Parsing '/home/furycd001/.gimp-2.8/parasiterc'
Loading 'brush factory' data
Loading 'dynamics factory' data
Loading 'pattern factory' data
Loading 'palette factory' data
Loading 'gradient factory' data
Loading fonts
Loading 'tool preset factory' data
Parsing '/home/furycd001/.gimp-2.8/templaterc'
Parsing '/home/furycd001/.gimp-2.8/modulerc'
Loading module '/usr/lib/gimp/2.0/modules/libcontroller-midi.so'
Unloading module '/usr/lib/gimp/2.0/modules/libcontroller-midi.so'
Loading module '/usr/lib/gimp/2.0/modules/libcolor-selector-cmyk.so'
Unloading module '/usr/lib/gimp/2.0/modules/libcolor-selector-cmyk.so'
Loading module '/usr/lib/gimp/2.0/modules/libdisplay-filter-high-contrast.so'
Unloading module '/usr/lib/gimp/2.0/modules/libdisplay-filter-high-contrast.so'
Loading module '/usr/lib/gimp/2.0/modules/libcontroller-linux-input.so'
Unloading module '/usr/lib/gimp/2.0/modules/libcontroller-linux-input.so'
Loading module '/usr/lib/gimp/2.0/modules/libdisplay-filter-gamma.so'
Unloading module '/usr/lib/gimp/2.0/modules/libdisplay-filter-gamma.so'
Loading module '/usr/lib/gimp/2.0/modules/libdisplay-filter-proof.so'
Unloading module '/usr/lib/gimp/2.0/modules/libdisplay-filter-proof.so'
Loading module '/usr/lib/gimp/2.0/modules/libdisplay-filter-color-blind.so'
Unloading module '/usr/lib/gimp/2.0/modules/libdisplay-filter-color-blind.so'
Loading module '/usr/lib/gimp/2.0/modules/libcolor-selector-wheel.so'
Unloading module '/usr/lib/gimp/2.0/modules/libcolor-selector-wheel.so'
Loading module '/usr/lib/gimp/2.0/modules/libcolor-selector-water.so'
Unloading module '/usr/lib/gimp/2.0/modules/libcolor-selector-water.so'
Loading module '/usr/lib/gimp/2.0/modules/libdisplay-filter-lcms.so'
Unloading module '/usr/lib/gimp/2.0/modules/libdisplay-filter-lcms.so'
INIT: gui_restore_callback
clipboard: writable pixbuf format: image/png
clipboard: writable pixbuf format: image/bmp
clipboard: writable pixbuf format: image/x-bmp
clipboard: writable pixbuf format: image/x-MS-bmp
clipboard: writable pixbuf format: image/tiff
clipboard: writable pixbuf format: image/x-icon
clipboard: writable pixbuf format: image/x-ico
clipboard: writable pixbuf format: image/x-win-bitmap
clipboard: writable pixbuf format: image/jpeg
Parsing '/home/furycd001/.gimp-2.8/sessionrc'
Parsing '/home/furycd001/.gimp-2.8/dockrc'
Parsing '/home/furycd001/.gimp-2.8/toolrc'
Parsing '/home/furycd001/.gimp-2.8/contextrc'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-rect-select-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-ellipse-select-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-free-select-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-fuzzy-select-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-by-color-select-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-iscissors-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-foreground-select-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-vector-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-color-picker-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-zoom-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-measure-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-move-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-align-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-crop-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-rotate-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-scale-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-shear-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-perspective-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-flip-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-cage-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-text-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-bucket-fill-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-blend-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-pencil-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-paintbrush-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-eraser-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-airbrush-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-ink-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-clone-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-heal-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-perspective-clone-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-convolve-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-smudge-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-dodge-burn-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-desaturate-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-color-balance-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-hue-saturation-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-colorize-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-brightness-contrast-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-threshold-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-levels-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-curves-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-posterize-tool'
Parsing '/home/furycd001/.gimp-2.8/tool-options/gimp-gegl-tool'
INIT: gimp_real_restore
Parsing '/home/furycd001/.gimp-2.8/pluginrc'
Starting extension: 'extension-script-fu'
INIT: gui_restore_after_callback
Parsing '/home/furycd001/.gimp-2.8/menurc'
Parsing '/home/furycd001/.gimp-2.8/devicerc'
Parsing '/home/furycd001/.gimp-2.8/controllerrc'
Parsing '/home/furycd001/.gimp-2.8/colorrc'
loading menu '/usr/share/gimp/2.0/menus/image-menu.xml' for /image-menubar
Loading module '/usr/lib/gimp/2.0/modules/libdisplay-filter-lcms.so'
EXIT: gimp_exit
EXIT: gui_exit_callback
Writing '/home/furycd001/.gimp-2.8/sessionrc'
Writing '/home/furycd001/.gimp-2.8/dockrc'
Writing '/home/furycd001/.gimp-2.8/colorrc'
Writing '/home/furycd001/.gimp-2.8/menurc'
Writing '/home/furycd001/.gimp-2.8/controllerrc'
Writing '/home/furycd001/.gimp-2.8/toolrc'
EXIT: gimp_real_exit
Terminating plug-in: '/usr/lib/gimp/2.0/plug-ins/script-fu'
Writing '/home/furycd001/.gimp-2.8/templaterc'
Writing '/home/furycd001/.gimp-2.8/parasiterc'
Writing '/home/furycd001/.gimp-2.8/unitrc'
EXIT: gui_exit_after_callback
EXIT: app_exit_after_callback

```

Would these errors maybe disappear if I uninstalled and re-installed both applications ??

---

### Post by kc1di on 2017-05-30
seems in gimp anyway that it can not find a theme in a folder in your home directory named /furycd001  Check and see if you find that folder in your /home directory at all.
At this point I'm not sure if a reinstall will work , but it may.  I would go into the home folder after uninstalling gimp and delete any folders/hidden files that have to do with gimp.

then reinstall--

---

### Post by Furycd001 on 2017-05-30
> **kc1di said:**
> seems in gimp anyway that it can not find a theme in a folder in your home directory named /furycd001  Check and see if you find that folder in your /home directory at all.
At this point I'm not sure if a reinstall will work , but it may.  I would go into the home folder after uninstalling gimp and delete any folders/hidden files that have to do with gimp.

then reinstall--

Ok so I removed both applications, and then reinstalled them and everything appears fine now. I can launch both applications without receiving any error messages now.
```
sudo apt-get update && sudo apt-get remove --purge gimp pinta && sudo apt-get install gimp pinta
```

---

### Post by kc1di on 2017-05-30
Glad that worked for you :)

---

