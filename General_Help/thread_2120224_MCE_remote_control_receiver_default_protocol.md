---
title: "MCE remote control receiver default protocol"
date: 2013-02-26
forum: General Help
---

### Post by trits on 2013-02-26
Hi,
 
 My  problem is that after rebooting, I have to manually load the keytable  for my remote control receiver... Here&#8217;s a detailed explanation:
 
 I  am running XBMC on Ubuntu 3.2.0-37-generic-pae and am using my Sony Bravia remote control  with an MCE remote control receiver connected to the computer. I have  created a new keytable called Sony in ~/Documents for the sony remote, with contents: 
 
```
# table rc6_mce, type: SONY
0x9700a6 KEY_C #MEDIA
0x1003a KEY_I
0x9700a5 KEY_APOSTROPHE #CHANNELDOWN
0x97009c KEY_FASTFORWARD
0x97009b KEY_REWIND
0x970099 KEY_PLAY
0x970098 KEY_STOP
0x9700bd KEY_LEFTBRACE #NXT
0x9700bc KEY_RIGHTBRACE #PREVIOUS
0x10074 KEY_UP
0x10075 KEY_DOWN
0x10034 KEY_LEFT
0x10033 KEY_RIGHT
0x10065 KEY_ENTER
0x9700a3 KEY_BACKSPACE
0x9700a8 KEY_L #SUBTITLE
0x97009a KEY_PLAYPAUSE
0x9700a4 KEY_BACKSLASH
0x9700a7 KEY_TAB
```I   use ir-keytable to load this table. This also sets the enabled   protocol. Here is the ir-keytable output after the table is loaded:
 
 ```
Found /sys/class/rc/rc0/ (/dev/input/event3) with:
    Driver mceusb, table rc-rc6-mce
    Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
    Enabled protocols: SONY 
    Repeat delay = 500 ms, repeat period = 125 ms
```Up to this point it all works perfectly. The problem comes when I reboot.

In order to load the above table on startup, I&#8217;ve edited /etc/rc_maps.cfg:
 
 ```
*    rc-rc6-mce               /home/tim/Documents/Sony
```My problem is that after reboot, all protocols are enabled, as follows:
 
 ```
Found /sys/class/rc/rc0/ (/dev/input/event3) with:
    Driver mceusb, table rc-rc6-mce
    Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
    Enabled protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
    Repeat delay = 500 ms, repeat period = 125 ms
```This is strange because any other changes to ~/Documents/Sony are updated after a reboot. Just not the protocol.
 
 With all protocols enabled, something weird seems to be happening. The receiver is seeing some rc-5 events, which seems to make keypresses on the remote repeat several times. This is the ir-keytable -t output for one keypress:

 
 ```
1361856103.046225: event MSC: scancode = 1f3f
1361856103.046226: event sync
1361856103.067218: event MSC: scancode = 9700a3
1361856103.067223: event key down: KEY_BACKSPACE (0x000e)
1361856103.067224: event sync
1361856103.091223: event key up: KEY_BACKSPACE (0x000e)
1361856103.091227: event MSC: scancode = 1f3f
1361856103.091228: event sync
1361856103.112235: event MSC: scancode = 9700a3
1361856103.112241: event key down: KEY_BACKSPACE (0x000e)
1361856103.112242: event sync
1361856103.136242: event key up: KEY_BACKSPACE (0x000e)
1361856103.136246: event MSC: scancode = 1f3f
1361856103.136247: event sync
1361856103.236221: event MSC: scancode = 9700a3
1361856103.236226: event key down: KEY_BACKSPACE (0x000e)
1361856103.236227: event sync
1361856103.485315: event key up: KEY_BACKSPACE (0x000e)
1361856103.485317: event sync
```All the "event MSC: scancode = 1f3f" lines are the rc-5 protocol. When only rc-5 is enabled, all buttons produce the same line.

 
 So, because of all this, after reboot I have to manually load the keymap using ```
ir-keytable -w ~/Documents/Sony
``` or manually change the protocol using ```
ir-keytable -p sony
``` This is what I want to avoid.

 
 I have found this file: /sys/class/rc/rc0/protocols with contents:
 
 ```
[rc-5] [nec] [rc-6] [jvc] [sony] mce_kbd [lirc]
``` I dont really know what it does, but in any case i cannot edit it.
 
 Can someone offer advice on how to set the default protocol to Sony only? Im a bit of a newb so any general explanations would be great.

Thanks!

---

