---
title: "vnc text editor segfault"
date: 2008-07-04
forum: General Help
---

### Post by jediborger on 2008-07-04
Just for a little background I have set up a cut down ubuntu headless server using openbox so I can work with some graphical only applications. So I ssh in, run x11vnc and then vnc into the server to work with them. There seems to be one problem though, any graphical program that takes text input segfaults. By this I mean leafpad, geany and even obmenu. I know these programs are compiled properly but after I type something in a text input they all return "Segmentation Fault." Also after a few times x11vnc quits with the following error:
```
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  132 (XTEST)
  Minor opcode of failed request:  2 (X_XTestFakeInput)
  Value in failed request:  0x0
  Serial number of failed request:  24289
  Current serial number in output stream:  24290

```
So I have a feeling extra keycodes are being passed from my local keyboard through vnc and causing the programs to crash. But strangely if I use nano or vim in an xterm window, I have no issues. This seems to be limited to graphical(mostly gtk) apps. Any ideas or suggestions as to avoid this nuisance?

---

### Post by krunge on 2008-07-04
Run x11vnc like this:
```
x11vnc -nopw -dk -o log.txt (plus anything else you need)
```
then connect viewer and make it (x11vnc) fail via typing as you described.  Then post all of log.txt here.

---

### Post by jediborger on 2008-07-06
Thanks for the help. Here's the log file since it's too big to attach.
```
06/07/2008 20:48:22 x11vnc version: 0.9.3 lastmod: 2007-09-30
06/07/2008 20:48:22 Using X display :0
06/07/2008 20:48:22 
06/07/2008 20:48:22 ------------------ USEFUL INFORMATION ------------------
06/07/2008 20:48:22 X DAMAGE available on display, using it for polling hints.
06/07/2008 20:48:22   To disable this behavior use: '-noxdamage'
06/07/2008 20:48:22 
06/07/2008 20:48:22 Wireframing: -wireframe mode is in effect for window moves.
06/07/2008 20:48:22   If this yields undesired behavior (poor response, painting
06/07/2008 20:48:22   errors, etc) it may be disabled:
06/07/2008 20:48:22    - use '-nowf' to disable wireframing completely.
06/07/2008 20:48:22    - use '-nowcr' to disable the Copy Rectangle after the
06/07/2008 20:48:22      moved window is released in the new position.
06/07/2008 20:48:22   Also see the -help entry for tuning parameters.
06/07/2008 20:48:22   You can press 3 Alt_L's (Left "Alt" key) in a row to 
06/07/2008 20:48:22   repaint the screen, also see the -fixscreen option for
06/07/2008 20:48:22   periodic repaints.
06/07/2008 20:48:22 
06/07/2008 20:48:22 XFIXES available on display, resetting cursor mode
06/07/2008 20:48:22   to: '-cursor most'.
06/07/2008 20:48:22   to disable this behavior use: '-cursor arrow'
06/07/2008 20:48:22   or '-noxfixes'.
06/07/2008 20:48:22 using XFIXES for cursor drawing.
06/07/2008 20:48:22 GrabServer control via XTEST.
06/07/2008 20:48:22 
06/07/2008 20:48:22 Scroll Detection: -scrollcopyrect mode is in effect to
06/07/2008 20:48:22   use RECORD extension to try to detect scrolling windows
06/07/2008 20:48:22   (induced by either user keystroke or mouse input).
06/07/2008 20:48:22   If this yields undesired behavior (poor response, painting
06/07/2008 20:48:22   errors, etc) it may be disabled via: '-noscr'
06/07/2008 20:48:22   Also see the -help entry for tuning parameters.
06/07/2008 20:48:22   You can press 3 Alt_L's (Left "Alt" key) in a row to 
06/07/2008 20:48:22   repaint the screen, also see the -fixscreen option for
06/07/2008 20:48:22   periodic repaints.
06/07/2008 20:48:22 
06/07/2008 20:48:22 XKEYBOARD: "must have" keysyms better accounted for
06/07/2008 20:48:22 under -noxkb mode: not switching to -xkb mode:
06/07/2008 20:48:22    xkb  noxkb   Keysym  ("X" means present)
06/07/2008 20:48:22    ---  -----   -----------------------------
06/07/2008 20:48:22                 0x21  exclam
06/07/2008 20:48:22                 0x40  at
06/07/2008 20:48:22                 0x23  numbersign
06/07/2008 20:48:22                 0x24  dollar
06/07/2008 20:48:22                 0x25  percent
06/07/2008 20:48:22                 0x26  ampersand
06/07/2008 20:48:22                 0x2a  asterisk
06/07/2008 20:48:22                 0x28  parenleft
06/07/2008 20:48:22                 0x29  parenright
06/07/2008 20:48:22                 0x5f  underscore
06/07/2008 20:48:22                 0x2b  plus
06/07/2008 20:48:22                 0x2d  minus
06/07/2008 20:48:22                 0x3d  equal
06/07/2008 20:48:22                 0x5b  bracketleft
06/07/2008 20:48:22                 0x5d  bracketright
06/07/2008 20:48:22                 0x7b  braceleft
06/07/2008 20:48:22                 0x7d  braceright
06/07/2008 20:48:22                 0x7c  bar
06/07/2008 20:48:22                 0x5c  backslash
06/07/2008 20:48:22                 0x3b  semicolon
06/07/2008 20:48:22                 0x3a  colon
06/07/2008 20:48:22                 0x22  quotedbl
06/07/2008 20:48:22                 0x2c  comma
06/07/2008 20:48:22                 0x2e  period
06/07/2008 20:48:22                 0x3c  less
06/07/2008 20:48:22                 0x3e  greater
06/07/2008 20:48:22                 0x2f  slash
06/07/2008 20:48:22                 0x3f  question
06/07/2008 20:48:22 
06/07/2008 20:48:22   If some keys still cannot be typed, try using -xkb.
06/07/2008 20:48:22   Also, remember "-remap DEAD" for accenting characters.
06/07/2008 20:48:22 X FBPM extension not supported.
Xlib:  extension "DPMS" missing on display ":0.0".
06/07/2008 20:48:22 X display is not capable of DPMS.
06/07/2008 20:48:22 --------------------------------------------------------
06/07/2008 20:48:22 
06/07/2008 20:48:22 Default visual ID: 0x23
06/07/2008 20:48:22 Read initial data from X display into framebuffer.
06/07/2008 20:48:22 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/4096
06/07/2008 20:48:22 
06/07/2008 20:48:22 X display :0.0 is 32bpp depth=24 true color
06/07/2008 20:48:22 
06/07/2008 20:48:22 Autoprobing TCP port 
06/07/2008 20:48:22 Autoprobing selected port 5900
06/07/2008 20:48:22 fb read rate: 326 MB/sec
06/07/2008 20:48:22 initialize_modtweak: keycode -> keysyms mapping info:
  008  null               null               null               null               
  009  null               null               null               null               
  010  null               null               null               null               
  011  null               null               null               null               
  012  null               null               null               null               
  013  null               null               null               null               
  014  null               null               null               null               
  015  null               null               null               null               
  016  null               null               null               null               
  017  null               null               null               null               
  018  null               null               null               null               
  019  null               null               null               null               
  020  null               null               null               null               
  021  null               null               null               null               
  022  null               null               null               null               
  023  null               null               null               null               
  024  null               null               null               null               
  025  null               null               null               null               
  026  null               null               null               null               
  027  null               null               null               null               
  028  null               null               null               null               
  029  null               null               null               null               
  030  null               null               null               null               
  031  null               null               null               null               
  032  null               null               null               null               
  033  null               null               null               null               
  034  null               null               null               null               
  035  null               null               null               null               
  036  null               null               null               null               
  037  null               null               null               null               
  038  null               null               null               null               
  039  null               null               null               null               
  040  null               null               null               null               
  041  null               null               null               null               
  042  null               null               null               null               
  043  null               null               null               null               
  044  null               null               null               null               
  045  null               null               null               null               
  046  null               null               null               null               
  047  null               null               null               null               
  048  null               null               null               null               
  049  null               null               null               null               
  050  null               null               null               null               
  051  null               null               null               null               
  052  null               null               null               null               
  053  null               null               null               null               
  054  null               null               null               null               
  055  null               null               null               null               
  056  null               null               null               null               
  057  null               null               null               null               
  058  null               null               null               null               
  059  null               null               null               null               
  060  null               null               null               null               
  061  null               null               null               null               
  062  null               null               null               null               
  063  null               null               null               null               
  064  null               null               null               null               
  065  null               null               null               null               
  066  null               null               null               null               
  067  null               null               null               null               
  068  null               null               null               null               
  069  null               null               null               null               
  070  null               null               null               null               
  071  null               null               null               null               
  072  null               null               null               null               
  073  null               null               null               null               
  074  null               null               null               null               
  075  null               null               null               null               
  076  null               null               null               null               
  077  null               null               null               null               
  078  null               null               null               null               
  079  null               null               null               null               
  080  null               null               null               null               
  081  null               null               null               null               
  082  null               null               null               null               
  083  null               null               null               null               
  084  null               null               null               null               
  085  null               null               null               null               
  086  null               null               null               null               
  087  null               null               null               null               
  088  null               null               null               null               
  089  null               null               null               null               
  090  null               null               null               null               
  091  null               null               null               null               
  092  null               null               null               null               
  093  null               null               null               null               
  094  null               null               null               null               
  095  null               null               null               null               
  096  null               null               null               null               
  097  null               null               null               null               
  098  null               null               null               null               
  099  null               null               null               null               
  100  null               null               null               null               
  101  null               null               null               null               
  102  null               null               null               null               
  103  null               null               null               null               
  104  null               null               null               null               
  105  null               null               null               null               
  106  null               null               null               null               
  107  null               null               null               null               
  108  null               null               null               null               
  109  null               null               null               null               
  110  null               null               null               null               
  111  null               null               null               null               
  112  null               null               null               null               
  113  null               null               null               null               
  114  null               null               null               null               
  115  null               null               null               null               
  116  null               null               null               null               
  117  null               null               null               null               
  118  null               null               null               null               
  119  null               null               null               null               
  120  null               null               null               null               
  121  null               null               null               null               
  122  null               null               null               null               
  123  null               null               null               null               
  124  null               null               null               null               
  125  null               null               null               null               
  126  null               null               null               null               
  127  null               null               null               null               
  128  null               null               null               null               
  129  null               null               null               null               
  130  null               null               null               null               
  131  null               null               null               null               
  132  null               null               null               null               
  133  null               null               null               null               
  134  null               null               null               null               
  135  null               null               null               null               
  136  null               null               null               null               
  137  null               null               null               null               
  138  null               null               null               null               
  139  null               null               null               null               
  140  null               null               null               null               
  141  null               null               null               null               
  142  null               null               null               null               
  143  null               null               null               null               
  144  null               null               null               null               
  145  null               null               null               null               
  146  null               null               null               null               
  147  null               null               null               null               
  148  null               null               null               null               
  149  null               null               null               null               
  150  null               null               null               null               
  151  null               null               null               null               
  152  null               null               null               null               
  153  null               null               null               null               
  154  null               null               null               null               
  155  null               null               null               null               
  156  null               null               null               null               
  157  null               null               null               null               
  158  null               null               null               null               
  159  null               null               null               null               
  160  null               null               null               null               
  161  null               null               null               null               
  162  null               null               null               null               
  163  null               null               null               null               
  164  null               null               null               null               
  165  null               null               null               null               
  166  null               null               null               null               
  167  null               null               null               null               
  168  null               null               null               null               
  169  null               null               null               null               
  170  null               null               null               null               
  171  null               null               null               null               
  172  null               null               null               null               
  173  null               null               null               null               
  174  null               null               null               null               
  175  null               null               null               null               
  176  null               null               null               null               
  177  null               null               null               null               
  178  null               null               null               null               
  179  null               null               null               null               
  180  null               null               null               null               
  181  null               null               null               null               
  182  null               null               null               null               
  183  null               null               null               null               
  184  null               null               null               null               
  185  null               null               null               null               
  186  null               null               null               null               
  187  null               null               null               null               
  188  null               null               null               null               
  189  null               null               null               null               
  190  null               null               null               null               
  191  null               null               null               null               
  192  null               null               null               null               
  193  null               null               null               null               
  194  null               null               null               null               
  195  null               null               null               null               
  196  null               null               null               null               
  197  null               null               null               null               
  198  null               null               null               null               
  199  null               null               null               null               
  200  null               null               null               null               
  201  null               null               null               null               
  202  null               null               null               null               
  203  null               null               null               null               
  204  null               null               null               null               
  205  null               null               null               null               
  206  null               null               null               null               
  207  null               null               null               null               
  208  null               null               null               null               
  209  null               null               null               null               
  210  null               null               null               null               
  211  null               null               null               null               
  212  null               null               null               null               
  213  null               null               null               null               
  214  null               null               null               null               
  215  null               null               null               null               
  216  null               null               null               null               
  217  null               null               null               null               
  218  null               null               null               null               
  219  null               null               null               null               
  220  null               null               null               null               
  221  null               null               null               null               
  222  null               null               null               null               
  223  null               null               null               null               
  224  null               null               null               null               
  225  null               null               null               null               
  226  null               null               null               null               
  227  null               null               null               null               
  228  null               null               null               null               
  229  null               null               null               null               
  230  null               null               null               null               
  231  null               null               null               null               
  232  null               null               null               null               
  233  null               null               null               null               
  234  null               null               null               null               
  235  null               null               null               null               
  236  null               null               null               null               
  237  null               null               null               null               
  238  null               null               null               null               
  239  null               null               null               null               
  240  null               null               null               null               
  241  null               null               null               null               
  242  null               null               null               null               
  243  null               null               null               null               
  244  null               null               null               null               
  245  null               null               null               null               
  246  null               null               null               null               
  247  null               null               null               null               
  248  null               null               null               null               
  249  null               null               null               null               
  250  null               null               null               null               
  251  null               null               null               null               
  252  null               null               null               null               
  253  null               null               null               null               
  254  null               null               null               null               
  255  null               null               null               null               
06/07/2008 20:48:22 screen setup finished.
06/07/2008 20:48:22 

The VNC desktop is:      home-server:0

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

more info: http://www.karlrunge.com/x11vnc/#faq-client-caching

06/07/2008 20:48:42 Got connection from client 192.168.1.45
06/07/2008 20:48:42   other clients:
06/07/2008 20:48:42 Disabled X server key autorepeat.
06/07/2008 20:48:42   to force back on run: 'xset r on' (3 times)
06/07/2008 20:48:42 created xdamage object: 0x400024
06/07/2008 20:48:42 Client Protocol Version 3.8
06/07/2008 20:48:42 Protocol version sent 3.8, using 3.8
06/07/2008 20:48:42 rfbProcessClientSecurityType: executing handler for type 1
06/07/2008 20:48:42 rfbProcessClientSecurityType: returning securityResult for client rfb version >= 3.8
06/07/2008 20:48:42 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0xFFFFFEFE)
06/07/2008 20:48:42 Enabling NewFBSize protocol extension for client 192.168.1.45
06/07/2008 20:48:42 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0x574D5669)
06/07/2008 20:48:42 Enabling full-color cursor updates for client 192.168.1.45
06/07/2008 20:48:42 Enabling X-style cursor updates for client 192.168.1.45
06/07/2008 20:48:42 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0xFFFFFEFF)
06/07/2008 20:48:42 Using tight encoding for client 192.168.1.45
06/07/2008 20:49:20 # keyboard(down, 0x6c "l") uip=0  57.4999
06/07/2008 20:49:20 modifier_tweak_keyboard: down keysym=0x6c
06/07/2008 20:49:20 tweak_mod: Skip:  down=1 index=-1
06/07/2008 20:49:20 added missing keysym to X display: 009 0x6c "l"
06/07/2008 20:49:20 modifier_tweak_keyboard: KeySym 0x6c "l" -> KeyCode 0x9
06/07/2008 20:49:20 XTestFakeKeyEvent(dpy, keycode=0x9 "null", down)
06/07/2008 20:49:20 calling XTestFakeKeyEvent(9, 1)  57.5025
06/07/2008 20:49:20 tweak_mod: Skip:  down=0 index=-1
06/07/2008 20:49:20 # keyboard(up, 0x6c "l") uip=0  57.5759
06/07/2008 20:49:20 modifier_tweak_keyboard: up keysym=0x6c
06/07/2008 20:49:20 modifier_tweak_keyboard: KeySym 0x6c "l" -> KeyCode 0x9
06/07/2008 20:49:20 XTestFakeKeyEvent(dpy, keycode=0x9 "l", up)
06/07/2008 20:49:20 calling XTestFakeKeyEvent(9, 0)  57.5763
06/07/2008 20:49:20 # keyboard(down, 0x65 "e") uip=0  57.8327
06/07/2008 20:49:20 modifier_tweak_keyboard: down keysym=0x65
06/07/2008 20:49:20 tweak_mod: Skip:  down=1 index=-1
06/07/2008 20:49:20 added missing keysym to X display: 010 0x65 "e"
06/07/2008 20:49:20 modifier_tweak_keyboard: KeySym 0x65 "e" -> KeyCode 0xa
06/07/2008 20:49:20 XTestFakeKeyEvent(dpy, keycode=0xa "null", down)
06/07/2008 20:49:20 calling XTestFakeKeyEvent(10, 1)  57.8335
06/07/2008 20:49:20 tweak_mod: Skip:  down=0 index=-1
06/07/2008 20:49:20 # keyboard(up, 0x65 "e") uip=0  57.9783
06/07/2008 20:49:20 modifier_tweak_keyboard: up keysym=0x65
06/07/2008 20:49:20 modifier_tweak_keyboard: KeySym 0x65 "e" -> KeyCode 0xa
06/07/2008 20:49:20 XTestFakeKeyEvent(dpy, keycode=0xa "e", up)
06/07/2008 20:49:20 calling XTestFakeKeyEvent(10, 0)  57.9787
06/07/2008 20:49:20 # keyboard(down, 0x61 "a") uip=0  57.9798
06/07/2008 20:49:20 modifier_tweak_keyboard: down keysym=0x61
06/07/2008 20:49:20 tweak_mod: Skip:  down=1 index=-1
06/07/2008 20:49:20 added missing keysym to X display: 011 0x61 "a"
06/07/2008 20:49:20 modifier_tweak_keyboard: KeySym 0x61 "a" -> KeyCode 0xb
06/07/2008 20:49:20 XTestFakeKeyEvent(dpy, keycode=0xb "null", down)
06/07/2008 20:49:20 calling XTestFakeKeyEvent(11, 1)  57.9805
06/07/2008 20:49:20 tweak_mod: Skip:  down=0 index=-1
06/07/2008 20:49:20 # keyboard(up, 0x61 "a") uip=0  58.0879
06/07/2008 20:49:20 modifier_tweak_keyboard: up keysym=0x61
06/07/2008 20:49:20 modifier_tweak_keyboard: KeySym 0x61 "a" -> KeyCode 0xb
06/07/2008 20:49:20 XTestFakeKeyEvent(dpy, keycode=0xb "a", up)
06/07/2008 20:49:20 calling XTestFakeKeyEvent(11, 0)  58.0883
06/07/2008 20:49:20 # keyboard(down, 0x66 "f") uip=0  58.1098
06/07/2008 20:49:20 modifier_tweak_keyboard: down keysym=0x66
06/07/2008 20:49:20 tweak_mod: Skip:  down=1 index=-1
06/07/2008 20:49:20 added missing keysym to X display: 012 0x66 "f"
06/07/2008 20:49:20 modifier_tweak_keyboard: KeySym 0x66 "f" -> KeyCode 0xc
06/07/2008 20:49:20 XTestFakeKeyEvent(dpy, keycode=0xc "f", down)
06/07/2008 20:49:20 calling XTestFakeKeyEvent(12, 1)  58.1124
06/07/2008 20:49:20 tweak_mod: Skip:  down=0 index=-1
06/07/2008 20:49:20 # keyboard(up, 0x66 "f") uip=0  58.2157
06/07/2008 20:49:20 modifier_tweak_keyboard: up keysym=0x66
06/07/2008 20:49:20 modifier_tweak_keyboard: KeySym 0x66 "f" -> KeyCode 0xc
06/07/2008 20:49:20 XTestFakeKeyEvent(dpy, keycode=0xc "f", up)
06/07/2008 20:49:20 calling XTestFakeKeyEvent(12, 0)  58.2159
06/07/2008 20:49:21 # keyboard(down, 0x70 "p") uip=0  58.2823
06/07/2008 20:49:21 modifier_tweak_keyboard: down keysym=0x70
06/07/2008 20:49:21 tweak_mod: Skip:  down=1 index=-1
06/07/2008 20:49:21 added missing keysym to X display: 013 0x70 "p"
06/07/2008 20:49:21 modifier_tweak_keyboard: KeySym 0x70 "p" -> KeyCode 0xd
06/07/2008 20:49:21 XTestFakeKeyEvent(dpy, keycode=0xd "p", down)
06/07/2008 20:49:21 calling XTestFakeKeyEvent(13, 1)  58.2849
06/07/2008 20:49:21 tweak_mod: Skip:  down=0 index=-1
06/07/2008 20:49:21 # keyboard(up, 0x70 "p") uip=0  58.3919
06/07/2008 20:49:21 modifier_tweak_keyboard: up keysym=0x70
06/07/2008 20:49:21 modifier_tweak_keyboard: KeySym 0x70 "p" -> KeyCode 0xd
06/07/2008 20:49:21 XTestFakeKeyEvent(dpy, keycode=0xd "p", up)
06/07/2008 20:49:21 calling XTestFakeKeyEvent(13, 0)  58.3921
06/07/2008 20:49:21 # keyboard(down, 0x61 "a") uip=0  58.4094
06/07/2008 20:49:21 modifier_tweak_keyboard: down keysym=0x61
06/07/2008 20:49:21 tweak_mod: Skip:  down=1 index=-1
06/07/2008 20:49:21 modifier_tweak_keyboard: KeySym 0x61 "a" -> KeyCode 0xb
06/07/2008 20:49:21 XTestFakeKeyEvent(dpy, keycode=0xb "a", down)
06/07/2008 20:49:21 calling XTestFakeKeyEvent(11, 1)  58.4099
06/07/2008 20:49:21 tweak_mod: Skip:  down=0 index=-1
06/07/2008 20:49:21 # keyboard(up, 0x61 "a") uip=0  58.5159
06/07/2008 20:49:21 modifier_tweak_keyboard: up keysym=0x61
06/07/2008 20:49:21 modifier_tweak_keyboard: KeySym 0x61 "a" -> KeyCode 0xb
06/07/2008 20:49:21 XTestFakeKeyEvent(dpy, keycode=0xb "a", up)
06/07/2008 20:49:21 calling XTestFakeKeyEvent(11, 0)  58.5161
06/07/2008 20:49:21 # keyboard(down, 0x64 "d") uip=0  58.5999
06/07/2008 20:49:21 modifier_tweak_keyboard: down keysym=0x64
06/07/2008 20:49:21 tweak_mod: Skip:  down=1 index=-1
06/07/2008 20:49:21 added missing keysym to X display: 014 0x64 "d"
06/07/2008 20:49:21 modifier_tweak_keyboard: KeySym 0x64 "d" -> KeyCode 0xe
06/07/2008 20:49:21 XTestFakeKeyEvent(dpy, keycode=0xe "d", down)
06/07/2008 20:49:21 calling XTestFakeKeyEvent(14, 1)  58.6025
06/07/2008 20:49:21 tweak_mod: Skip:  down=0 index=-1
06/07/2008 20:49:21 # keyboard(up, 0x64 "d") uip=0  58.6650
06/07/2008 20:49:21 modifier_tweak_keyboard: up keysym=0x64
06/07/2008 20:49:21 modifier_tweak_keyboard: KeySym 0x64 "d" -> KeyCode 0xe
06/07/2008 20:49:21 XTestFakeKeyEvent(dpy, keycode=0xe "d", up)
06/07/2008 20:49:21 calling XTestFakeKeyEvent(14, 0)  58.6653
06/07/2008 20:49:21 # keyboard(down, 0xff0d "Return") uip=0  58.7744
06/07/2008 20:49:21 modifier_tweak_keyboard: down keysym=0xff0d
06/07/2008 20:49:21 added missing keysym to X display: 015 0xff0d "Return"
06/07/2008 20:49:21 modifier_tweak_keyboard: KeySym 0xff0d "Return" -> KeyCode 0xf
06/07/2008 20:49:21 XTestFakeKeyEvent(dpy, keycode=0xf "Return", down)
06/07/2008 20:49:21 calling XTestFakeKeyEvent(15, 1)  58.7770
06/07/2008 20:49:21 # keyboard(up, 0xff0d "Return") uip=0  58.8520
06/07/2008 20:49:21 modifier_tweak_keyboard: up keysym=0xff0d
06/07/2008 20:49:21 modifier_tweak_keyboard: KeySym 0xff0d "Return" -> KeyCode 0xf
06/07/2008 20:49:21 XTestFakeKeyEvent(dpy, keycode=0xf "Return", up)
06/07/2008 20:49:21 calling XTestFakeKeyEvent(15, 0)  58.8522
06/07/2008 20:49:22 initialize_modtweak: keycode -> keysyms mapping info:
  008  null               null               null               null               
  009  l                  l                  l                  l                  
  010  e                  e                  e                  e                  
  011  a                  a                  a                  a                  
  012  f                  f                  f                  f                  
  013  p                  p                  p                  p                  
  014  d                  d                  d                  d                  
  015  Return             Return             Return             Return             
  016  null               null               null               null               
  017  null               null               null               null               
  018  null               null               null               null               
  019  null               null               null               null               
  020  null               null               null               null               
  021  null               null               null               null               
  022  null               null               null               null               
  023  null               null               null               null               
  024  null               null               null               null               
  025  null               null               null               null               
  026  null               null               null               null               
  027  null               null               null               null               
  028  null               null               null               null               
  029  null               null               null               null               
  030  null               null               null               null               
  031  null               null               null               null               
  032  null               null               null               null               
  033  null               null               null               null               
  034  null               null               null               null               
  035  null               null               null               null               
  036  null               null               null               null               
  037  null               null               null               null               
  038  null               null               null               null               
  039  null               null               null               null               
  040  null               null               null               null               
  041  null               null               null               null               
  042  null               null               null               null               
  043  null               null               null               null               
  044  null               null               null               null               
  045  null               null               null               null               
  046  null               null               null               null               
  047  null               null               null               null               
  048  null               null               null               null               
  049  null               null               null               null               
  050  null               null               null               null               
  051  null               null               null               null               
  052  null               null               null               null               
  053  null               null               null               null               
  054  null               null               null               null               
  055  null               null               null               null               
  056  null               null               null               null               
  057  null               null               null               null               
  058  null               null               null               null               
  059  null               null               null               null               
  060  null               null               null               null               
  061  null               null               null               null               
  062  null               null               null               null               
  063  null               null               null               null               
  064  null               null               null               null               
  065  null               null               null               null               
  066  null               null               null               null               
  067  null               null               null               null               
  068  null               null               null               null               
  069  null               null               null               null               
  070  null               null               null               null               
  071  null               null               null               null               
  072  null               null               null               null               
  073  null               null               null               null               
  074  null               null               null               null               
  075  null               null               null               null               
  076  null               null               null               null               
  077  null               null               null               null               
  078  null               null               null               null               
  079  null               null               null               null               
  080  null               null               null               null               
  081  null               null               null               null               
  082  null               null               null               null               
  083  null               null               null               null               
  084  null               null               null               null               
  085  null               null               null               null               
  086  null               null               null               null               
  087  null               null               null               null               
  088  null               null               null               null               
  089  null               null               null               null               
  090  null               null               null               null               
  091  null               null               null               null               
  092  null               null               null               null               
  093  null               null               null               null               
  094  null               null               null               null               
  095  null               null               null               null               
  096  null               null               null               null               
  097  null               null               null               null               
  098  null               null               null               null               
  099  null               null               null               null               
  100  null               null               null               null               
  101  null               null               null               null               
  102  null               null               null               null               
  103  null               null               null               null               
  104  null               null               null               null               
  105  null               null               null               null               
  106  null               null               null               null               
  107  null               null               null               null               
  108  null               null               null               null               
  109  null               null               null               null               
  110  null               null               null               null               
  111  null               null               null               null               
  112  null               null               null               null               
  113  null               null               null               null               
  114  null               null               null               null               
  115  null               null               null               null               
  116  null               null               null               null               
  117  null               null               null               null               
  118  null               null               null               null               
  119  null               null               null               null               
  120  null               null               null               null               
  121  null               null               null               null               
  122  null               null               null               null               
  123  null               null               null               null               
  124  null               null               null               null               
  125  null               null               null               null               
  126  null               null               null               null               
  127  null               null               null               null               
  128  null               null               null               null               
  129  null               null               null               null               
  130  null               null               null               null               
  131  null               null               null               null               
  132  null               null               null               null               
  133  null               null               null               null               
  134  null               null               null               null               
  135  null               null               null               null               
  136  null               null               null               null               
  137  null               null               null               null               
  138  null               null               null               null               
  139  null               null               null               null               
  140  null               null               null               null               
  141  null               null               null               null               
  142  null               null               null               null               
  143  null               null               null               null               
  144  null               null               null               null               
  145  null               null               null               null               
  146  null               null               null               null               
  147  null               null               null               null               
  148  null               null               null               null               
  149  null               null               null               null               
  150  null               null               null               null               
  151  null               null               null               null               
  152  null               null               null               null               
  153  null               null               null               null               
  154  null               null               null               null               
  155  null               null               null               null               
  156  null               null               null               null               
  157  null               null               null               null               
  158  null               null               null               null               
  159  null               null               null               null               
  160  null               null               null               null               
  161  null               null               null               null               
  162  null               null               null               null               
  163  null               null               null               null               
  164  null               null               null               null               
  165  null               null               null               null               
  166  null               null               null               null               
  167  null               null               null               null               
  168  null               null               null               null               
  169  null               null               null               null               
  170  null               null               null               null               
  171  null               null               null               null               
  172  null               null               null               null               
  173  null               null               null               null               
  174  null               null               null               null               
  175  null               null               null               null               
  176  null               null               null               null               
  177  null               null               null               null               
  178  null               null               null               null               
  179  null               null               null               null               
  180  null               null               null               null               
  181  null               null               null               null               
  182  null               null               null               null               
  183  null               null               null               null               
  184  null               null               null               null               
  185  null               null               null               null               
  186  null               null               null               null               
  187  null               null               null               null               
  188  null               null               null               null               
  189  null               null               null               null               
  190  null               null               null               null               
  191  null               null               null               null               
  192  null               null               null               null               
  193  null               null               null               null               
  194  null               null               null               null               
  195  null               null               null               null               
  196  null               null               null               null               
  197  null               null               null               null               
  198  null               null               null               null               
  199  null               null               null               null               
  200  null               null               null               null               
  201  null               null               null               null               
  202  null               null               null               null               
  203  null               null               null               null               
  204  null               null               null               null               
  205  null               null               null               null               
  206  null               null               null               null               
  207  null               null               null               null               
  208  null               null               null               null               
  209  null               null               null               null               
  210  null               null               null               null               
  211  null               null               null               null               
  212  null               null               null               null               
  213  null               null               null               null               
  214  null               null               null               null               
  215  null               null               null               null               
  216  null               null               null               null               
  217  null               null               null               null               
  218  null               null               null               null               
  219  null               null               null               null               
  220  null               null               null               null               
  221  null               null               null               null               
  222  null               null               null               null               
  223  null               null               null               null               
  224  null               null               null               null               
  225  null               null               null               null               
  226  null               null               null               null               
  227  null               null               null               null               
  228  null               null               null               null               
  229  null               null               null               null               
  230  null               null               null               null               
  231  null               null               null               null               
  232  null               null               null               null               
  233  null               null               null               null               
  234  null               null               null               null               
  235  null               null               null               null               
  236  null               null               null               null               
  237  null               null               null               null               
  238  null               null               null               null               
  239  null               null               null               null               
  240  null               null               null               null               
  241  null               null               null               null               
  242  null               null               null               null               
  243  null               null               null               null               
  244  null               null               null               null               
  245  null               null               null               null               
  246  null               null               null               null               
  247  null               null               null               null               
  248  null               null               null               null               
  249  null               null               null               null               
  250  null               null               null               null               
  251  null               null               null               null               
  252  null               null               null               null               
  253  null               null               null               null               
  254  null               null               null               null               
  255  null               null               null               null               
06/07/2008 20:49:24 # keyboard(down, 0x68 "h") uip=0  61.3225
06/07/2008 20:49:24 modifier_tweak_keyboard: down keysym=0x68
06/07/2008 20:49:24 tweak_mod: Skip:  down=1 index=-1
06/07/2008 20:49:24 added missing keysym to X display: 016 0x68 "h"
06/07/2008 20:49:24 modifier_tweak_keyboard: KeySym 0x68 "h" -> KeyCode 0x10
06/07/2008 20:49:24 XTestFakeKeyEvent(dpy, keycode=0x10 "h", down)
06/07/2008 20:49:24 calling XTestFakeKeyEvent(16, 1)  61.3273
06/07/2008 20:49:24 tweak_mod: Skip:  down=0 index=-1
06/07/2008 20:49:24 # keyboard(up, 0x68 "h") uip=0  61.4319
06/07/2008 20:49:24 modifier_tweak_keyboard: up keysym=0x68
06/07/2008 20:49:24 modifier_tweak_keyboard: KeySym 0x68 "h" -> KeyCode 0x10
06/07/2008 20:49:24 XTestFakeKeyEvent(dpy, keycode=0x10 "h", up)
06/07/2008 20:49:24 calling XTestFakeKeyEvent(16, 0)  61.4321
06/07/2008 20:49:24 # keyboard(down, 0x65 "e") uip=0  61.7279
06/07/2008 20:49:24 modifier_tweak_keyboard: down keysym=0x65
06/07/2008 20:49:24 tweak_mod: Start:  down=1 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:24 tweak_mod: Finish: down=1 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:24 modifier_tweak_keyboard: KeySym 0x65 "e" -> KeyCode 0xa
06/07/2008 20:49:24 XTestFakeKeyEvent(dpy, keycode=0xa "e", down)
06/07/2008 20:49:24 calling XTestFakeKeyEvent(10, 1)  61.7286
06/07/2008 20:49:24 tweak_mod: Start:  down=0 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:24 tweak_mod: Finish: down=0 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:24 # keyboard(up, 0x65 "e") uip=0  61.7293
06/07/2008 20:49:24 modifier_tweak_keyboard: up keysym=0x65
06/07/2008 20:49:24 modifier_tweak_keyboard: KeySym 0x65 "e" -> KeyCode 0xa
06/07/2008 20:49:24 XTestFakeKeyEvent(dpy, keycode=0xa "e", up)
06/07/2008 20:49:24 calling XTestFakeKeyEvent(10, 0)  61.7295
06/07/2008 20:49:25 # keyboard(down, 0xff08 "BackSpace") uip=0  62.8239
06/07/2008 20:49:25 modifier_tweak_keyboard: down keysym=0xff08
06/07/2008 20:49:25 added missing keysym to X display: 017 0xff08 "BackSpace"
06/07/2008 20:49:25 modifier_tweak_keyboard: KeySym 0xff08 "BackSpace" -> KeyCode 0x11
06/07/2008 20:49:25 XTestFakeKeyEvent(dpy, keycode=0x11 "BackSpace", down)
06/07/2008 20:49:25 calling XTestFakeKeyEvent(17, 1)  62.8265
06/07/2008 20:49:25 # keyboard(up, 0xff08 "BackSpace") uip=0  62.9359
06/07/2008 20:49:25 modifier_tweak_keyboard: up keysym=0xff08
06/07/2008 20:49:25 modifier_tweak_keyboard: KeySym 0xff08 "BackSpace" -> KeyCode 0x11
06/07/2008 20:49:25 XTestFakeKeyEvent(dpy, keycode=0x11 "BackSpace", up)
06/07/2008 20:49:25 calling XTestFakeKeyEvent(17, 0)  62.9361
06/07/2008 20:49:26 initialize_modtweak: keycode -> keysyms mapping info:
  008  null               null               null               null               
  009  l                  l                  l                  l                  
  010  e                  e                  e                  e                  
  011  a                  a                  a                  a                  
  012  f                  f                  f                  f                  
  013  p                  p                  p                  p                  
  014  d                  d                  d                  d                  
  015  Return             Return             Return             Return             
  016  h                  h                  h                  h                  
  017  BackSpace          BackSpace          BackSpace          BackSpace          
  018  null               null               null               null               
  019  null               null               null               null               
  020  null               null               null               null               
  021  null               null               null               null               
  022  null               null               null               null               
  023  null               null               null               null               
  024  null               null               null               null               
  025  null               null               null               null               
  026  null               null               null               null               
  027  null               null               null               null               
  028  null               null               null               null               
  029  null               null               null               null               
  030  null               null               null               null               
  031  null               null               null               null               
  032  null               null               null               null               
  033  null               null               null               null               
  034  null               null               null               null               
  035  null               null               null               null               
  036  null               null               null               null               
  037  null               null               null               null               
  038  null               null               null               null               
  039  null               null               null               null               
  040  null               null               null               null               
  041  null               null               null               null               
  042  null               null               null               null               
  043  null               null               null               null               
  044  null               null               null               null               
  045  null               null               null               null               
  046  null               null               null               null               
  047  null               null               null               null               
  048  null               null               null               null               
  049  null               null               null               null               
  050  null               null               null               null               
  051  null               null               null               null               
  052  null               null               null               null               
  053  null               null               null               null               
  054  null               null               null               null               
  055  null               null               null               null               
  056  null               null               null               null               
  057  null               null               null               null               
  058  null               null               null               null               
  059  null               null               null               null               
  060  null               null               null               null               
  061  null               null               null               null               
  062  null               null               null               null               
  063  null               null               null               null               
  064  null               null               null               null               
  065  null               null               null               null               
  066  null               null               null               null               
  067  null               null               null               null               
  068  null               null               null               null               
  069  null               null               null               null               
  070  null               null               null               null               
  071  null               null               null               null               
  072  null               null               null               null               
  073  null               null               null               null               
  074  null               null               null               null               
  075  null               null               null               null               
  076  null               null               null               null               
  077  null               null               null               null               
  078  null               null               null               null               
  079  null               null               null               null               
  080  null               null               null               null               
  081  null               null               null               null               
  082  null               null               null               null               
  083  null               null               null               null               
  084  null               null               null               null               
  085  null               null               null               null               
  086  null               null               null               null               
  087  null               null               null               null               
  088  null               null               null               null               
  089  null               null               null               null               
  090  null               null               null               null               
  091  null               null               null               null               
  092  null               null               null               null               
  093  null               null               null               null               
  094  null               null               null               null               
  095  null               null               null               null               
  096  null               null               null               null               
  097  null               null               null               null               
  098  null               null               null               null               
  099  null               null               null               null               
  100  null               null               null               null               
  101  null               null               null               null               
  102  null               null               null               null               
  103  null               null               null               null               
  104  null               null               null               null               
  105  null               null               null               null               
  106  null               null               null               null               
  107  null               null               null               null               
  108  null               null               null               null               
  109  null               null               null               null               
  110  null               null               null               null               
  111  null               null               null               null               
  112  null               null               null               null               
  113  null               null               null               null               
  114  null               null               null               null               
  115  null               null               null               null               
  116  null               null               null               null               
  117  null               null               null               null               
  118  null               null               null               null               
  119  null               null               null               null               
  120  null               null               null               null               
  121  null               null               null               null               
  122  null               null               null               null               
  123  null               null               null               null               
  124  null               null               null               null               
  125  null               null               null               null               
  126  null               null               null               null               
  127  null               null               null               null               
  128  null               null               null               null               
  129  null               null               null               null               
  130  null               null               null               null               
  131  null               null               null               null               
  132  null               null               null               null               
  133  null               null               null               null               
  134  null               null               null               null               
  135  null               null               null               null               
  136  null               null               null               null               
  137  null               null               null               null               
  138  null               null               null               null               
  139  null               null               null               null               
  140  null               null               null               null               
  141  null               null               null               null               
  142  null               null               null               null               
  143  null               null               null               null               
  144  null               null               null               null               
  145  null               null               null               null               
  146  null               null               null               null               
  147  null               null               null               null               
  148  null               null               null               null               
  149  null               null               null               null               
  150  null               null               null               null               
  151  null               null               null               null               
  152  null               null               null               null               
  153  null               null               null               null               
  154  null               null               null               null               
  155  null               null               null               null               
  156  null               null               null               null               
  157  null               null               null               null               
  158  null               null               null               null               
  159  null               null               null               null               
  160  null               null               null               null               
  161  null               null               null               null               
  162  null               null               null               null               
  163  null               null               null               null               
  164  null               null               null               null               
  165  null               null               null               null               
  166  null               null               null               null               
  167  null               null               null               null               
  168  null               null               null               null               
  169  null               null               null               null               
  170  null               null               null               null               
  171  null               null               null               null               
  172  null               null               null               null               
  173  null               null               null               null               
  174  null               null               null               null               
  175  null               null               null               null               
  176  null               null               null               null               
  177  null               null               null               null               
  178  null               null               null               null               
  179  null               null               null               null               
  180  null               null               null               null               
  181  null               null               null               null               
  182  null               null               null               null               
  183  null               null               null               null               
  184  null               null               null               null               
  185  null               null               null               null               
  186  null               null               null               null               
  187  null               null               null               null               
  188  null               null               null               null               
  189  null               null               null               null               
  190  null               null               null               null               
  191  null               null               null               null               
  192  null               null               null               null               
  193  null               null               null               null               
  194  null               null               null               null               
  195  null               null               null               null               
  196  null               null               null               null               
  197  null               null               null               null               
  198  null               null               null               null               
  199  null               null               null               null               
  200  null               null               null               null               
  201  null               null               null               null               
  202  null               null               null               null               
  203  null               null               null               null               
  204  null               null               null               null               
  205  null               null               null               null               
  206  null               null               null               null               
  207  null               null               null               null               
  208  null               null               null               null               
  209  null               null               null               null               
  210  null               null               null               null               
  211  null               null               null               null               
  212  null               null               null               null               
  213  null               null               null               null               
  214  null               null               null               null               
  215  null               null               null               null               
  216  null               null               null               null               
  217  null               null               null               null               
  218  null               null               null               null               
  219  null               null               null               null               
  220  null               null               null               null               
  221  null               null               null               null               
  222  null               null               null               null               
  223  null               null               null               null               
  224  null               null               null               null               
  225  null               null               null               null               
  226  null               null               null               null               
  227  null               null               null               null               
  228  null               null               null               null               
  229  null               null               null               null               
  230  null               null               null               null               
  231  null               null               null               null               
  232  null               null               null               null               
  233  null               null               null               null               
  234  null               null               null               null               
  235  null               null               null               null               
  236  null               null               null               null               
  237  null               null               null               null               
  238  null               null               null               null               
  239  null               null               null               null               
  240  null               null               null               null               
  241  null               null               null               null               
  242  null               null               null               null               
  243  null               null               null               null               
  244  null               null               null               null               
  245  null               null               null               null               
  246  null               null               null               null               
  247  null               null               null               null               
  248  null               null               null               null               
  249  null               null               null               null               
  250  null               null               null               null               
  251  null               null               null               null               
  252  null               null               null               null               
  253  null               null               null               null               
  254  null               null               null               null               
  255  null               null               null               null               
06/07/2008 20:49:28 # keyboard(down, 0x67 "g") uip=0  65.2319
06/07/2008 20:49:28 modifier_tweak_keyboard: down keysym=0x67
06/07/2008 20:49:28 tweak_mod: Skip:  down=1 index=-1
06/07/2008 20:49:28 added missing keysym to X display: 018 0x67 "g"
06/07/2008 20:49:28 modifier_tweak_keyboard: KeySym 0x67 "g" -> KeyCode 0x12
06/07/2008 20:49:28 XTestFakeKeyEvent(dpy, keycode=0x12 "g", down)
06/07/2008 20:49:28 calling XTestFakeKeyEvent(18, 1)  65.2345
06/07/2008 20:49:28 tweak_mod: Skip:  down=0 index=-1
06/07/2008 20:49:28 initialize_modtweak: keycode -> keysyms mapping info:
  008  null               null               null               null               
  009  l                  l                  l                  l                  
  010  e                  e                  e                  e                  
  011  a                  a                  a                  a                  
  012  f                  f                  f                  f                  
  013  p                  p                  p                  p                  
  014  d                  d                  d                  d                  
  015  Return             Return             Return             Return             
  016  h                  h                  h                  h                  
  017  BackSpace          BackSpace          BackSpace          BackSpace          
  018  g                  g                  g                  g                  
  019  null               null               null               null               
  020  null               null               null               null               
  021  null               null               null               null               
  022  null               null               null               null               
  023  null               null               null               null               
  024  null               null               null               null               
  025  null               null               null               null               
  026  null               null               null               null               
  027  null               null               null               null               
  028  null               null               null               null               
  029  null               null               null               null               
  030  null               null               null               null               
  031  null               null               null               null               
  032  null               null               null               null               
  033  null               null               null               null               
  034  null               null               null               null               
  035  null               null               null               null               
  036  null               null               null               null               
  037  null               null               null               null               
  038  null               null               null               null               
  039  null               null               null               null               
  040  null               null               null               null               
  041  null               null               null               null               
  042  null               null               null               null               
  043  null               null               null               null               
  044  null               null               null               null               
  045  null               null               null               null               
  046  null               null               null               null               
  047  null               null               null               null               
  048  null               null               null               null               
  049  null               null               null               null               
  050  null               null               null               null               
  051  null               null               null               null               
  052  null               null               null               null               
  053  null               null               null               null               
  054  null               null               null               null               
  055  null               null               null               null               
  056  null               null               null               null               
  057  null               null               null               null               
  058  null               null               null               null               
  059  null               null               null               null               
  060  null               null               null               null               
  061  null               null               null               null               
  062  null               null               null               null               
  063  null               null               null               null               
  064  null               null               null               null               
  065  null               null               null               null               
  066  null               null               null               null               
  067  null               null               null               null               
  068  null               null               null               null               
  069  null               null               null               null               
  070  null               null               null               null               
  071  null               null               null               null               
  072  null               null               null               null               
  073  null               null               null               null               
  074  null               null               null               null               
  075  null               null               null               null               
  076  null               null               null               null               
  077  null               null               null               null               
  078  null               null               null               null               
  079  null               null               null               null               
  080  null               null               null               null               
  081  null               null               null               null               
  082  null               null               null               null               
  083  null               null               null               null               
  084  null               null               null               null               
  085  null               null               null               null               
  086  null               null               null               null               
  087  null               null               null               null               
  088  null               null               null               null               
  089  null               null               null               null               
  090  null               null               null               null               
  091  null               null               null               null               
  092  null               null               null               null               
  093  null               null               null               null               
  094  null               null               null               null               
  095  null               null               null               null               
  096  null               null               null               null               
  097  null               null               null               null               
  098  null               null               null               null               
  099  null               null               null               null               
  100  null               null               null               null               
  101  null               null               null               null               
  102  null               null               null               null               
  103  null               null               null               null               
  104  null               null               null               null               
  105  null               null               null               null               
  106  null               null               null               null               
  107  null               null               null               null               
  108  null               null               null               null               
  109  null               null               null               null               
  110  null               null               null               null               
  111  null               null               null               null               
  112  null               null               null               null               
  113  null               null               null               null               
  114  null               null               null               null               
  115  null               null               null               null               
  116  null               null               null               null               
  117  null               null               null               null               
  118  null               null               null               null               
  119  null               null               null               null               
  120  null               null               null               null               
  121  null               null               null               null               
  122  null               null               null               null               
  123  null               null               null               null               
  124  null               null               null               null               
  125  null               null               null               null               
  126  null               null               null               null               
  127  null               null               null               null               
  128  null               null               null               null               
  129  null               null               null               null               
  130  null               null               null               null               
  131  null               null               null               null               
  132  null               null               null               null               
  133  null               null               null               null               
  134  null               null               null               null               
  135  null               null               null               null               
  136  null               null               null               null               
  137  null               null               null               null               
  138  null               null               null               null               
  139  null               null               null               null               
  140  null               null               null               null               
  141  null               null               null               null               
  142  null               null               null               null               
  143  null               null               null               null               
  144  null               null               null               null               
  145  null               null               null               null               
  146  null               null               null               null               
  147  null               null               null               null               
  148  null               null               null               null               
  149  null               null               null               null               
  150  null               null               null               null               
  151  null               null               null               null               
  152  null               null               null               null               
  153  null               null               null               null               
  154  null               null               null               null               
  155  null               null               null               null               
  156  null               null               null               null               
  157  null               null               null               null               
  158  null               null               null               null               
  159  null               null               null               null               
  160  null               null               null               null               
  161  null               null               null               null               
  162  null               null               null               null               
  163  null               null               null               null               
  164  null               null               null               null               
  165  null               null               null               null               
  166  null               null               null               null               
  167  null               null               null               null               
  168  null               null               null               null               
  169  null               null               null               null               
  170  null               null               null               null               
  171  null               null               null               null               
  172  null               null               null               null               
  173  null               null               null               null               
  174  null               null               null               null               
  175  null               null               null               null               
  176  null               null               null               null               
  177  null               null               null               null               
  178  null               null               null               null               
  179  null               null               null               null               
  180  null               null               null               null               
  181  null               null               null               null               
  182  null               null               null               null               
  183  null               null               null               null               
  184  null               null               null               null               
  185  null               null               null               null               
  186  null               null               null               null               
  187  null               null               null               null               
  188  null               null               null               null               
  189  null               null               null               null               
  190  null               null               null               null               
  191  null               null               null               null               
  192  null               null               null               null               
  193  null               null               null               null               
  194  null               null               null               null               
  195  null               null               null               null               
  196  null               null               null               null               
  197  null               null               null               null               
  198  null               null               null               null               
  199  null               null               null               null               
  200  null               null               null               null               
  201  null               null               null               null               
  202  null               null               null               null               
  203  null               null               null               null               
  204  null               null               null               null               
  205  null               null               null               null               
  206  null               null               null               null               
  207  null               null               null               null               
  208  null               null               null               null               
  209  null               null               null               null               
  210  null               null               null               null               
  211  null               null               null               null               
  212  null               null               null               null               
  213  null               null               null               null               
  214  null               null               null               null               
  215  null               null               null               null               
  216  null               null               null               null               
  217  null               null               null               null               
  218  null               null               null               null               
  219  null               null               null               null               
  220  null               null               null               null               
  221  null               null               null               null               
  222  null               null               null               null               
  223  null               null               null               null               
  224  null               null               null               null               
  225  null               null               null               null               
  226  null               null               null               null               
  227  null               null               null               null               
  228  null               null               null               null               
  229  null               null               null               null               
  230  null               null               null               null               
  231  null               null               null               null               
  232  null               null               null               null               
  233  null               null               null               null               
  234  null               null               null               null               
  235  null               null               null               null               
  236  null               null               null               null               
  237  null               null               null               null               
  238  null               null               null               null               
  239  null               null               null               null               
  240  null               null               null               null               
  241  null               null               null               null               
  242  null               null               null               null               
  243  null               null               null               null               
  244  null               null               null               null               
  245  null               null               null               null               
  246  null               null               null               null               
  247  null               null               null               null               
  248  null               null               null               null               
  249  null               null               null               null               
  250  null               null               null               null               
  251  null               null               null               null               
  252  null               null               null               null               
  253  null               null               null               null               
  254  null               null               null               null               
  255  null               null               null               null               
06/07/2008 20:49:28 # keyboard(up, 0x67 "g") uip=0  65.3279
06/07/2008 20:49:28 modifier_tweak_keyboard: up keysym=0x67
06/07/2008 20:49:28 modifier_tweak_keyboard: KeySym 0x67 "g" -> KeyCode 0x12
06/07/2008 20:49:28 XTestFakeKeyEvent(dpy, keycode=0x12 "g", up)
06/07/2008 20:49:28 calling XTestFakeKeyEvent(18, 0)  65.3281
06/07/2008 20:49:28 # keyboard(down, 0x65 "e") uip=0  65.4480
06/07/2008 20:49:28 modifier_tweak_keyboard: down keysym=0x65
06/07/2008 20:49:28 tweak_mod: Start:  down=1 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:28 tweak_mod: Finish: down=1 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:28 modifier_tweak_keyboard: KeySym 0x65 "e" -> KeyCode 0xa
06/07/2008 20:49:28 XTestFakeKeyEvent(dpy, keycode=0xa "e", down)
06/07/2008 20:49:28 calling XTestFakeKeyEvent(10, 1)  65.4485
06/07/2008 20:49:28 tweak_mod: Start:  down=0 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:28 tweak_mod: Finish: down=0 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:28 # keyboard(down, 0x61 "a") uip=0  65.5239
06/07/2008 20:49:28 modifier_tweak_keyboard: down keysym=0x61
06/07/2008 20:49:28 tweak_mod: Start:  down=1 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:28 tweak_mod: Finish: down=1 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:28 modifier_tweak_keyboard: KeySym 0x61 "a" -> KeyCode 0xb
06/07/2008 20:49:28 XTestFakeKeyEvent(dpy, keycode=0xb "a", down)
06/07/2008 20:49:28 calling XTestFakeKeyEvent(11, 1)  65.5245
06/07/2008 20:49:28 tweak_mod: Start:  down=0 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:28 tweak_mod: Finish: down=0 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:28 # keyboard(up, 0x65 "e") uip=0  65.5533
06/07/2008 20:49:28 modifier_tweak_keyboard: up keysym=0x65
06/07/2008 20:49:28 modifier_tweak_keyboard: KeySym 0x65 "e" -> KeyCode 0xa
06/07/2008 20:49:28 XTestFakeKeyEvent(dpy, keycode=0xa "e", up)
06/07/2008 20:49:28 calling XTestFakeKeyEvent(10, 0)  65.5535
06/07/2008 20:49:28 # keyboard(up, 0x61 "a") uip=0  65.6279
06/07/2008 20:49:28 modifier_tweak_keyboard: up keysym=0x61
06/07/2008 20:49:28 modifier_tweak_keyboard: KeySym 0x61 "a" -> KeyCode 0xb
06/07/2008 20:49:28 XTestFakeKeyEvent(dpy, keycode=0xb "a", up)
06/07/2008 20:49:28 calling XTestFakeKeyEvent(11, 0)  65.6281
06/07/2008 20:49:28 # keyboard(down, 0x6e "n") uip=0  65.6294
06/07/2008 20:49:28 modifier_tweak_keyboard: down keysym=0x6e
06/07/2008 20:49:28 tweak_mod: Skip:  down=1 index=-1
06/07/2008 20:49:28 added missing keysym to X display: 019 0x6e "n"
06/07/2008 20:49:28 modifier_tweak_keyboard: KeySym 0x6e "n" -> KeyCode 0x13
06/07/2008 20:49:28 XTestFakeKeyEvent(dpy, keycode=0x13 "n", down)
06/07/2008 20:49:28 calling XTestFakeKeyEvent(19, 1)  65.6321
06/07/2008 20:49:28 tweak_mod: Skip:  down=0 index=-1
06/07/2008 20:49:28 # keyboard(up, 0x6e "n") uip=0  65.6959
06/07/2008 20:49:28 modifier_tweak_keyboard: up keysym=0x6e
06/07/2008 20:49:28 modifier_tweak_keyboard: KeySym 0x6e "n" -> KeyCode 0x13
06/07/2008 20:49:28 XTestFakeKeyEvent(dpy, keycode=0x13 "n", up)
06/07/2008 20:49:28 calling XTestFakeKeyEvent(19, 0)  65.6962
06/07/2008 20:49:28 # keyboard(down, 0x79 "y") uip=0  65.8359
06/07/2008 20:49:28 modifier_tweak_keyboard: down keysym=0x79
06/07/2008 20:49:28 tweak_mod: Skip:  down=1 index=-1
06/07/2008 20:49:28 added missing keysym to X display: 020 0x79 "y"
06/07/2008 20:49:28 modifier_tweak_keyboard: KeySym 0x79 "y" -> KeyCode 0x14
06/07/2008 20:49:28 XTestFakeKeyEvent(dpy, keycode=0x14 "y", down)
06/07/2008 20:49:28 calling XTestFakeKeyEvent(20, 1)  65.8385
06/07/2008 20:49:28 tweak_mod: Skip:  down=0 index=-1
06/07/2008 20:49:28 # keyboard(up, 0x79 "y") uip=0  65.8987
06/07/2008 20:49:28 modifier_tweak_keyboard: up keysym=0x79
06/07/2008 20:49:28 modifier_tweak_keyboard: KeySym 0x79 "y" -> KeyCode 0x14
06/07/2008 20:49:28 XTestFakeKeyEvent(dpy, keycode=0x14 "y", up)
06/07/2008 20:49:28 calling XTestFakeKeyEvent(20, 0)  65.8989
06/07/2008 20:49:28 # keyboard(down, 0xff0d "Return") uip=0  66.0440
06/07/2008 20:49:28 modifier_tweak_keyboard: down keysym=0xff0d
06/07/2008 20:49:28 modifier_tweak_keyboard: KeySym 0xff0d "Return" -> KeyCode 0xf
06/07/2008 20:49:28 XTestFakeKeyEvent(dpy, keycode=0xf "Return", down)
06/07/2008 20:49:28 calling XTestFakeKeyEvent(15, 1)  66.0445
06/07/2008 20:49:28 # keyboard(up, 0xff0d "Return") uip=0  66.1451
06/07/2008 20:49:28 modifier_tweak_keyboard: up keysym=0xff0d
06/07/2008 20:49:28 modifier_tweak_keyboard: KeySym 0xff0d "Return" -> KeyCode 0xf
06/07/2008 20:49:28 XTestFakeKeyEvent(dpy, keycode=0xf "Return", up)
06/07/2008 20:49:28 calling XTestFakeKeyEvent(15, 0)  66.1453
06/07/2008 20:49:30 client 1 network rate 70.5 KB/sec (6859.0 eff KB/sec)
06/07/2008 20:49:30 client 1 latency:  12.2 ms
06/07/2008 20:49:30 dt1: 0.0940, dt2: 0.2514 dt3: 0.0122 bytes: 23913
06/07/2008 20:49:30 link_rate: LR_BROADBAND - 12 ms, 70 KB/s
06/07/2008 20:49:30 initialize_modtweak: keycode -> keysyms mapping info:
  008  null               null               null               null               
  009  l                  l                  l                  l                  
  010  e                  e                  e                  e                  
  011  a                  a                  a                  a                  
  012  f                  f                  f                  f                  
  013  p                  p                  p                  p                  
  014  d                  d                  d                  d                  
  015  Return             Return             Return             Return             
  016  h                  h                  h                  h                  
  017  BackSpace          BackSpace          BackSpace          BackSpace          
  018  g                  g                  g                  g                  
  019  n                  n                  n                  n                  
  020  y                  y                  y                  y                  
  021  null               null               null               null               
  022  null               null               null               null               
  023  null               null               null               null               
  024  null               null               null               null               
  025  null               null               null               null               
  026  null               null               null               null               
  027  null               null               null               null               
  028  null               null               null               null               
  029  null               null               null               null               
  030  null               null               null               null               
  031  null               null               null               null               
  032  null               null               null               null               
  033  null               null               null               null               
  034  null               null               null               null               
  035  null               null               null               null               
  036  null               null               null               null               
  037  null               null               null               null               
  038  null               null               null               null               
  039  null               null               null               null               
  040  null               null               null               null               
  041  null               null               null               null               
  042  null               null               null               null               
  043  null               null               null               null               
  044  null               null               null               null               
  045  null               null               null               null               
  046  null               null               null               null               
  047  null               null               null               null               
  048  null               null               null               null               
  049  null               null               null               null               
  050  null               null               null               null               
  051  null               null               null               null               
  052  null               null               null               null               
  053  null               null               null               null               
  054  null               null               null               null               
  055  null               null               null               null               
  056  null               null               null               null               
  057  null               null               null               null               
  058  null               null               null               null               
  059  null               null               null               null               
  060  null               null               null               null               
  061  null               null               null               null               
  062  null               null               null               null               
  063  null               null               null               null               
  064  null               null               null               null               
  065  null               null               null               null               
  066  null               null               null               null               
  067  null               null               null               null               
  068  null               null               null               null               
  069  null               null               null               null               
  070  null               null               null               null               
  071  null               null               null               null               
  072  null               null               null               null               
  073  null               null               null               null               
  074  null               null               null               null               
  075  null               null               null               null               
  076  null               null               null               null               
  077  null               null               null               null               
  078  null               null               null               null               
  079  null               null               null               null               
  080  null               null               null               null               
  081  null               null               null               null               
  082  null               null               null               null               
  083  null               null               null               null               
  084  null               null               null               null               
  085  null               null               null               null               
  086  null               null               null               null               
  087  null               null               null               null               
  088  null               null               null               null               
  089  null               null               null               null               
  090  null               null               null               null               
  091  null               null               null               null               
  092  null               null               null               null               
  093  null               null               null               null               
  094  null               null               null               null               
  095  null               null               null               null               
  096  null               null               null               null               
  097  null               null               null               null               
  098  null               null               null               null               
  099  null               null               null               null               
  100  null               null               null               null               
  101  null               null               null               null               
  102  null               null               null               null               
  103  null               null               null               null               
  104  null               null               null               null               
  105  null               null               null               null               
  106  null               null               null               null               
  107  null               null               null               null               
  108  null               null               null               null               
  109  null               null               null               null               
  110  null               null               null               null               
  111  null               null               null               null               
  112  null               null               null               null               
  113  null               null               null               null               
  114  null               null               null               null               
  115  null               null               null               null               
  116  null               null               null               null               
  117  null               null               null               null               
  118  null               null               null               null               
  119  null               null               null               null               
  120  null               null               null               null               
  121  null               null               null               null               
  122  null               null               null               null               
  123  null               null               null               null               
  124  null               null               null               null               
  125  null               null               null               null               
  126  null               null               null               null               
  127  null               null               null               null               
  128  null               null               null               null               
  129  null               null               null               null               
  130  null               null               null               null               
  131  null               null               null               null               
  132  null               null               null               null               
  133  null               null               null               null               
  134  null               null               null               null               
  135  null               null               null               null               
  136  null               null               null               null               
  137  null               null               null               null               
  138  null               null               null               null               
  139  null               null               null               null               
  140  null               null               null               null               
  141  null               null               null               null               
  142  null               null               null               null               
  143  null               null               null               null               
  144  null               null               null               null               
  145  null               null               null               null               
  146  null               null               null               null               
  147  null               null               null               null               
  148  null               null               null               null               
  149  null               null               null               null               
  150  null               null               null               null               
  151  null               null               null               null               
  152  null               null               null               null               
  153  null               null               null               null               
  154  null               null               null               null               
  155  null               null               null               null               
  156  null               null               null               null               
  157  null               null               null               null               
  158  null               null               null               null               
  159  null               null               null               null               
  160  null               null               null               null               
  161  null               null               null               null               
  162  null               null               null               null               
  163  null               null               null               null               
  164  null               null               null               null               
  165  null               null               null               null               
  166  null               null               null               null               
  167  null               null               null               null               
  168  null               null               null               null               
  169  null               null               null               null               
  170  null               null               null               null               
  171  null               null               null               null               
  172  null               null               null               null               
  173  null               null               null               null               
  174  null               null               null               null               
  175  null               null               null               null               
  176  null               null               null               null               
  177  null               null               null               null               

  178  null               null               null               null               
  179  null               null               null               null               
  180  null               null               null               null               
  181  null               null               null               null               
  182  null               null               null               null               
  183  null               null               null               null               
  184  null               null               null               null               
  185  null               null               null               null               
  186  null               null               null               null               
  187  null               null               null               null               
  188  null               null               null               null               
  189  null               null               null               null               
  190  null               null               null               null               
  191  null               null               null               null               
  192  null               null               null               null               
  193  null               null               null               null               
  194  null               null               null               null               
  195  null               null               null               null               
  196  null               null               null               null               
  197  null               null               null               null               
  198  null               null               null               null               
  199  null               null               null               null               
  200  null               null               null               null               
  201  null               null               null               null               
  202  null               null               null               null               
  203  null               null               null               null               
  204  null               null               null               null               
  205  null               null               null               null               
  206  null               null               null               null               
  207  null               null               null               null               
  208  null               null               null               null               
  209  null               null               null               null               
  210  null               null               null               null               
  211  null               null               null               null               
  212  null               null               null               null               
  213  null               null               null               null               
  214  null               null               null               null               
  215  null               null               null               null               
  216  null               null               null               null               
  217  null               null               null               null               
  218  null               null               null               null               
  219  null               null               null               null               
  220  null               null               null               null               
  221  null               null               null               null               
  222  null               null               null               null               
  223  null               null               null               null               
  224  null               null               null               null               
  225  null               null               null               null               
  226  null               null               null               null               
  227  null               null               null               null               
  228  null               null               null               null               
  229  null               null               null               null               
  230  null               null               null               null               
  231  null               null               null               null               
  232  null               null               null               null               
  233  null               null               null               null               
  234  null               null               null               null               
  235  null               null               null               null               
  236  null               null               null               null               
  237  null               null               null               null               
  238  null               null               null               null               
  239  null               null               null               null               
  240  null               null               null               null               
  241  null               null               null               null               
  242  null               null               null               null               
  243  null               null               null               null               
  244  null               null               null               null               
  245  null               null               null               null               
  246  null               null               null               null               
  247  null               null               null               null               
  248  null               null               null               null               
  249  null               null               null               null               
  250  null               null               null               null               
  251  null               null               null               null               
  252  null               null               null               null               
  253  null               null               null               null               
  254  null               null               null               null               
  255  null               null               null               null               
06/07/2008 20:49:31 # keyboard(down, 0x68 "h") uip=0  68.7749
06/07/2008 20:49:31 modifier_tweak_keyboard: down keysym=0x68
06/07/2008 20:49:31 tweak_mod: Start:  down=1 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:31 tweak_mod: Finish: down=1 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:31 modifier_tweak_keyboard: KeySym 0x68 "h" -> KeyCode 0x10
06/07/2008 20:49:31 XTestFakeKeyEvent(dpy, keycode=0x10 "h", down)
06/07/2008 20:49:31 calling XTestFakeKeyEvent(16, 1)  68.7763
06/07/2008 20:49:31 tweak_mod: Start:  down=0 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:31 tweak_mod: Finish: down=0 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:31 # keyboard(up, 0x68 "h") uip=0  68.8439
06/07/2008 20:49:31 modifier_tweak_keyboard: up keysym=0x68
06/07/2008 20:49:31 modifier_tweak_keyboard: KeySym 0x68 "h" -> KeyCode 0x10
06/07/2008 20:49:31 XTestFakeKeyEvent(dpy, keycode=0x10 "h", up)
06/07/2008 20:49:31 calling XTestFakeKeyEvent(16, 0)  68.8441
06/07/2008 20:49:31 # keyboard(down, 0x65 "e") uip=0  68.8683
06/07/2008 20:49:31 modifier_tweak_keyboard: down keysym=0x65
06/07/2008 20:49:31 tweak_mod: Start:  down=1 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:31 tweak_mod: Finish: down=1 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:31 modifier_tweak_keyboard: KeySym 0x65 "e" -> KeyCode 0xa
06/07/2008 20:49:31 XTestFakeKeyEvent(dpy, keycode=0xa "e", down)
06/07/2008 20:49:31 calling XTestFakeKeyEvent(10, 1)  68.8688
06/07/2008 20:49:31 tweak_mod: Start:  down=0 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:31 tweak_mod: Finish: down=0 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:31 # keyboard(up, 0x65 "e") uip=0  69.1535
06/07/2008 20:49:31 modifier_tweak_keyboard: up keysym=0x65
06/07/2008 20:49:31 modifier_tweak_keyboard: KeySym 0x65 "e" -> KeyCode 0xa
06/07/2008 20:49:31 XTestFakeKeyEvent(dpy, keycode=0xa "e", up)
06/07/2008 20:49:31 calling XTestFakeKeyEvent(10, 0)  69.1537
06/07/2008 20:49:31 # keyboard(down, 0x6c "l") uip=0  69.1540
06/07/2008 20:49:31 modifier_tweak_keyboard: down keysym=0x6c
06/07/2008 20:49:31 tweak_mod: Start:  down=1 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:31 tweak_mod: Finish: down=1 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:31 modifier_tweak_keyboard: KeySym 0x6c "l" -> KeyCode 0x9
06/07/2008 20:49:31 XTestFakeKeyEvent(dpy, keycode=0x9 "l", down)
06/07/2008 20:49:31 calling XTestFakeKeyEvent(9, 1)  69.1546
06/07/2008 20:49:31 tweak_mod: Start:  down=0 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:31 tweak_mod: Finish: down=0 index=3 mod_state=0x0 is_shift=0
06/07/2008 20:49:31 # keyboard(up, 0x6c "l") uip=0  69.1553
06/07/2008 20:49:31 modifier_tweak_keyboard: up keysym=0x6c
06/07/2008 20:49:31 modifier_tweak_keyboard: KeySym 0x6c "l" -> KeyCode 0x9
06/07/2008 20:49:31 XTestFakeKeyEvent(dpy, keycode=0x9 "l", up)
06/07/2008 20:49:31 calling XTestFakeKeyEvent(9, 0)  69.1554
06/07/2008 20:49:33 # keyboard(down, 0xff08 "BackSpace") uip=0  70.2199
06/07/2008 20:49:33 modifier_tweak_keyboard: down keysym=0xff08
06/07/2008 20:49:33 modifier_tweak_keyboard: KeySym 0xff08 "BackSpace" -> KeyCode 0x11
06/07/2008 20:49:33 XTestFakeKeyEvent(dpy, keycode=0x11 "BackSpace", down)
06/07/2008 20:49:33 calling XTestFakeKeyEvent(17, 1)  70.2205
06/07/2008 20:49:33 # keyboard(up, 0xff08 "BackSpace") uip=0  70.2879
06/07/2008 20:49:33 modifier_tweak_keyboard: up keysym=0xff08
06/07/2008 20:49:33 modifier_tweak_keyboard: KeySym 0xff08 "BackSpace" -> KeyCode 0x11
06/07/2008 20:49:33 XTestFakeKeyEvent(dpy, keycode=0x11 "BackSpace", up)
06/07/2008 20:49:33 calling XTestFakeKeyEvent(17, 0)  70.2881
06/07/2008 20:49:33 # keyboard(down, 0xff08 "BackSpace") uip=0  70.3615
06/07/2008 20:49:33 modifier_tweak_keyboard: down keysym=0xff08
06/07/2008 20:49:33 modifier_tweak_keyboard: KeySym 0xff08 "BackSpace" -> KeyCode 0x11
06/07/2008 20:49:33 XTestFakeKeyEvent(dpy, keycode=0x11 "BackSpace", down)
06/07/2008 20:49:33 calling XTestFakeKeyEvent(17, 1)  70.3619
06/07/2008 20:49:33 # keyboard(up, 0xff08 "BackSpace") uip=0  70.4399
06/07/2008 20:49:33 modifier_tweak_keyboard: up keysym=0xff08
06/07/2008 20:49:33 modifier_tweak_keyboard: KeySym 0xff08 "BackSpace" -> KeyCode 0x11
06/07/2008 20:49:33 XTestFakeKeyEvent(dpy, keycode=0x11 "BackSpace", up)
06/07/2008 20:49:33 calling XTestFakeKeyEvent(17, 0)  70.4401
06/07/2008 20:49:37 increased wireframe timeouts for slow network connection.
06/07/2008 20:49:37 netrate: 70 KB/sec, latency: 12 ms
06/07/2008 20:49:38 client_count: 0
06/07/2008 20:49:38 Restored X server key autorepeat to: 1
06/07/2008 20:49:38 viewer exited.
06/07/2008 20:49:38 deleted 32 tile_row polling images.
06/07/2008 20:49:38 deleted keycode from X display: 009 0x6c "l"
06/07/2008 20:49:38 deleted keycode from X display: 010 0x65 "e"
06/07/2008 20:49:38 deleted keycode from X display: 011 0x61 "a"
06/07/2008 20:49:38 deleted keycode from X display: 012 0x66 "f"
06/07/2008 20:49:38 deleted keycode from X display: 013 0x70 "p"
06/07/2008 20:49:38 deleted keycode from X display: 014 0x64 "d"
06/07/2008 20:49:38 deleted keycode from X display: 015 0xff0d "Return"
06/07/2008 20:49:38 deleted keycode from X display: 016 0x68 "h"
06/07/2008 20:49:38 deleted keycode from X display: 017 0xff08 "BackSpace"
06/07/2008 20:49:38 deleted keycode from X display: 018 0x67 "g"
06/07/2008 20:49:38 deleted keycode from X display: 019 0x6e "n"
06/07/2008 20:49:38 deleted keycode from X display: 020 0x79 "y"
```

