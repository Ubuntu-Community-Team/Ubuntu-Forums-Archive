---
title: "How to remap the keys with a higher code 255 without /lib/udev/keymap ?"
date: 2013-10-19
forum: General Help
---

### Post by hizo on 2013-10-19
Hi , sorry for my english, I will try to explain my problem...

Many applications doesn't work with high (> 255) key code (like the key configuration in kde, xev or other applications...), so I remapped the keys.

Before Saucy, I changed the special keys of my keyboard with /lib/udev/keymap like this :

1) Keys identification :
```
sudo /lib/udev/keymap input/event3
> scan code: 0xC1021   key code: zoomreset => 100%
> scan code: 0xC101F   key code: zoomin => zoom -
> scan code: 0xC1020   key code: zoomout => zoom +
> scan code: 0xC0192   key code: calc => calculator

```

2) Choose keys name available in /usr/include/linux/input.h file :
```
define KEY_PHONE       169
define KEY_SPORT       220
define KEY_SHOP        221
define KEY_WWW         150

```

3) Remap keyx with /lib/udev/keymap :
```
sudo /lib/udev/keymap input/event3 0xC1021 phone
sudo /lib/udev/keymap input/event3 0xC101F sport
sudo /lib/udev/keymap input/event3 0xC1020 shop
sudo /lib/udev/keymap input/event3 0xC0192 www

```


**It was great, simply and quick... but it was before...**


Now :
1) Keys identification :
/lib/udev/keymap no longer exists.

So I use evtest as indicated by 60-keyboard.hwdb file.

