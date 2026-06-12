---
title: "Trouble Compiling and Installing Xvkbd"
date: 2007-10-14
forum: General Help
---

### Post by yosef on 2007-10-14
I am trying to compile and install xvkbd 2.8 from source and I am getting errors.  I am running Xubuntu feisty and I have both build-essential and gcc installed. I use the instructions from [here]("http://homepage3.nifty.com/tsato/xvkbd/")  which are just three commands and I get nothing but error messages from the make install

```

~/Desktop/xvkbd-2.8$ make install
rm -f xvkbd.o
gcc -m32 -c -g -O2 -fno-strict-aliasing         -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                          -D_POSIX_SOURCE -D_XOPEN_SOURCE      -D_BSD_SOURCE -D_SVID_SOURCE                                 -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64                                                       -DFUNCPROTO=15 -DNARROWPROTO   -DXAW3D -DUSE_XTEST -DUSE_I18N    xvkbd.c
xvkbd.c:27:27: error: X11/Intrinsic.h: No such file or directory
xvkbd.c:28:28: error: X11/StringDefs.h: No such file or directory
xvkbd.c:29:23: error: X11/Shell.h: No such file or directory
xvkbd.c:30:24: error: X11/keysym.h: No such file or directory
xvkbd.c:31:28: error: X11/cursorfont.h: No such file or directory
xvkbd.c:32:51: error: X11/Xproto.h: No such file or directory
xvkbd.c:33:25: error: X11/Xaw/Box.h: No such file or directory
xvkbd.c:34:26: error: X11/Xaw/Form.h: No such file or directory
xvkbd.c:35:29: error: X11/Xaw/Command.h: No such file or directory
xvkbd.c:36:30: error: X11/Xaw/Repeater.h: No such file or directory
xvkbd.c:37:27: error: X11/Xaw/Label.h: No such file or directory
xvkbd.c:38:32: error: X11/Xaw/MenuButton.h: No such file or directory
xvkbd.c:39:32: error: X11/Xaw/SimpleMenu.h: No such file or directory
xvkbd.c:40:28: error: X11/Xaw/SmeBSB.h: No such file or directory
xvkbd.c:41:29: error: X11/Xaw/SmeLine.h: No such file or directory
xvkbd.c:42:31: error: X11/Xaw/AsciiText.h: No such file or directory
xvkbd.c:43:30: error: X11/Xaw/Viewport.h: No such file or directory
xvkbd.c:44:26: error: X11/Xaw/List.h: No such file or directory
xvkbd.c:45:29: error: X11/Xmu/WinUtil.h: No such file or directory
xvkbd.c:48:26: error: X11/Xlocale.h: No such file or directory
xvkbd.c:52:35: error: X11/extensions/XTest.h: No such file or directory
In file included from xvkbd.c:55:
resources.h:23: error: expected specifier-qualifier-list before ‘String’
resources.h:97: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘FindWidget’
xvkbd.c:211: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘application_resources’
xvkbd.c:361: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘options’
xvkbd.c:411: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘app_con’
xvkbd.c:412: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘toplevel’
xvkbd.c:413: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘key_widgets’
xvkbd.c:414: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘main_menu’
xvkbd.c:416: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘toplevel_height’
xvkbd.c:418: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
xvkbd.c:419: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘wm_delete_window’
xvkbd.c:421: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
xvkbd.c:424: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘error_detected’
xvkbd.c:429: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘altgr_keysym’
xvkbd.c:434: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
xvkbd.c:436: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘toplevel_parent’
xvkbd.c:437: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘focused_window’
xvkbd.c:438: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘focused_subwindow’
xvkbd.c:440: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘xvkbd_pixmap’
xvkbd.c:442: error: expected ‘)’ before ‘keysym’
xvkbd.c:444: error: expected ‘)’ before ‘remake’
xvkbd.c:445: error: expected ‘)’ before ‘form’
xvkbd.c:446: error: expected ‘)’ before ‘form’
xvkbd.c:447: error: expected ‘)’ before ‘form’
xvkbd.c:450: error: expected ‘)’ before ‘w’
xvkbd.c:456: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘FindWindow’
xvkbd.c: In function ‘GetFocusedWindow’:
xvkbd.c:500: error: ‘Cursor’ undeclared (first use in this function)
xvkbd.c:500: error: (Each undeclared identifier is reported only once
xvkbd.c:500: error: for each function it appears in.)
xvkbd.c:500: error: expected ‘;’ before ‘cursor’
xvkbd.c:501: error: ‘XEvent’ undeclared (first use in this function)
xvkbd.c:501: error: expected ‘;’ before ‘event’
xvkbd.c:502: error: ‘Window’ undeclared (first use in this function)
xvkbd.c:502: error: expected ‘;’ before ‘target_root’
xvkbd.c:505: error: expected ‘;’ before ‘junk_w’
xvkbd.c:510: error: ‘target_dpy’ undeclared (first use in this function)
xvkbd.c:511: error: ‘target_root’ undeclared (first use in this function)
xvkbd.c:513: error: ‘cursor’ undeclared (first use in this function)
xvkbd.c:513: error: ‘dpy’ undeclared (first use in this function)
xvkbd.c:513: error: ‘XC_crosshair’ undeclared (first use in this function)
xvkbd.c:513: error: ‘XC_dot’ undeclared (first use in this function)
xvkbd.c:514: error: ‘False’ undeclared (first use in this function)
xvkbd.c:514: error: ‘ButtonPressMask’ undeclared (first use in this function)
xvkbd.c:515: error: ‘GrabModeSync’ undeclared (first use in this function)
xvkbd.c:515: error: ‘GrabModeAsync’ undeclared (first use in this function)
xvkbd.c:515: error: ‘None’ undeclared (first use in this function)
xvkbd.c:516: error: ‘CurrentTime’ undeclared (first use in this function)
xvkbd.c:517: error: ‘struct appres_struct’ has no member named ‘debug’
xvkbd.c:522: error: ‘toplevel’ undeclared (first use in this function)
xvkbd.c:526: error: ‘SyncPointer’ undeclared (first use in this function)
xvkbd.c:528: error: ‘event’ undeclared (first use in this function)
xvkbd.c:530: error: ‘ButtonPress’ undeclared (first use in this function)
xvkbd.c:531: error: ‘junk_w’ undeclared (first use in this function)
xvkbd.c:537: error: ‘struct appres_struct’ has no member named ‘debug’
xvkbd.c:543: error: ‘child’ undeclared (first use in this function)
xvkbd.c:553: error: ‘focused_window’ undeclared (first use in this function)
xvkbd.c:560: error: ‘struct appres_struct’ has no member named ‘debug’
xvkbd.c:571: error: ‘struct appres_struct’ has no member named ‘debug’
xvkbd.c:576: error: ‘focused_subwindow’ undeclared (first use in this function)
xvkbd.c:586: error: ‘struct appres_struct’ has no member named ‘debug’
xvkbd.c:589: error: ‘struct appres_struct’ has no member named ‘list_widgets’
xvkbd.c:589: error: ‘struct appres_struct’ has no member named ‘widget’
xvkbd.c:590: error: ‘struct appres_struct’ has no member named ‘widget’
xvkbd.c: At top level:
xvkbd.c:604: error: expected declaration specifiers or ‘...’ before ‘Boolean’
xvkbd.c: In function ‘ReadKeymap’:
xvkbd.c:610: error: ‘KeySym’ undeclared (first use in this function)
xvkbd.c:610: error: expected ‘;’ before ‘keysym’
xvkbd.c:611: error: ‘XModifierKeymap’ undeclared (first use in this function)
xvkbd.c:611: error: ‘modifiers’ undeclared (first use in this function)
xvkbd.c:612: error: ‘Widget’ undeclared (first use in this function)
xvkbd.c:612: error: expected ‘;’ before ‘w’
xvkbd.c:615: error: ‘target_dpy’ undeclared (first use in this function)
xvkbd.c:616: error: ‘keysym_table’ undeclared (first use in this function)
xvkbd.c:624: error: ‘NoSymbol’ undeclared (first use in this function)
xvkbd.c:625: error: ‘XK_A’ undeclared (first use in this function)
xvkbd.c:625: error: ‘XK_Z’ undeclared (first use in this function)
xvkbd.c:626: error: ‘XK_a’ undeclared (first use in this function)
xvkbd.c:626: error: ‘XK_z’ undeclared (first use in this function)
xvkbd.c:637: error: ‘altgr_keysym’ undeclared (first use in this function)
xvkbd.c:644: error: ‘keysym’ undeclared (first use in this function)
xvkbd.c:645: error: ‘XK_Alt_L’ undeclared (first use in this function)
xvkbd.c:645: error: ‘XK_Alt_R’ undeclared (first use in this function)
xvkbd.c:647: error: ‘XK_Meta_L’ undeclared (first use in this function)
xvkbd.c:647: error: ‘XK_Meta_R’ undeclared (first use in this function)
xvkbd.c:649: error: ‘XK_Mode_switch’ undeclared (first use in this function)
xvkbd.c:650: error: ‘struct appres_struct’ has no member named ‘debug’
xvkbd.c:652: error: ‘XK_ISO_Level3_Shift’ undeclared (first use in this function)
xvkbd.c:653: error: ‘struct appres_struct’ has no member named ‘debug’
xvkbd.c:663: error: ‘struct appres_struct’ has no member named ‘debug’
xvkbd.c:666: error: ‘struct appres_struct’ has no member named ‘debug’
xvkbd.c:684: error: ‘w’ undeclared (first use in this function)
xvkbd.c:684: error: ‘toplevel’ undeclared (first use in this function)
xvkbd.c:685: error: ‘None’ undeclared (first use in this function)
xvkbd.c:686: error: ‘XK_Multi_key’ undeclared (first use in this function)
xvkbd.c:687: error: ‘struct appres_struct’ has no member named ‘auto_add_keysym’
xvkbd.c:687: error: ‘FALSE’ undeclared (first use in this function)
xvkbd.c:693: error: ‘struct appres_struct’ has no member named ‘xtest’
xvkbd.c:693: error: ‘struct appres_struct’ has no member named ‘altgr_keycode’
xvkbd.c:694: error: ‘TRUE’ undeclared (first use in this function)
xvkbd.c:695: error: ‘struct appres_struct’ has no member named ‘debug’
xvkbd.c:697: error: ‘struct appres_struct’ has no member named ‘altgr_keycode’
xvkbd.c:704: error: too many arguments to function ‘Highlight’
xvkbd.c: At top level:
xvkbd.c:715: error: expected ‘)’ before ‘*’ token
xvkbd.c:736: error: expected ‘)’ before ‘*’ token
xvkbd.c:834: error: expected ‘)’ before ‘keysym’
xvkbd.c:878: error: expected ‘)’ before ‘keysym’
xvkbd.c:914: error: expected ‘)’ before ‘keysym’
xvkbd.c:1148: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘completion_panel’
xvkbd.c:1149: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘completion_entry’
xvkbd.c:1150: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘completion_list’
xvkbd.c:1165: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘word_list’
xvkbd.c: In function ‘ReadCompletionDictionary’:
xvkbd.c:1180: error: ‘struct appres_struct’ has no member named ‘dict_file’
xvkbd.c:1183: error: ‘struct appres_struct’ has no member named ‘dict_file’
xvkbd.c:1191: warning: assignment makes pointer from integer without a cast
xvkbd.c: At top level:
xvkbd.c:1201: error: expected ‘)’ before ‘keysym’
xvkbd.c:1237: error: expected ‘)’ before ‘w’
xvkbd.c: In function ‘PopupCompletionPanel’:
xvkbd.c:1260: error: ‘Widget’ undeclared (first use in this function)
xvkbd.c:1260: error: expected ‘;’ before ‘form’
xvkbd.c:1262: error: ‘completion_panel’ undeclared (first use in this function)
xvkbd.c:1262: error: ‘None’ undeclared (first use in this function)
xvkbd.c:1263: error: ‘transientShellWidgetClass’ undeclared (first use in this function)
xvkbd.c:1264: error: ‘toplevel’ undeclared (first use in this function)
xvkbd.c:1265: error: ‘form’ undeclared (first use in this function)
xvkbd.c:1265: error: ‘formWidgetClass’ undeclared (first use in this function)
xvkbd.c:1266: error: ‘label’ undeclared (first use in this function)
xvkbd.c:1266: error: ‘labelWidgetClass’ undeclared (first use in this function)
xvkbd.c:1267: error: ‘completion_entry’ undeclared (first use in this function)
xvkbd.c:1268: error: ‘XtNfromHoriz’ undeclared (first use in this function)
xvkbd.c:1269: error: ‘view’ undeclared (first use in this function)
xvkbd.c:1269: error: ‘viewportWidgetClass’ undeclared (first use in this function)
xvkbd.c:1270: error: ‘XtNfromVert’ undeclared (first use in this function)
xvkbd.c:1271: error: ‘completion_list’ undeclared (first use in this function)
xvkbd.c:1271: error: ‘listWidgetClass’ undeclared (first use in this function)
xvkbd.c:1272: error: ‘XtNcallback’ undeclared (first use in this function)
xvkbd.c:1272: error: ‘CompletionWordSelected’ undeclared (first use in this function)
xvkbd.c:1274: error: ‘dpy’ undeclared (first use in this function)
xvkbd.c:1274: error: ‘wm_delete_window’ undeclared (first use in this function)
xvkbd.c:1276: error: ‘XtGrabNone’ undeclared (first use in this function)
xvkbd.c:1277: error: ‘NoSymbol’ undeclared (first use in this function)
xvkbd.c: At top level:
xvkbd.c:1290: error: expected ‘)’ before ‘w’
xvkbd.c: In function ‘SendString’:
xvkbd.c:1317: error: ‘None’ undeclared (first use in this function)
xvkbd.c:1321: error: ‘ShiftMask’ undeclared (first use in this function)
xvkbd.c:1322: error: ‘ControlMask’ undeclared (first use in this function)
xvkbd.c:1325: error: ‘XK_BackSpace’ undeclared (first use in this function)
xvkbd.c:1326: error: ‘XK_Tab’ undeclared (first use in this function)
xvkbd.c:1327: error: ‘XK_Linefeed’ undeclared (first use in this function)
xvkbd.c:1328: error: ‘XK_Return’ undeclared (first use in this function)
xvkbd.c:1329: error: ‘XK_Escape’ undeclared (first use in this function)
xvkbd.c:1330: error: ‘XK_Delete’ undeclared (first use in this function)
xvkbd.c: In function ‘SendFileContent’:
xvkbd.c:1357: error: ‘XK_Return’ undeclared (first use in this function)
xvkbd.c:1359: error: ‘XK_Escape’ undeclared (first use in this function)
xvkbd.c:1361: error: ‘XK_Delete’ undeclared (first use in this function)
xvkbd.c:1363: error: ‘ControlMask’ undeclared (first use in this function)
xvkbd.c: At top level:
xvkbd.c:1374: error: expected declaration specifiers or ‘...’ before ‘Boolean’
xvkbd.c: In function ‘Highlight’:
xvkbd.c:1377: error: ‘Widget’ undeclared (first use in this function)
xvkbd.c:1377: error: expected ‘;’ before ‘w’
xvkbd.c:1380: error: ‘w’ undeclared (first use in this function)
xvkbd.c:1380: error: ‘toplevel’ undeclared (first use in this function)
xvkbd.c:1381: error: ‘None’ undeclared (first use in this function)
xvkbd.c:1383: error: ‘target_dpy’ undeclared (first use in this function)
xvkbd.c:1383: error: ‘dpy’ undeclared (first use in this function)
xvkbd.c:1384: error: ‘XtNbackground’ undeclared (first use in this function)
xvkbd.c:1384: error: ‘struct appres_struct’ has no member named ‘focus_background’
xvkbd.c:1386: error: ‘struct appres_struct’ has no member named ‘remote_focus_background’
xvkbd.c:1387: error: ‘state’ undeclared (first use in this function)
xvkbd.c:1388: error: ‘XtNforeground’ undeclared (first use in this function)
xvkbd.c:1388: error: ‘struct appres_struct’ has no member named ‘highlight_foreground’
xvkbd.c:1390: error: ‘struct appres_struct’ has no member named ‘special_foreground’
xvkbd.c:1393: error: ‘struct appres_struct’ has no member named ‘highlight_background’
xvkbd.c:1394: error: ‘struct appres_struct’ has no member named ‘highlight_foreground’
xvkbd.c:1396: error: ‘struct appres_struct’ has no member named ‘special_background’
xvkbd.c:1397: error: ‘struct appres_struct’ has no member named ‘special_foreground’
xvkbd.c: At top level:
xvkbd.c:1405: error: expected ‘)’ before ‘force’
xvkbd.c:1561: error: expected ‘)’ before ‘w’
xvkbd.c:1581: error: expected ‘)’ before ‘w’
xvkbd.c:1593: error: expected ‘)’ before ‘w’
xvkbd.c:1613: error: expected ‘)’ before ‘w’
xvkbd.c: In function ‘PopupLayoutPanel’:
xvkbd.c:1675: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘layout_panel’
xvkbd.c:1675: error: ‘layout_panel’ undeclared (first use in this function)
xvkbd.c:1675: error: ‘None’ undeclared (first use in this function)
xvkbd.c:1679: error: ‘Widget’ undeclared (first use in this function)
xvkbd.c:1679: error: expected ‘;’ before ‘box’
xvkbd.c:1682: error: ‘transientShellWidgetClass’ undeclared (first use in this function)
xvkbd.c:1683: error: ‘toplevel’ undeclared (first use in this function)
xvkbd.c:1684: error: ‘box’ undeclared (first use in this function)
xvkbd.c:1684: error: ‘boxWidgetClass’ undeclared (first use in this function)
xvkbd.c:1686: error: ‘struct appres_struct’ has no member named ‘customizations’
xvkbd.c:1686: warning: assignment makes pointer from integer without a cast
xvkbd.c:1691: error: ‘button’ undeclared (first use in this function)
xvkbd.c:1691: error: ‘commandWidgetClass’ undeclared (first use in this function)
xvkbd.c:1693: error: ‘XtNcallback’ undeclared (first use in this function)
xvkbd.c:1693: error: ‘XtCallbackProc’ undeclared (first use in this function)
xvkbd.c:1693: error: expected ‘)’ before ‘LayoutSelected’
xvkbd.c:1697: error: ‘dpy’ undeclared (first use in this function)
xvkbd.c:1697: error: ‘wm_delete_window’ undeclared (first use in this function)
xvkbd.c:1702: error: ‘XtGrabNone’ undeclared (first use in this function)
xvkbd.c: At top level:
xvkbd.c:1708: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘about_panel’
xvkbd.c:1709: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘keypad_panel’
xvkbd.c:1710: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sun_fkey_panel’
xvkbd.c:1711: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘deadkey_panel’
xvkbd.c:1712: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘display_panel’
xvkbd.c:1713: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘display_status’
xvkbd.c:1719: error: expected ‘)’ before ‘w’
xvkbd.c:1756: error: expected ‘)’ before ‘w’
xvkbd.c:1871: error: expected ‘)’ before ‘w’
xvkbd.c:1885: error: expected ‘)’ before ‘w’
xvkbd.c:1942: error: expected declaration specifiers or ‘...’ before ‘Boolean’
xvkbd.c:1943: error: expected ‘)’ before ‘w’
xvkbd.c:1945: error: expected ‘)’ before ‘w’
xvkbd.c: In function ‘RedefineKeys’:
xvkbd.c:2165: warning: initialization makes pointer from integer without a cast
xvkbd.c:2189: warning: assignment makes pointer from integer without a cast
xvkbd.c: At top level:
xvkbd.c:2201: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘MakeKey’
xvkbd.c:2271: error: expected ‘)’ before ‘form’
xvkbd.c:2320: error: expected ‘)’ before ‘form’
xvkbd.c:2354: error: expected ‘)’ before ‘form’
xvkbd.c: In function ‘RefreshMainMenu’:
xvkbd.c:2376: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘check_pixmap’
xvkbd.c:2376: error: ‘check_pixmap’ undeclared (first use in this function)
xvkbd.c:2376: error: ‘None’ undeclared (first use in this function)
xvkbd.c:2379: error: ‘dpy’ undeclared (first use in this function)
xvkbd.c:2382: error: ‘main_menu’ undeclared (first use in this function)
xvkbd.c:2383: error: ‘XtNrightBitmap’ undeclared (first use in this function)
xvkbd.c:2383: error: ‘struct appres_struct’ has no member named ‘keypad’
xvkbd.c:2385: error: ‘struct appres_struct’ has no member named ‘function_key’
xvkbd.c:2388: error: ‘struct appres_struct’ has no member named ‘xtest’
xvkbd.c:2391: error: ‘struct appres_struct’ has no member named ‘quick_modifiers’
xvkbd.c:2393: error: ‘struct appres_struct’ has no member named ‘shift_lock’
xvkbd.c:2395: error: ‘struct appres_struct’ has no member named ‘altgr_lock’
xvkbd.c:2397: error: ‘struct appres_struct’ has no member named ‘modifiers_lock’
xvkbd.c:2399: error: ‘struct appres_struct’ has no member named ‘always_on_top’
xvkbd.c:2401: error: ‘struct appres_struct’ has no member named ‘function_key’
xvkbd.c:2402: error: ‘target_dpy’ undeclared (first use in this function)
xvkbd.c: At top level:
xvkbd.c:2405: error: expected ‘)’ before ‘remake’
xvkbd.c:2592: error: expected ‘)’ before ‘w’
xvkbd.c:2611: error: expected ‘)’ before ‘w’
xvkbd.c: In function ‘ReadFuncionKeys’:
xvkbd.c:2658: error: ‘struct appres_struct’ has no member named ‘key_file’
xvkbd.c:2659: error: ‘struct appres_struct’ has no member named ‘key_file’
xvkbd.c:2660: error: ‘struct appres_struct’ has no member named ‘key_file’
xvkbd.c:2662: error: ‘struct appres_struct’ has no member named ‘key_file’
xvkbd.c:2671: error: ‘struct appres_struct’ has no member named ‘quick_modifiers’
xvkbd.c:2673: error: ‘struct appres_struct’ has no member named ‘shift_lock’
xvkbd.c:2675: error: ‘struct appres_struct’ has no member named ‘altgr_lock’
xvkbd.c:2677: error: ‘struct appres_struct’ has no member named ‘modifiers_lock’
xvkbd.c:2688: warning: assignment makes pointer from integer without a cast
xvkbd.c: At top level:
xvkbd.c:2698: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘edit_fkey_panel’
xvkbd.c:2699: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fkey_menu_button’
xvkbd.c:2700: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fkey_value_menu_button’
xvkbd.c:2701: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fkey_value_entry’
xvkbd.c:2706: error: expected ‘)’ before ‘w’
xvkbd.c:2721: error: expected ‘)’ before ‘w’
xvkbd.c: In function ‘CloseFunctionKeyPanel’:
xvkbd.c:2786: error: ‘edit_fkey_panel’ undeclared (first use in this function)
xvkbd.c: In function ‘SaveFunctionKey’:
xvkbd.c:2794: error: ‘edit_fkey_panel’ undeclared (first use in this function)
xvkbd.c:2794: error: ‘None’ undeclared (first use in this function)
xvkbd.c:2802: error: ‘struct appres_struct’ has no member named ‘quick_modifiers’
xvkbd.c:2803: error: ‘struct appres_struct’ has no member named ‘shift_lock’
xvkbd.c:2804: error: ‘struct appres_struct’ has no member named ‘altgr_lock’
xvkbd.c:2805: error: ‘struct appres_struct’ has no member named ‘modifiers_lock’
xvkbd.c: In function ‘PopupFunctionKeyEditor’:
xvkbd.c:2816: error: ‘Widget’ undeclared (first use in this function)
xvkbd.c:2816: error: expected ‘;’ before ‘form’
xvkbd.c:2821: error: ‘edit_fkey_panel’ undeclared (first use in this function)
xvkbd.c:2821: error: ‘None’ undeclared (first use in this function)
xvkbd.c:2822: error: ‘transientShellWidgetClass’ undeclared (first use in this function)
xvkbd.c:2823: error: ‘toplevel’ undeclared (first use in this function)
xvkbd.c:2824: error: ‘form’ undeclared (first use in this function)
xvkbd.c:2824: error: ‘formWidgetClass’ undeclared (first use in this function)
xvkbd.c:2826: error: ‘form2’ undeclared (first use in this function)
xvkbd.c:2827: error: ‘labelWidgetClass’ undeclared (first use in this function)
xvkbd.c:2828: error: ‘fkey_menu_button’ undeclared (first use in this function)
xvkbd.c:2828: error: ‘menuButtonWidgetClass’ undeclared (first use in this function)
xvkbd.c:2830: error: ‘menu’ undeclared (first use in this function)
xvkbd.c:2830: error: ‘simpleMenuWidgetClass’ undeclared (first use in this function)
xvkbd.c:2832: error: ‘struct appres_struct’ has no member named ‘editable_function_keys’
xvkbd.c:2837: warning: assignment makes pointer from integer without a cast
xvkbd.c:2838: error: ‘menu_entry’ undeclared (first use in this function)
xvkbd.c:2838: error: ‘smeBSBObjectClass’ undeclared (first use in this function)
xvkbd.c:2839: error: ‘XtNcallback’ undeclared (first use in this function)
xvkbd.c:2839: error: ‘XtCallbackProc’ undeclared (first use in this function)
xvkbd.c:2839: error: expected ‘)’ before ‘FKeyMenuSelected’
xvkbd.c:2844: error: ‘fkey_value_menu_button’ undeclared (first use in this function)
xvkbd.c:2848: error: expected ‘)’ before ‘FKeyValueMenuSelected’
xvkbd.c:2851: error: expected ‘)’ before ‘FKeyValueMenuSelected’
xvkbd.c:2856: error: ‘fkey_value_entry’ undeclared (first use in this function)
xvkbd.c:2856: error: ‘asciiTextWidgetClass’ undeclared (first use in this function)
xvkbd.c:2857: error: ‘XtNuseStringInPlace’ undeclared (first use in this function)
xvkbd.c:2857: error: ‘True’ undeclared (first use in this function)
xvkbd.c:2858: error: ‘XtNeditType’ undeclared (first use in this function)
xvkbd.c:2858: error: ‘XawtextEdit’ undeclared (first use in this function)
xvkbd.c:2859: error: ‘XtNstring’ undeclared (first use in this function)
xvkbd.c:2860: error: ‘XtNlength’ undeclared (first use in this function)
xvkbd.c:2863: error: ‘button’ undeclared (first use in this function)
xvkbd.c:2863: error: ‘commandWidgetClass’ undeclared (first use in this function)
xvkbd.c:2864: error: expected ‘)’ before ‘SaveFunctionKey’
xvkbd.c:2867: error: expected ‘)’ before ‘CloseFunctionKeyPanel’
xvkbd.c:2870: error: ‘dpy’ undeclared (first use in this function)
xvkbd.c:2870: error: ‘wm_delete_window’ undeclared (first use in this function)
xvkbd.c:2877: error: ‘XtGrabNone’ undeclared (first use in this function)
xvkbd.c: At top level:
xvkbd.c:2884: error: expected declaration specifiers or ‘...’ before ‘Boolean’
xvkbd.c: In function ‘FindFunctionKeyValue’:
xvkbd.c:2892: error: ‘shiftable’ undeclared (first use in this function)
xvkbd.c:2895: error: ‘ControlMask’ undeclared (first use in this function)
xvkbd.c:2896: error: ‘ShiftMask’ undeclared (first use in this function)
xvkbd.c: At top level:
xvkbd.c:2913: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘balloon_panel_open’
xvkbd.c:2914: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘balloon_panel’
xvkbd.c:2916: error: expected ‘)’ before ‘w’
xvkbd.c:2949: error: expected ‘)’ before ‘w’
xvkbd.c:2960: error: expected ‘)’ before ‘w’
xvkbd.c:2980: error: expected ‘)’ before ‘w’
xvkbd.c: In function ‘main’:
xvkbd.c:3012: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘actions’
xvkbd.c:3012: error: ‘actions’ undeclared (first use in this function)
xvkbd.c:3012: error: expected expression before ‘]’ token
xvkbd.c:3023: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fallback_resources’
xvkbd.c:3023: error: ‘fallback_resources’ undeclared (first use in this function)
xvkbd.c:3023: error: expected expression before ‘]’ token
xvkbd.c:3029: error: ‘Window’ undeclared (first use in this function)
xvkbd.c:3029: error: expected ‘;’ before ‘child’
xvkbd.c:3043: error: ‘toplevel’ undeclared (first use in this function)
xvkbd.c:3044: error: ‘options’ undeclared (first use in this function)
xvkbd.c:3046: error: ‘dpy’ undeclared (first use in this function)
xvkbd.c:3047: error: ‘app_con’ undeclared (first use in this function)
xvkbd.c:3050: error: ‘target_dpy’ undeclared (first use in this function)
xvkbd.c:3057: error: ‘application_resources’ undeclared (first use in this function)
xvkbd.c:3059: error: ‘struct appres_struct’ has no member named ‘compact’
xvkbd.c:3060: error: ‘struct appres_struct’ has no member named ‘keypad’
xvkbd.c:3060: error: ‘FALSE’ undeclared (first use in this function)
xvkbd.c:3061: error: ‘struct appres_struct’ has no member named ‘function_key’
xvkbd.c:3063: error: ‘struct appres_struct’ has no member named ‘keypad_only’
xvkbd.c:3063: error: ‘struct appres_struct’ has no member named ‘keypad’
xvkbd.c:3064: error: ‘struct appres_struct’ has no member named ‘keypad_only’
xvkbd.c:3068: error: ‘struct appres_struct’ has no member named ‘no_sync’
xvkbd.c:3070: error: ‘MyErrorHandler’ undeclared (first use in this function)
xvkbd.c:3073: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3074: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3075: error: ‘focused_window’ undeclared (first use in this function)
xvkbd.c:3076: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3077: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3079: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3080: error: ‘None’ undeclared (first use in this function)
xvkbd.c:3081: error: ‘struct appres_struct’ has no member named ‘window’
xvkbd.c:3086: error: ‘focused_subwindow’ undeclared (first use in this function)
xvkbd.c:3089: error: ‘struct appres_struct’ has no member named ‘auto_add_keysym’
xvkbd.c:3089: error: ‘XK_Mode_switch’ undeclared (first use in this function)
xvkbd.c:3091: error: ‘struct appres_struct’ has no member named ‘text’
xvkbd.c:3091: error: ‘struct appres_struct’ has no member named ‘file’
xvkbd.c:3092: error: ‘struct appres_struct’ has no member named ‘keypad_keysym’
xvkbd.c:3092: error: ‘TRUE’ undeclared (first use in this function)
xvkbd.c:3094: error: ‘struct appres_struct’ has no member named ‘list_widgets’
xvkbd.c:3094: error: ‘struct appres_struct’ has no member named ‘widget’
xvkbd.c:3095: error: ‘XtNwidth’ undeclared (first use in this function)
xvkbd.c:3095: error: ‘XtNheight’ undeclared (first use in this function)
xvkbd.c:3097: error: ‘child’ undeclared (first use in this function)
xvkbd.c:3097: error: ‘struct appres_struct’ has no member named ‘widget’
xvkbd.c:3100: error: ‘struct appres_struct’ has no member named ‘text’
xvkbd.c:3101: error: ‘struct appres_struct’ has no member named ‘text’
xvkbd.c:3103: error: ‘struct appres_struct’ has no member named ‘file’
xvkbd.c:3108: error: ‘struct appres_struct’ has no member named ‘keys_normal’
xvkbd.c:3109: error: ‘struct appres_struct’ has no member named ‘keys_normal’
xvkbd.c:3110: error: ‘struct appres_struct’ has no member named ‘keys_shift’
xvkbd.c:3111: error: ‘struct appres_struct’ has no member named ‘keys_shift’
xvkbd.c:3112: error: ‘struct appres_struct’ has no member named ‘keys_altgr’
xvkbd.c:3113: error: ‘struct appres_struct’ has no member named ‘keys_altgr’
xvkbd.c:3114: error: ‘struct appres_struct’ has no member named ‘keys_shift_altgr’
xvkbd.c:3115: error: ‘struct appres_struct’ has no member named ‘keys_shift_altgr’
xvkbd.c:3117: error: ‘struct appres_struct’ has no member named ‘key_labels’
xvkbd.c:3118: error: ‘struct appres_struct’ has no member named ‘key_labels’
xvkbd.c:3119: error: ‘struct appres_struct’ has no member named ‘normal_key_labels’
xvkbd.c:3120: error: ‘struct appres_struct’ has no member named ‘normal_key_labels’
xvkbd.c:3121: error: ‘struct appres_struct’ has no member named ‘shift_key_labels’
xvkbd.c:3122: error: ‘struct appres_struct’ has no member named ‘shift_key_labels’
xvkbd.c:3123: error: ‘struct appres_struct’ has no member named ‘altgr_key_labels’
xvkbd.c:3124: error: ‘struct appres_struct’ has no member named ‘altgr_key_labels’
xvkbd.c:3125: error: ‘struct appres_struct’ has no member named ‘shift_altgr_key_labels’
xvkbd.c:3126: error: ‘struct appres_struct’ has no member named ‘shift_altgr_key_labels’
xvkbd.c:3131: error: ‘struct appres_struct’ has no member named ‘list_widgets’
xvkbd.c:3131: error: ‘struct appres_struct’ has no member named ‘widget’
xvkbd.c:3132: error: ‘struct appres_struct’ has no member named ‘widget’
xvkbd.c:3136: error: ‘main_menu’ undeclared (first use in this function)
xvkbd.c:3137: error: ‘struct appres_struct’ has no member named ‘dict_file’
xvkbd.c:3139: error: ‘struct appres_struct’ has no member named ‘customizations’
xvkbd.c:3143: error: ‘struct appres_struct’ has no member named ‘nonexitable’
xvkbd.c:3145: error: ‘struct appres_struct’ has no member named ‘secure’
xvkbd.c:3153: error: ‘struct appres_struct’ has no member named ‘xtest’
xvkbd.c:3158: error: ‘struct appres_struct’ has no member named ‘xtest’
xvkbd.c:3167: error: ‘struct appres_struct’ has no member named ‘debug’
xvkbd.c: In function ‘setlocale’:
xvkbd.c:3201: error: ‘LC_ALL’ undeclared (first use in this function)
make: *** [xvkbd.o] Error 1
```


am I missing something here?

---

### Post by jpkotta on 2007-10-14
Edit: Sorry, this thing appears to be imake-based.  There will be no configure step.  But the general rules still apply.

Did you install the -dev packages?
[CODE]sudo aptitude install xorg-dev libx11-dev[CODE]

The general algorithm is:
Run ./configure
See what it complains about
Look in your favorite package manager for a package that will probably provide it.  It will end in -dev and usually start with lib.
Install
Repeat until ./configure works.

---

### Post by jpkotta on 2007-10-14
You do know that xvkbd is in the repos, right?

---

### Post by yosef on 2007-10-15
Yeah, I know its iin the repos... but I need too compile 2.8 with a patch for my tablet.

---

### Post by yosef on 2007-10-15
Thank you for your help, it finally worked!  And now I have my virtual keyboard working well (more or less) on my fujitsu stylistic lt p600.  No more w2k!!:guitar:

---