---

### Post by krunge on 2008-07-07
> **jediborger said:**
> Thanks for the help. Here's the log file since it's too big to attach.


Thanks that's useful info.

However I asked you for output where x11vnc fails as you described ("X Error of failed request:  BadValue ...").  If you could get that it would be useful.

In any event with the -dk debug keyboard output, one can see keyboard mapping starts out in a very weird state:

  008  null               null               null               null

etc. for all keycode numbers. So, at least at this level, your X server **has no keyboard mappings at all**.  So I am not surprised there are problems when typing into applications.

You should be able to see an empty mapping via "xmodmap -pk".  Try it and see (I suggest restarting the X server or the entire machine before running it).

It would be useful to see the same output you posted but adding "-xkb" to x11vnc's command line options.  Please send it.

Anyway, when you type a letter like "e" x11vnc desparately tries to add it to the (initially empty) keymapping.  Having x11vnc do this for every key is a bad idea and you should look into what is leading to the empty mapping.

Have you upgraded recently to some broken version of Ubuntu where it might misconfigure X server settings for some setups?

Maybe the broken setup is due to some incorrect locale setting or perhaps some (presumably incorrect) keyboard accessibility mapping?

Do you have any input hardware that might remap keystrokes, mouse events or both?

---

### Post by jediborger on 2008-07-09
So in short are you saying I should hook up some real hardware to the server and run Xorg? Although I don't have Xorg installed, just Xvfb. As for input hardware, there has not been any attached to it since I first installed gutsy on it and have since upgraded to hardy.