So with evtest :
```
sudo evtest /dev/input/event3 
Input driver version is 1.0.1
Input device ID: bus 0x3 vendor 0x46d product 0xc517 version 0x110
Input device name: "Logitech USB Receiver"
Supported events:
  Event type 0 (EV_SYN)
  Event type 1 (EV_KEY)
    Event code 1 (KEY_ESC)
    Event code 28 (KEY_ENTER)
    Event code 74 (KEY_KPMINUS)
    Event code 78 (KEY_KPPLUS)
    Event code 103 (KEY_UP)
    Event code 105 (KEY_LEFT)
    Event code 106 (KEY_RIGHT)
    Event code 108 (KEY_DOWN)
    Event code 110 (KEY_INSERT)
    Event code 111 (KEY_DELETE)
    Event code 113 (KEY_MUTE)
    Event code 114 (KEY_VOLUMEDOWN)
    Event code 115 (KEY_VOLUMEUP)
    Event code 116 (KEY_POWER)
    Event code 119 (KEY_PAUSE)
    Event code 128 (KEY_STOP)
    Event code 130 (KEY_PROPS)
    Event code 131 (KEY_UNDO)
    Event code 133 (KEY_COPY)
    Event code 134 (KEY_OPEN)
    Event code 135 (KEY_PASTE)
    Event code 136 (KEY_FIND)
    Event code 137 (KEY_CUT)
    Event code 138 (KEY_HELP)
    Event code 139 (KEY_MENU)
    Event code 140 (KEY_CALC)
    Event code 142 (KEY_SLEEP)
    Event code 143 (KEY_WAKEUP)
    Event code 144 (KEY_FILE)
    Event code 148 (KEY_PROG1)
    Event code 149 (KEY_PROG2)
    Event code 150 (KEY_WWW)
    Event code 152 (KEY_SCREENLOCK)
    Event code 154 (KEY_CYCLEWINDOWS)
    Event code 155 (KEY_MAIL)
    Event code 156 (KEY_BOOKMARKS)
    Event code 158 (KEY_BACK)
    Event code 159 (KEY_FORWARD)
    Event code 161 (KEY_EJECTCD)
    Event code 162 (KEY_EJECTCLOSECD)
    Event code 163 (KEY_NEXTSONG)
    Event code 164 (KEY_PLAYPAUSE)
    Event code 165 (KEY_PREVIOUSSONG)
    Event code 166 (KEY_STOPCD)
    Event code 167 (KEY_RECORD)
    Event code 168 (KEY_REWIND)
    Event code 169 (KEY_PHONE)
    Event code 172 (KEY_HOMEPAGE)
    Event code 173 (KEY_REFRESH)
    Event code 174 (KEY_EXIT)
    Event code 176 (KEY_EDIT)
    Event code 177 (KEY_SCROLLUP)
    Event code 178 (KEY_SCROLLDOWN)
    Event code 181 (KEY_NEW)
    Event code 182 (KEY_REDO)
    Event code 202 (KEY_PROG3)
    Event code 203 (KEY_PROG4)
    Event code 206 (KEY_CLOSE)
    Event code 207 (KEY_PLAY)
    Event code 208 (KEY_FASTFORWARD)
    Event code 209 (KEY_BASSBOOST)
    Event code 210 (KEY_PRINT)
    Event code 212 (KEY_CAMERA)
    Event code 213 (KEY_SOUND)
    Event code 216 (KEY_CHAT)
    Event code 217 (KEY_SEARCH)
    Event code 219 (KEY_FINANCE)
    Event code 223 (KEY_CANCEL)
    Event code 226 (KEY_MEDIA)
    Event code 228 (KEY_KBDILLUMTOGGLE)
    Event code 231 (KEY_SEND)
    Event code 232 (KEY_REPLY)
    Event code 233 (KEY_FORWARDMAIL)
    Event code 234 (KEY_SAVE)
    Event code 235 (KEY_DOCUMENTS)
    Event code 241 (KEY_VIDEO_NEXT)
    Event code 256 (BTN_0)
    Event code 272 (BTN_LEFT)
    Event code 273 (BTN_RIGHT)
    Event code 274 (BTN_MIDDLE)
    Event code 275 (BTN_SIDE)
    Event code 276 (BTN_EXTRA)
    Event code 277 (BTN_FORWARD)
    Event code 278 (BTN_BACK)
    Event code 279 (BTN_TASK)
    Event code 352 (KEY_OK)
    Event code 353 (KEY_SELECT)
    Event code 354 (KEY_GOTO)
    Event code 358 (KEY_INFO)
    Event code 362 (KEY_PROGRAM)
    Event code 366 (KEY_PVR)
    Event code 370 (KEY_SUBTITLE)
    Event code 371 (KEY_ANGLE)
    Event code 372 (KEY_ZOOM)
    Event code 374 (KEY_KEYBOARD)
    Event code 376 (KEY_PC)
    Event code 377 (KEY_TV)
    Event code 378 (KEY_TV2)
    Event code 379 (KEY_VCR)
    Event code 380 (KEY_VCR2)
    Event code 381 (KEY_SAT)
    Event code 383 (KEY_CD)
    Event code 384 (KEY_TAPE)
    Event code 386 (KEY_TUNER)
    Event code 387 (KEY_PLAYER)
    Event code 389 (KEY_DVD)
    Event code 392 (KEY_AUDIO)
    Event code 393 (KEY_VIDEO)
    Event code 396 (KEY_MEMO)
    Event code 397 (KEY_CALENDAR)
    Event code 398 (KEY_RED)
    Event code 399 (KEY_GREEN)
    Event code 400 (KEY_YELLOW)
    Event code 401 (KEY_BLUE)
    Event code 402 (KEY_CHANNELUP)
    Event code 403 (KEY_CHANNELDOWN)
    Event code 405 (KEY_LAST)
    Event code 408 (KEY_RESTART)
    Event code 409 (KEY_SLOW)
    Event code 410 (KEY_SHUFFLE)
    Event code 416 (KEY_VIDEOPHONE)
    Event code 417 (KEY_GAMES)
    Event code 418 (KEY_ZOOMIN)
    Event code 419 (KEY_ZOOMOUT)
    Event code 420 (KEY_ZOOMRESET)
    Event code 421 (KEY_WORDPROCESSOR)
    Event code 422 (KEY_EDITOR)
    Event code 423 (KEY_SPREADSHEET)
    Event code 424 (KEY_GRAPHICSEDITOR)
    Event code 425 (KEY_PRESENTATION)
    Event code 426 (KEY_DATABASE)
    Event code 427 (KEY_NEWS)
    Event code 428 (KEY_VOICEMAIL)
    Event code 429 (KEY_ADDRESSBOOK)
    Event code 430 (KEY_MESSENGER)
    Event code 432 (KEY_SPELLCHECK)
    Event code 433 (KEY_LOGOFF)
    Event code 439 (KEY_MEDIA_REPEAT)
    Event code 442 (?)
    Event code 478 (KEY_FN_1)
    Event code 479 (KEY_FN_2)
  Event type 2 (EV_REL)
    Event code 0 (REL_X)
    Event code 1 (REL_Y)
    Event code 6 (REL_HWHEEL)
    Event code 7 (REL_DIAL)
    Event code 8 (REL_WHEEL)
  Event type 3 (EV_ABS)
    Event code 32 (ABS_VOLUME)
      Value      0
      Min        1
      Max     4173
  Event type 4 (EV_MSC)
    Event code 4 (MSC_SCAN)
Properties:
Testing ... (interrupt to exit)
> Event: time 1381940761.592647, type 1 (EV_KEY), code 140 (KEY_CALC), value 1 => calculator
> Event: time 1381940790.224658, type 1 (EV_KEY), code 420 (KEY_ZOOMRESET), value 1 => 100%
> Event: time 1381940810.928667, type 1 (EV_KEY), code 419 (KEY_ZOOMOUT), value 1 => Zoom -
> Event: time 1381940836.216678, type 1 (EV_KEY), code 418 (KEY_ZOOMIN), value 1 => Zoom +

```


