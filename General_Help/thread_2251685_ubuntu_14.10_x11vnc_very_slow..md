---
title: "ubuntu 14.10 x11vnc very slow."
date: 2014-11-06
forum: General Help
---

### Post by peterwillcn2 on 2014-11-06
sudo apt-get install x11vnc
sudo x11vnc -xkb -forever -auth /var/run/lightdm/root/:0 -display :0 -rfbport 5900 -bg -o /var/log/x11vnc.log
sudo mkdir /etc/x11vnc/
sudo x11vnc -storepasswd /etc/x11vnc/passwd
sudo x11vnc -xkb -forever -auth /var/run/lightdm/root/:0 -display :0 -rfbauth /etc/x11vnc/passwd -rfbport 5900 -bg -o /var/log/x11vnc.log -geometry 1280x800


   Ubuntu 14.10 don't[COLOR=#333333][FONT=arial] connect the lcd monitor open [/FONT][/COLOR]x11vnc [COLOR=#333333][FONT=arial] display[/FONT][/COLOR][COLOR=#333333][FONT=arial] speed [/FONT][/COLOR]very slow, [COLOR=#333333][FONT=arial]But[/FONT][/COLOR][COLOR=#333333][FONT=arial] the first turn on the monitor[/FONT][/COLOR][COLOR=#333333][FONT=arial] local[/FONT][/COLOR][COLOR=#333333][FONT=arial] after landing,[/FONT][/COLOR][COLOR=#333333][FONT=arial] then open the[/FONT][/COLOR][COLOR=#333333][FONT=arial] VNC[/FONT][/COLOR][COLOR=#333333][FONT=arial] client display[/FONT][/COLOR][COLOR=#333333][FONT=arial] speed[/FONT][/COLOR][COLOR=#333333][FONT=arial] quickly[/FONT][/COLOR][COLOR=#333333][FONT=arial].why?

[/FONT][/COLOR]
06/11/2014 19:40:46 Got connection from client 192.168.0.248
06/11/2014 19:40:46   other clients:
06/11/2014 19:40:46 Normal socket connection
06/11/2014 19:40:46 Disabled X server key autorepeat.
06/11/2014 19:40:46   to force back on run: 'xset r on' (3 times)
06/11/2014 19:40:46 incr accepted_client=1 for 192.168.0.248:58509  sock=11
06/11/2014 19:40:46 Client Protocol Version 3.8
06/11/2014 19:40:46 Protocol version sent 3.8, using 3.8
06/11/2014 19:40:46 rfbProcessClientSecurityType: executing handler for type 1
06/11/2014 19:40:46 rfbProcessClientSecurityType: returning securityResult for client rfb version >= 3.8
06/11/2014 19:40:46 Pixel format for client 192.168.0.248:
06/11/2014 19:40:46   32 bpp, depth 24, little endian
06/11/2014 19:40:46   true colour: max r 255 g 255 b 255, shift r 16 g 8 b 0
06/11/2014 19:40:46 no translation needed
06/11/2014 19:40:46 Using image quality level 6 for client 192.168.0.248
06/11/2014 19:40:46 Using JPEG subsampling 0, Q79 for client 192.168.0.248
06/11/2014 19:40:46 rfbProcessClientNormalMessage: ignoring unsupported encoding type zlibhex
06/11/2014 19:40:46 rfbProcessClientNormalMessage: ignoring unsupported encoding type Enc(0xFFFFFECD)
06/11/2014 19:40:46 Enabling LastRect protocol extension for client 192.168.0.248
06/11/2014 19:40:46 Enabling NewFBSize protocol extension for client 192.168.0.248
06/11/2014 19:40:46 Enabling cursor position updates for client 192.168.0.248
06/11/2014 19:40:46 Enabling full-color cursor updates for client 192.168.0.248
06/11/2014 19:40:46 Using ZRLE encoding for client 192.168.0.248
06/11/2014 19:40:46 client 1 network rate 1148.2 KB/sec (76730.6 eff KB/sec)
06/11/2014 19:40:46 client 1 latency:  11.9 ms
06/11/2014 19:40:46 dt1: 0.0626, dt2: 0.0635 dt3: 0.0119 bytes: 137931
06/11/2014 19:40:46 link_rate: LR_UNKNOWN - 11 ms, 1148 KB/s
06/11/2014 19:40:47 client useCopyRect: 192.168.0.248 -1
06/11/2014 19:40:47 client_set_net: 192.168.0.248  0.0020
06/11/2014 19:40:47 created   xdamage object: 0x2000040
06/11/2014 19:40:54 copy_tiles: allocating first_line at size 61
06/11/2014 19:40:55 created selwin: 0x2000041
06/11/2014 19:40:55 called initialize_xfixes()
06/11/2014 19:40:56 client_count: 0
06/11/2014 19:40:56 Restored X server key autorepeat to: 1
06/11/2014 19:40:56 Client 192.168.0.248 gone
06/11/2014 19:40:56 Statistics             events    Transmit/ RawEquiv ( saved)
06/11/2014 19:40:56  FramebufferUpdate   :     10 |         0/        0 (  0.0%)
06/11/2014 19:40:56  ZRLE                :     11 |    138029/  9350788 ( 98.5%)
06/11/2014 19:40:56  RichCursor          :      1 |      1374/     1374 (  0.0%)
06/11/2014 19:40:56  TOTALS              :     22 |    139403/  9352162 ( 98.5%)
06/11/2014 19:40:56 Statistics             events    Received/ RawEquiv ( saved)
06/11/2014 19:40:56  KeyEvent            :      6 |        48/       48 (  0.0%)
06/11/2014 19:40:56  PointerEvent        :    193 |      1158/     1158 (  0.0%)
06/11/2014 19:40:56  FramebufferUpdate   :     12 |       120/      120 (  0.0%)
06/11/2014 19:40:56  SetEncodings        :      1 |        64/       64 (  0.0%)
06/11/2014 19:40:56  SetPixelFormat      :      1 |        20/       20 (  0.0%)
06/11/2014 19:40:56  TOTALS              :    213 |      1410/     1410 (  0.0%)
06/11/2014 19:40:56 destroyed xdamage object: 0x2000040
06/11/2014 17:08:56 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:08:56 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:08:58 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:08:58 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:00 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:00 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:02 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:02 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:04 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:04 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:06 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:06 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:08 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:08 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:10 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:10 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:12 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:12 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:14 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:14 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:16 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:16 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:18 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:18 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:20 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:20 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:22 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:22 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:24 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:24 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:26 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:26 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:28 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:28 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:30 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:30 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:32 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:32 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:09:32 active keyboard: last such message for 600 secs.
06/11/2014 17:19:32 active keyboard: waiting until all keys are up. key_down=13 4.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'
06/11/2014 17:19:32 active keyboard: waiting until all keys are up. key_down=113 Left.  If the key is inaccessible via keyboard, consider 'x11vnc -R clear_all'

---