Here's the terminal output from the X11vnc crash:
```
09/07/2008 18:48:28 Got connection from client 192.168.1.43
09/07/2008 18:48:28   other clients:
09/07/2008 18:48:28 Disabled X server key autorepeat.
09/07/2008 18:48:28   to force back on run: 'xset r on' (3 times)
09/07/2008 18:48:28 created xdamage object: 0x400024
09/07/2008 18:48:28 Client Protocol Version 3.8
09/07/2008 18:48:28 Protocol version sent 3.8, using 3.8
09/07/2008 18:48:28 rfbProcessClientSecurityType: executing handler for type 1
09/07/2008 18:48:28 rfbProcessClientSecurityType: returning securityResult for client rfb version >= 3.8
09/07/2008 18:48:28 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0xFFFFFEFE)
09/07/2008 18:48:28 Enabling NewFBSize protocol extension for client 192.168.1.43
09/07/2008 18:48:28 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0x574D5669)
09/07/2008 18:48:28 Enabling full-color cursor updates for client 192.168.1.43
09/07/2008 18:48:28 Enabling X-style cursor updates for client 192.168.1.43
09/07/2008 18:48:28 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0xFFFFFEFF)
09/07/2008 18:48:28 Using tight encoding for client 192.168.1.43
caught X11 error:
09/07/2008 18:48:36 deleted 32 tile_row polling images.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7a7e767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7a7e81e]
#2 /usr/lib/libX11.so.6 [0xb7c9e518]
#3 /usr/lib/libX11.so.6(XGetKeyboardControl+0x34) [0xb7c7d114]
#4 x11vnc [0x8062695]
#5 x11vnc [0x80626f6]
#6 x11vnc [0x80541c9]
#7 x11vnc [0x80542fa]
#8 /usr/lib/libX11.so.6(_XError+0xfe) [0xb7c9773e]
#9 /usr/lib/libX11.so.6 [0xb7c9ee5c]
#10 /usr/lib/libX11.so.6(_XEventsQueued+0x4f) [0xb7c9f71f]
#11 /usr/lib/libX11.so.6(_XFlush+0x42) [0xb7c9f7a2]
#12 /usr/lib/libX11.so.6(XFlush+0x31) [0xb7c78a91]
#13 x11vnc [0x8064c7a]
#14 /usr/lib/libvncserver.so.0(rfbProcessClientMessage+0xe80) [0xb7f48e70]
#15 /usr/lib/libvncserver.so.0(rfbCheckFds+0x357) [0xb7f4c6c7]
#16 /usr/lib/libvncserver.so.0(rfbProcessEvents+0x30) [0xb7f41af0]
#17 x11vnc [0x80b8b0c]
#18 x11vnc [0x80c2bf5]
#19 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7aa6450]
extra[1] signal: 0
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  132 (XTEST)
  Minor opcode of failed request:  2 (X_XTestFakeInput)
  Value in failed request:  0x0
  Serial number of failed request:  4397
  Current serial number in output stream:  4398

```