**But my big problem is : How to remap key simply ?!!**


I tested many things...

xinput list return :
```
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                     id=10   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Power Button                              id=7    [slave  keyboard (3)]
    &#8627; STV06xx                                   id=8    [slave  keyboard (3)]
    &#8627; Logitech USB Receiver                     id=9    [slave  keyboard (3)]

```


ir-keytable doesn't work :
```
/sys/class/rc/: No such file or directory

```


I tryed to add this code in /lib/udev/hwdb.d/60-keyboard.hwdb :
```
 # Cordless Desktop S520
keyboard:usb:v046DpC517*
 KEYBOARD_KEY_XXX=www
 KEYBOARD_KEY_XXX=phone
 KEYBOARD_KEY_XXX=sport
 KEYBOARD_KEY_XXX=shop

```Where XXX are codes of evtest or keymap... reboot... and... nothing....

I tested xmodmap :
```
xmodmap -e "keycode 420 = XF86WWW"
```
Doesn't work with code > 255...


I tested [http://www.thenautilus.net/SW/xf86-input-evdev/](http://www.thenautilus.net/SW/xf86-input-evdev/) but I haven't xorg file...


**It's possible ? Or am I the problem ?!!**


Thank you very much for reading this and I hope you have solutions for my request...

---

### Post by hizo on 2013-10-20
I have changed my question and my explications : **How to remap the keys with a higher code 255**.

---

### Post by hizo on 2013-10-20
After many search, I found !!!

Thank you very much at [Daniel Klaffenbach]("http://www-user.tu-chemnitz.de/~klada/?site=projects&id=logitechkbd") !!

So :
1) Install [evrouter]("http://www.bedroomlan.org/projects/evrouter")


2) Add a rule to allow users to read [COLOR=#000000][FONT=Verdana]/dev/input/event*
[/FONT][/COLOR]```
echo 'KERNEL=="event*", NAME="input/%k", GROUP="input" | sudo tee /etc/udev/rules.d/80-evrouter.rules
```

Create the input group
```
sudo addgroup input
```

Add this group at the user
```
sudo usermod -aG input ${USER}
```


3) Reboot the system
```
sudo reboot
```


4) Keys identification, choose the good input, eg :
```
evtest
> Available devices:
> /dev/input/event0:      Power Button
> /dev/input/event1:      Power Button
> /dev/input/event2:      Logitech USB Receiver
> /dev/input/event3:      Logitech USB Receiver
> /dev/input/event4:      Sony PLAYSTATION(R)3 Controller
> /dev/input/event5:      STV06xx
> /dev/input/event6:      HDA ATI HDMI HDMI/DP,pcm=3
Select the device event number [0-6]: 3

```

Press the keys to configure, eg:
```
> Event: time 1381940761.592647, type 1 (EV_KEY), code 140 (KEY_CALC), value 1 => calculator
> Event: time 1381940790.224658, type 1 (EV_KEY), code 420 (KEY_ZOOMRESET), value 1 => 100%
> Event: time 1381940810.928667, type 1 (EV_KEY), code 419 (KEY_ZOOMOUT), value 1 => Zoom -
> Event: time 1381940836.216678, type 1 (EV_KEY), code 418 (KEY_ZOOMIN), value 1 => Zoom +

```


5) Create a evrouter file config (${HOME}/.evrouterrc):
```
"Name of your event" "event link" none key/Number_your_key "XKey/Name_your_key"
```

my config file :
```
#Zoom +
"Logitech USB Receiver" "/dev/input/event3" none key/418 "XKey/XF86ZoomIn"

#Zoom -
"Logitech USB Receiver" "/dev/input/event3" none key/419 "XKey/XF86ZoomOut"

# Zoom Rest => XF86ZoomReset[COLOR=#000000][FONT=Verdana] u[/FONT][/COLOR]nknow, so I use other key
"Logitech USB Receiver" "/dev/input/event3" none key/420 "XKey/XF86Phone"
```

