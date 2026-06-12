---
title: "Lirc and some unknown chinese remote?"
date: 2008-04-08
forum: General Help
---

### Post by Povilas on 2008-04-08
I've recently gotten my hands on [one of these](http://computer.category.madeinchina.com/1822482/P4421652/Media-Center-PC-Remote-Controller.shtml). I was unable find out anything else about this remote other than 'Compatible with Microsoft-Philips IR Protocol'. Well, I installed LIRC, selected 'Windows Media Center Remotes (new version Philips et al.)' and got /dev/lircd. However, no matter what I do, I am unable to get /dev/lirc (also known as /dev/lirc0 or /dev/lirc/0). Any ideas?

---

### Post by jonlowe on 2008-04-10
I have the sameremote.  Go to Applications>Add/Remove and search for Infrared Remote Control.  Add that applicaton.  Got to System>Administrion>Infrared Remote Control.  In the window that comes up, select Auto-detect under IR-Receiver.  If your receiver was plugged in, it should find CypSe Withehome as the model.  Punch some buttons on the remote, and they should show up in the lower part of the box.  If you want to do custom key mappings, click on "Use diifferent remote control", and select Custom Configuration.

Note that this only does the front end of lirc, ie, getting lirc to recongnize your remote.  It doesn't set up the interface between those codes and your application that you want to control.  What is needed is something that takes the mappings of what this app does, and make custom .lirc files for common apps such as VLC or Totem, and then install them in the system.  This new app does half the job, but it takes a lot of work out of setting up the remote.

Jon

---

### Post by Povilas on 2008-04-10
Thanks for the hint. I discovered that this remote uses /dev/input/eventX interface for receiving signals. From there it was pretty straightforward.

Oh, if you don't mind, could you share /etc/lirc/lircd.conf file with me? I am having trouble configuring some buttons.

---

### Post by jonlowe on 2008-04-10
Unfortunately, I haven't gotten that far yet.  I'm a newbie to Ubuntu and Linux, and I discovered this by pretty much accident while trying, as yet unsuccessfully, to set up an MCE remote.  I'm close, but not there yet.  If you get it to work, please let me know how!

Jon

---