So it sounds like I need to create a keymap. How would I go about doing that?

---

### Post by krunge on 2008-07-10
> **jediborger said:**
> So in short are you saying I should hook up some real hardware to the server and run Xorg? Although I don't have Xorg installed, just Xvfb.

Ah, that would have been useful info in your original post that you were using Xvfb instead of Xorg; it is misleading otherwise.  People sometimes use "headless" to mean no monitor, keyboard, or mouse; but they still run x11vnc pointed at Xorg on the video card.

But in any event x11vnc+Xvfb should work fine: I use it every day on several machines.

I'm not sure how Xvfb works these days. Perhaps by not having Xorg installed there are some shared things (fonts, keyboard mapping files, xorg.conf, etc) that are not present and cause Xvfb to work sub-optimally.

So I don't really know how to fix it... I'm not saying run Xorg on the hardware video card (since that can often be much slower), just perhaps installing the Xorg packages might help (but maybe they are already installed...)

> As for input hardware, there has not been any attached to it since I first installed gutsy on it and have since upgraded to hardy.

Here's the terminal output from the X11vnc crash:
```

X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  132 (XTEST)
  Minor opcode of failed request:  2 (X_XTestFakeInput)
  Value in failed request:  0x0
  Serial number of failed request:  4397
  Current serial number in output stream:  4398

```