List of names of keys :
```
XF86AddFavoriteXF86ApplicationLeft
XF86ApplicationRight
XF86AudioMedia
XF86AudioMute
XF86AudioNext
XF86AudioPause
XF86AudioPlay
XF86AudioPrev
XF86AudioLowerVolume
XF86AudioRaiseVolume
XF86AudioRecord
XF86AudioRewind
XF86AudioStop
XF86Away
XF86Back
XF86Book
XF86BrightnessAdjust
XF86CD
XF86Calculator
XF86Calendar
XF86Clear
XF86ClearGrab
XF86Close
XF86Community
XF86ContrastAdjust
XF86Copy
XF86Cut
XF86DOS
XF86Display
XF86Documents
XF86Eject
XF86Excel
XF86Explorer
XF86Favorites
XF86Finance
XF86Forward
XF86Game
XF86Go
XF86History
XF86HomePage
XF86HotLinks
XF86Launch0
XF86Launch1
XF86Launch2
XF86Launch3
XF86Launch4
XF86Launch5
XF86Launch6
XF86Launch7
XF86Launch8
XF86Launch9
XF86LaunchA
XF86LaunchB
XF86LaunchC
XF86LaunchD
XF86LaunchE
XF86LaunchF
XF86LightBulb
XF86LogOff
XF86Mail
XF86MailForward
XF86Market
XF86Meeting
XF86Memo
XF86MenuKB
XF86MenuPB
XF86Messenger
XF86Music
XF86MyComputer
XF86MySites
XF86New
XF86News
XF86Next_VMode
XF86Prev_VMode
XF86OfficeHome
XF86Open
XF86OpenURL
XF86Option
XF86Paste
XF86Phone
XF86Pictures
XF86PowerDown
XF86PowerOff
XF86Next_VMode
XF86Prev_VMode
XF86Q
XF86Refresh
XF86Reload
XF86Reply
XF86RockerDown
XF86RockerEnter
XF86RockerUp
XF86RotateWindows
XF86RotationKB
XF86RotationPB
XF86Save
XF86ScreenSaver
XF86ScrollClick
XF86ScrollDown
XF86ScrollUp
XF86Search
XF86Send
XF86Shop
XF86Sleep
XF86Spell
XF86SplitScreen
XF86Standby
XF86Start
XF86Stop
XF86Support
XF86Switch_VT_1
XF86Switch_VT_10
XF86Switch_VT_11
XF86Switch_VT_12
XF86Switch_VT_2
XF86Switch_VT_3
XF86Switch_VT_4
XF86Switch_VT_5
XF86Switch_VT_6
XF86Switch_VT_7
XF86Switch_VT_8
XF86Switch_VT_9
XF86TaskPane
XF86Terminal
XF86ToDoList
XF86Tools
XF86Travel
XF86Ungrab
XF86User1KB
XF86User2KB
XF86UserPB
XF86VendorHome
XF86Video
XF86WWW
XF86WakeUp
XF86WebCam
XF86WheelButton
XF86Word
XF86XF86BackForward
XF86Xfer
XF86ZoomIn
XF86ZoomOut
XF86iTouch
```


6) Look the keys free with xmodmap, eg:
```
xmodmap -pke | egrep "=$"
> keycode 250 =
> keycode 251 =
> keycode 252 =

```


7) Create a xmodmap file config (${HOME}/.xmodmap):

```
keycode Number_key_free = Name_your_key
```

my config file :
```
# calculator doesn't work so at home, so I remap  him
keycode 148 = XF86WWW

#Zoom -
keycode 251 = XF86ZoomOut

#Zoom +
keycode 250 = XF86ZoomIn

# Zoom Rest
keycode 252 = XF86Phone

```


8) Execute the softwares :
```
xmodmap ~/.xmodmap
evrouter /dev/input/event3
```


9) Check the remap with xev, eg :
```
xev

=> Eg, when I click in ZoomReset key
> KeyRelease event, serial 43, synthetic NO, window 0x5c00001,
>    root 0x2c3, subw 0x0, time 2637741, (-472,493), root:(476,516),
>    state 0x10, keycode 177 (keysym 0x1008ff6e, XF86Phone), same_screen YES,
>    XLookupString gives 0 bytes: 
>    XFilterEvent returns: False

```


10) If all is good, create a auto start, eg in Kubuntu (${HOME}/.kde/Autostart/keys) :
```
#!/bin/sh
xmodmap ~/.xmodmap
evrouter /dev/input/event3


```

---