### Post by Povilas on 2008-04-11
I can use it without lircd configuration - the arrows reflect keyboard arrows, numbers reflect keyboard numbers, etc. To configure the remote properly (I think) I need a lircd.conf file with button values recorded. I have tried multiple times and most buttons (e.g. 'play' to 'forward') get detected as one button. So I can bind them all to only one action. If you have all the buttons working, could you share /etc/lirc/lircd.conf with me? (simply open the file in text editor and paste it's contents here)

---

### Post by aie93 on 2008-04-11
I got one of these remotes today and have spent most of the day reading code and Googling different things.  As far as I understand it the kernel has decided that the remote is a keyboard, and short of writing a USB HID driver for lirc (which I did consider earlier) which would read from /dev/hidraw0 (someone should write one of these soon!) I realised that every key was unique.

I couldn't get the "Media Center" button to work, it does output to the hidraw0 device, but the USB HID driver doesn't interpret it for some reason.

So, anyways I read about using input devices in lircd.conf and made up a conf file, so far I have not figured out if you can detect modifiers (i.e. CTRL + SHIFT) on a key press which renders the Repeat, Pause and Skip Forward buttons useless for now.  But here is my lircd.conf file which lets everything else work, and it's working for me here right now :D.

If anyone knows about this modifiers issue PLEASE do tell me!

```
begin remote
	name Cypress-Semiconductor-Corp
	bits 32
	begin codes
		POWER		0x10074
		RADIO		0x1001e
		TV		0x10014
		DVD		0x10031
		MUSIC		0x10032
		PHOTO		0x10017
		VIDEO		0x10012
		DVD_MENU	0x1002f

		CHAN_UP		0x10068
		CHAN_DOWN	0x1006d
		VOLUME_DOWN	0x10072
		VOLUME_UP	0x10073
		MUTE		0x10042
		ENTER		0x1001c
		LEFT		0x10069
		RIGHT		0x1006a
		UP		0x10067
		DOWN		0x1006c

		1		0x10002
		2		0x10003
		3		0x10004
		4		0x10005
		5		0x10006
		6		0x10007
		7		0x10008
		8		0x10009
		9		0x1000a
		0		0x1000b

		BACK		0x1000e
		GUIDE		0x1003b

		RECORD		0x10013
#		REPEAT		0x10013
		PLAY		0x10019
#		PAUSE		0x10019
		STOP		0x1001f
		REWIND		0x10020
		FFWD		0x10021
		SKIP_BACK	0x10030
#		SKIP_FWD	0x10021
	end codes
end remote

```

---

### Post by Povilas on 2008-04-12
Thanks, aie93. You definitely got much further than I did.

I'll see if I can find out something regarding modifiers, will post here if I do.

EDIT:
I've found this config file:
[http://linux.bytesex.org/v4l2/linux-input-layer-lircd.conf](http://linux.bytesex.org/v4l2/linux-input-layer-lircd.conf)

Looks like it utilizes modifiers:
> 
*# Play*
000000000001001d 00 LEFTCTRL linux-input-layer
000000000001002a 00 LEFTSHIFT linux-input-layer
0000000000010019 00 P linux-input-layer
*# Pause*
000000000001001d 00 LEFTCTRL linux-input-layer
0000000000010019 00 P linux-input-layer


---

### Post by Povilas on 2008-04-13
OK, I think I figured it out.

You cannot define modifier-keypress pairs in lircd.conf, however you can bind those pairs in .lircrc to various actions. Here's how:

**1.** Download [this lircd.conf](http://linux.bytesex.org/v4l2/linux-input-layer-lircd.conf) and save it as */etc/lirc/lircd.conf* . This will make all the buttons on the remote work (except 'Media Center' anyway).
**2.** Run *irw* on the console.
**3.** Now, press any button on the remote. For example if I press *Play* I get the following output:
> 
000000000001001d 00 **LEFTCTRL** linux-input-layer
000000000001002a 00 **LEFTSHIFT** linux-input-layer
0000000000010019 00 **P** linux-input-layer

**4.** Lirc recognized a series of buttons from one keypress: LEFTCTRL, LEFTSHIFT, P
**5.** Open *~/.lircrc* with text editor and bind some action to the keypress sequence. You can do this by adding multiple *button* fields. For example if I want to simulate a spacebar keypress when I press play, I would configure the key as follows:
> 
begin
    prog = irxevent
    button = LEFTCTRL 
    button = LEFTSHIFT 
    button = P
    config = Key KP_Space CurrentWindow
end

(irxevent has to be started manually to work. To do this, issue *irxevent -d* in console. If you are unsure where 'KP_Space' came from, check */usr/share/doc/lirc/irxevent.keys*)
**6.** Finally, kill any lirc frontend you have running (e.g. irkick) and run *lircrcd ~/.lircrc*

It's not perfect, but at least this way you can bind remote buttons to anything you want.

EDIT: Oh darn. Just as I have finally got it working the way I wanted, the remote had to fall down and stop working.

---

### Post by kadafi69 on 2008-05-24
your link to the lircd.conf doesnt work, could you send me a copy of the file as im trying to get this remote to work.

---

### Post by Povilas on 2008-05-24
> **kadafi69 said:**
> your link to the lircd.conf doesnt work, could you send me a copy of the file as im trying to get this remote to work.

It's here: [http://linux.bytesex.org/v4l2/linux-input-layer-lircd.conf](http://linux.bytesex.org/v4l2/linux-input-layer-lircd.conf)
For some reason the link in my post messed up.

```
begin remote
	name linux-input-layer
	bits 32
	begin codes
		ESC                  0x10001
		1                    0x10002
		2                    0x10003
		3                    0x10004
		4                    0x10005
		5                    0x10006
		6                    0x10007
		7                    0x10008
		8                    0x10009
		9                    0x1000a
		0                    0x1000b
		MINUS                0x1000c
		EQUAL                0x1000d
		BACKSPACE            0x1000e
		TAB                  0x1000f
		Q                    0x10010
		W                    0x10011
		E                    0x10012
		R                    0x10013
		T                    0x10014
		Y                    0x10015
		U                    0x10016
		I                    0x10017
		O                    0x10018
		P                    0x10019
		LEFTBRACE            0x1001a
		RIGHTBRACE           0x1001b
		ENTER                0x1001c
		LEFTCTRL             0x1001d
		A                    0x1001e
		S                    0x1001f
		D                    0x10020
		F                    0x10021
		G                    0x10022
		H                    0x10023
		J                    0x10024
		K                    0x10025
		L                    0x10026
		SEMICOLON            0x10027
		APOSTROPHE           0x10028
		GRAVE                0x10029
		LEFTSHIFT            0x1002a
		BACKSLASH            0x1002b
		Z                    0x1002c
		X                    0x1002d
		C                    0x1002e
		V                    0x1002f
		B                    0x10030
		N                    0x10031
		M                    0x10032
		COMMA                0x10033
		DOT                  0x10034
		SLASH                0x10035
		RIGHTSHIFT           0x10036
		KPASTERISK           0x10037
		LEFTALT              0x10038
		SPACE                0x10039
		CAPSLOCK             0x1003a
		F1                   0x1003b
		F2                   0x1003c
		F3                   0x1003d
		F4                   0x1003e
		F5                   0x1003f
		F6                   0x10040
		F7                   0x10041
		F8                   0x10042
		F9                   0x10043
		F10                  0x10044
		NUMLOCK              0x10045
		SCROLLLOCK           0x10046
		KP7                  0x10047
		KP8                  0x10048
		KP9                  0x10049
		KPMINUS              0x1004a
		KP4                  0x1004b
		KP5                  0x1004c
		KP6                  0x1004d
		KPPLUS               0x1004e
		KP1                  0x1004f
		KP2                  0x10050
		KP3                  0x10051
		KP0                  0x10052
		KPDOT                0x10053
		103RD                0x10054
		F13                  0x10055
		102ND                0x10056
		F11                  0x10057
		F12                  0x10058
		F14                  0x10059
		F15                  0x1005a
		F16                  0x1005b
		F17                  0x1005c
		F18                  0x1005d
		F19                  0x1005e
		F20                  0x1005f
		KPENTER              0x10060
		RIGHTCTRL            0x10061
		KPSLASH              0x10062
		SYSRQ                0x10063
		RIGHTALT             0x10064
		LINEFEED             0x10065
		HOME                 0x10066
		UP                   0x10067
		PAGEUP               0x10068
		LEFT                 0x10069
		RIGHT                0x1006a
		END                  0x1006b
		DOWN                 0x1006c
		PAGEDOWN             0x1006d
		INSERT               0x1006e
		DELETE               0x1006f
		MACRO                0x10070
		MUTE                 0x10071
		VOLUMEDOWN           0x10072
		VOLUMEUP             0x10073
		POWER                0x10074
		KPEQUAL              0x10075
		KPPLUSMINUS          0x10076
		PAUSE                0x10077
		F21                  0x10078
		F22                  0x10079
		F23                  0x1007a
		F24                  0x1007b
		KPCOMMA              0x1007c
		LEFTMETA             0x1007d
		RIGHTMETA            0x1007e
		COMPOSE              0x1007f
		STOP                 0x10080
		AGAIN                0x10081
		PROPS                0x10082
		UNDO                 0x10083
		FRONT                0x10084
		COPY                 0x10085
		OPEN                 0x10086
		PASTE                0x10087
		FIND                 0x10088
		CUT                  0x10089
		HELP                 0x1008a
		MENU                 0x1008b
		CALC                 0x1008c
		SETUP                0x1008d
		SLEEP                0x1008e
		WAKEUP               0x1008f
		FILE                 0x10090
		SENDFILE             0x10091
		DELETEFILE           0x10092
		XFER                 0x10093
		PROG1                0x10094
		PROG2                0x10095
		WWW                  0x10096
		MSDOS                0x10097
		COFFEE               0x10098
		DIRECTION            0x10099
		CYCLEWINDOWS         0x1009a
		MAIL                 0x1009b
		BOOKMARKS            0x1009c
		COMPUTER             0x1009d
		BACK                 0x1009e
		FORWARD              0x1009f
		CLOSECD              0x100a0
		EJECTCD              0x100a1
		EJECTCLOSECD         0x100a2
		NEXTSONG             0x100a3
		PLAYPAUSE            0x100a4
		PREVIOUSSONG         0x100a5
		STOPCD               0x100a6
		RECORD               0x100a7
		REWIND               0x100a8
		PHONE                0x100a9
		ISO                  0x100aa
		CONFIG               0x100ab
		HOMEPAGE             0x100ac
		REFRESH              0x100ad
		EXIT                 0x100ae
		MOVE                 0x100af
		EDIT                 0x100b0
		SCROLLUP             0x100b1
		SCROLLDOWN           0x100b2
		KPLEFTPAREN          0x100b3
		KPRIGHTPAREN         0x100b4
		INTL1                0x100b5
		INTL2                0x100b6
		INTL3                0x100b7
		INTL4                0x100b8
		INTL5                0x100b9
		INTL6                0x100ba
		INTL7                0x100bb
		INTL8                0x100bc
		INTL9                0x100bd
		LANG1                0x100be
		LANG2                0x100bf
		LANG3                0x100c0
		LANG4                0x100c1
		LANG5                0x100c2
		LANG6                0x100c3
		LANG7                0x100c4
		LANG8                0x100c5
		LANG9                0x100c6
		PLAYCD               0x100c8
		PAUSECD              0x100c9
		PROG3                0x100ca
		PROG4                0x100cb
		SUSPEND              0x100cd
		CLOSE                0x100ce
		PLAY                 0x100cf
		FASTFORWARD          0x100d0
		BASSBOOST            0x100d1
		PRINT                0x100d2
		HP                   0x100d3
		CAMERA               0x100d4
		SOUND                0x100d5
		QUESTION             0x100d6
		EMAIL                0x100d7
		CHAT                 0x100d8
		SEARCH               0x100d9
		CONNECT              0x100da
		FINANCE              0x100db
		SPORT                0x100dc
		SHOP                 0x100dd
		ALTERASE             0x100de
		CANCEL               0x100df
		BRIGHTNESSDOWN       0x100e0
		BRIGHTNESSUP         0x100e1
		MEDIA                0x100e2
		UNKNOWN              0x100f0
		BTN_MISC             0x10100
		BTN_0                0x10100
		BTN_1                0x10101
		BTN_2                0x10102
		BTN_3                0x10103
		BTN_4                0x10104
		BTN_5                0x10105
		BTN_6                0x10106
		BTN_7                0x10107
		BTN_8                0x10108
		BTN_9                0x10109
		BTN_MOUSE            0x10110
		BTN_LEFT             0x10110
		BTN_RIGHT            0x10111
		BTN_MIDDLE           0x10112
		BTN_SIDE             0x10113
		BTN_EXTRA            0x10114
		BTN_FORWARD          0x10115
		BTN_BACK             0x10116
		BTN_TASK             0x10117
		BTN_JOYSTICK         0x10120
		BTN_TRIGGER          0x10120
		BTN_THUMB            0x10121
		BTN_THUMB2           0x10122
		BTN_TOP              0x10123
		BTN_TOP2             0x10124
		BTN_PINKIE           0x10125
		BTN_BASE             0x10126
		BTN_BASE2            0x10127
		BTN_BASE3            0x10128
		BTN_BASE4            0x10129
		BTN_BASE5            0x1012a
		BTN_BASE6            0x1012b
		BTN_DEAD             0x1012f
		BTN_GAMEPAD          0x10130
		BTN_A                0x10130
		BTN_B                0x10131
		BTN_C                0x10132
		BTN_X                0x10133
		BTN_Y                0x10134
		BTN_Z                0x10135
		BTN_TL               0x10136
		BTN_TR               0x10137
		BTN_TL2              0x10138
		BTN_TR2              0x10139
		BTN_SELECT           0x1013a
		BTN_START            0x1013b
		BTN_MODE             0x1013c
		BTN_THUMBL           0x1013d
		BTN_THUMBR           0x1013e
		BTN_DIGI             0x10140
		BTN_TOOL_PEN         0x10140
		BTN_TOOL_RUBBER      0x10141
		BTN_TOOL_BRUSH       0x10142
		BTN_TOOL_PENCIL      0x10143
		BTN_TOOL_AIRBRUSH    0x10144
		BTN_TOOL_FINGER      0x10145
		BTN_TOOL_MOUSE       0x10146
		BTN_TOOL_LENS        0x10147
		BTN_TOUCH            0x1014a
		BTN_STYLUS           0x1014b
		BTN_STYLUS2          0x1014c
		BTN_WHEEL            0x10150
		BTN_GEAR_DOWN        0x10150
		BTN_GEAR_UP          0x10151
		OK                   0x10160
		SELECT               0x10161
		GOTO                 0x10162
		CLEAR                0x10163
		POWER2               0x10164
		OPTION               0x10165
		INFO                 0x10166
		TIME                 0x10167
		VENDOR               0x10168
		ARCHIVE              0x10169
		PROGRAM              0x1016a
		CHANNEL              0x1016b
		FAVORITES            0x1016c
		EPG                  0x1016d
		PVR                  0x1016e
		MHP                  0x1016f
		LANGUAGE             0x10170
		TITLE                0x10171
		SUBTITLE             0x10172
		ANGLE                0x10173
		ZOOM                 0x10174
		MODE                 0x10175
		KEYBOARD             0x10176
		SCREEN               0x10177
		PC                   0x10178
		TV                   0x10179
		TV2                  0x1017a
		VCR                  0x1017b
		VCR2                 0x1017c
		SAT                  0x1017d
		SAT2                 0x1017e
		CD                   0x1017f
		TAPE                 0x10180
		RADIO                0x10181
		TUNER                0x10182
		PLAYER               0x10183
		TEXT                 0x10184
		DVD                  0x10185
		AUX                  0x10186
		MP3                  0x10187
		AUDIO                0x10188
		VIDEO                0x10189
		DIRECTORY            0x1018a
		LIST                 0x1018b
		MEMO                 0x1018c
		CALENDAR             0x1018d
		RED                  0x1018e
		GREEN                0x1018f
		YELLOW               0x10190
		BLUE                 0x10191
		CHANNELUP            0x10192
		CHANNELDOWN          0x10193
		FIRST                0x10194
		LAST                 0x10195
		AB                   0x10196
		NEXT                 0x10197
		RESTART              0x10198
		SLOW                 0x10199
		SHUFFLE              0x1019a
		BREAK                0x1019b
		PREVIOUS             0x1019c
		DIGITS               0x1019d
		TEEN                 0x1019e
		TWEN                 0x1019f
		DEL_EOL              0x101c0
		DEL_EOS              0x101c1
		INS_LINE             0x101c2
		DEL_LINE             0x101c3
	end codes
end remote
```

---

### Post by kadafi69 on 2008-05-24
thanks, only problem is when i run the irw command i get a connection refused error. any ideas on how to resolve this?

---

### Post by Povilas on 2008-05-25
Try restarting lirc. If that doesn't help, you will have to edit /etc/lirc/hardware.conf. Since I no longer have the remote, I will be unable to provide a working hardware.conf.
If I remember correctly, lircd device (REMOTE_DEVICE) is located at /dev/input/event*. To see which one it is, unplug the usb receiver, run 'ls -l /dev/input/event*', plug it back in and run the command again. See which device appears when you plug adapter in.
Also, try googling for 'lirc linux input layer'.

---