So it sounds like I need to create a keymap. How would I go about doing that?

Hmmm, could it be the upgrade wiped some important Xorg files since there was no video hardware??

Also, did you run this with -dk?  If so, I don't see any keyboard debugging printout.  Makes me wonder if the X_XTestFakeInput error is mouse button (or motion?) related instead of keystroke related.

Run x11vnc as above, but with -dk and -dp options, and then induce the  X_XTestFakeInput crash, and post the output here again, thanks.

As to how to add a keymapping, I am not sure... all of the machines I run Xvfb on has Xorg installed (or XFree86 on the older ones).

BTW x11vnc in using the "-create" option (will start up Xvfb automatically for you) will add some keysyms by default, mostly modifiers like both Shift's, both Control's etc, because Xvfb by default skimps on the modifier keys in the mapping.

---

### Post by jediborger on 2009-05-12
I"m posting this here just in case anyone in the future has this issue.

I did not really solve the issue but found a work around. Install tightvncserver and use that instead of x11vnc. I have no text segfault issues when running tightvnc.

---

### Post by robertbub on 2010-11-13
I just downloaded and installed x11vnc version: 0.9.12 .

But, I get exactly the same error as originally posted.

It happens the moment I try scrolling with my scroll "wheel" on my touchpad.

Does anyone else have this problem?  Is there a fix?

---

### Post by krunge on 2010-11-13
> **robertbub said:**
> I just downloaded and installed x11vnc version: 0.9.12 .

But, I get exactly the same error as originally posted.

It happens the moment I try scrolling with my scroll "wheel" on my touchpad.

Does anyone else have this problem?  Is there a fix?
Please send the full output from x11vnc.

Also send the output of the command "xmodmap -pp" for the X display in question.

---

### Post by robertbub on 2010-11-14
I discovered that if I follow the prescription in [http://www.karlrunge.com/x11vnc/faq.html#faq-buttonmap-opt](http://www.karlrunge.com/x11vnc/faq.html#faq-buttonmap-opt) (Q-86):```
-buttonmap 12345-123:Prior::Next:
-buttonmap 12345-123:Up+Up+Up::Down+Down+Down:
```
as a workaround, it prevents x11vnc from exiting with a crash.  (Of course, mouse "wheel" scrolling is now erratic, jumpy, and sensitive, but at least x11vnc doesn't die.)

It may be due to the fact that I'm running in possibly a strange environment.  Below is a piece from my */var/log/Xorg.0.log*.  You'll see that my X display was set up by VirtualBox.```
Section "Device"
     Identifier      "Builtin Default vboxvideo Device 0"
     Driver  "vboxvideo"
EndSection
Section "Screen"
     Identifier      "Builtin Default vboxvideo Screen 0"
     Device  "Builtin Default vboxvideo Device 0"
EndSection
Section "Device"
     Identifier      "Builtin Default vesa Device 0"
     Driver  "vesa"
EndSection
Section "Screen"
     Identifier      "Builtin Default vesa Screen 0"
     Device  "Builtin Default vesa Device 0"
EndSection
Section "Device"
     Identifier      "Builtin Default fbdev Device 0"
     Driver  "fbdev"
EndSection
Section "Screen"
     Identifier      "Builtin Default fbdev Screen 0"
     Device  "Builtin Default fbdev Device 0"
EndSection
Section "ServerLayout"
     Identifier      "Builtin Default Layout"
     Screen  "Builtin Default vboxvideo Screen 0"
     Screen  "Builtin Default vesa Screen 0"
     Screen  "Builtin Default fbdev Screen 0"
EndSection
```

---

### Post by krunge on 2010-11-14
Send me "xmodmap -pp" output.  My guess is it will say something like this:
```

% xmodmap -pp
There are 3 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3


```
So you need to configure mousewheel (buttons 4 and 5) somehow.

In the old days (i.e. the machines I use now) something like this:
```

       Option          "ZAxisMapping"          "4 5"

```
in a "InputDevice" section of xorg.conf would do it. Not sure what would work nowadays...

---

### Post by robertbub on 2010-11-14
> **krunge said:**
> Send me "xmodmap -pp" output.```
There are 32 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3
        [snip]
```I cut off the entire list.

I just sent you a private message.  I have a feeling that there's a bad interface between *x11vnc* and my X Windows.

---

### Post by robertbub on 2010-11-15
I'm pretty convinced that this is a Virtualbox driver problem.  See [http://forums.virtualbox.org/viewtopic.php?f=3&t=32383&p=162213](http://forums.virtualbox.org/viewtopic.php?f=3&t=32383&p=162213).  In particular, since *x11vnc* uses XTEST for sending input events (including mouse button presses), it will fail.

I discovered 2 workarounds:
[LIST=1][*]**Disable mouse integration**.  This workaround disables mouse integration from the guest side.  Stick this in your *.x11vncrc*:```
afteraccept xinput set-int-prop "VirtualBox Guest Service" "Device Enabled" 8 0
gone xinput set-int-prop "VirtualBox Guest Service" "Device Enabled" 8 1
```Note that using Virtualbox will be affected -- the mouse won't work correctly while this is in effect.

[*]**Remap button 3 to button 2**.  Use of button 2 is disabled for this workaround.  First, stick this in your *.x11vncrc*:```
buttonmap 12345-122:Prior::Next:
buttonmap 12345-122:Up+Up::Down+Down:
```.  Then, do:```
xmodmap -e "pointer = 1 2 12 4 5 6 7 8 9 10 11 3"
```(i.e., exchange button 3 and button 12).  One caveat: you just have to remember to restore my xmodmap map once you're done using VNC.  Sigh.[/LIST]

---

