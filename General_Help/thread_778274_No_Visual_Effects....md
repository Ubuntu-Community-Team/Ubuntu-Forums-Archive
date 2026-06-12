---
title: "No Visual Effects..."
date: 2008-05-01
forum: General Help
---

### Post by UnderRedMountain on 2008-05-01
I've been working with Ubuntu for a month or so now, so I know this is probably a question that has been answered a thousand times... but I can't get desktop effects to work, and I was wondering if anyone could help me.

Running ```
lspci | grep VGA
``` in the terminal gives me this about my graphics card:

```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)\
```

And running ```
"compiz"
``` in the terminal makes my computer tweak out a little bit, and gives me this:

```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```

Haha I hope that helps

Thanks a lot!

---

### Post by Zorael on 2008-05-02
What is the terminal output of starting compiz?
```
$ compiz --replace &
```

---

### Post by UnderRedMountain on 2008-05-02
```
joe@joe-desktop:~$ compiz --replace &
[1] 6145
joe@joe-desktop:~$ Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```

I couldn't get desktop effects with my old graphics card, I got a new one from my friend, and the effects worked on the live cd.
Now I can't turn them on though :(

---

### Post by UnderRedMountain on 2008-05-02
Ahh, this is great
I've been doing some research 'round these forums, and it seems there are a few people with similar problems... that are unsolved.
I added the driver my video card is using (Generic video card, according to /etc/X11/xorg.conf, The driver was "vesa", generic open source or something) to the... whitelist... or something...
I'm not sure exactly what all that means.

But it changed the output when I put "compiz" or "compiz --replace" in the terminal to:
```
joe@joe-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2562 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

Compiz still doesn't work, whenever I try to enable desktop effects, it flickers, tweaks a bit, and tells me 'desktop effects could not be enabled'

Please... help me...
this is killing me... slowly..
draining my life force......

---

### Post by alsamman on 2008-05-02
Installing xserver-xgl worked before Hardy but now I'm not sure on how to fix it but I could've sworn that there is another thread with this issue somewhere in the forums that has been fixed.

---

### Post by UnderRedMountain on 2008-05-02
Not a chance you know about how far back it is?
Or what it was called?

Thanks, by the way, for taking the time to respond to this.
I know questions like this must get monotonous after a while haha

---

### Post by alsamman on 2008-05-02
haha, turns out that this was the thread that I saw which is on the first page of Desktop Effects & Customization right now lol:
[http://ubuntuforums.org/showthread.php?t=779297](http://ubuntuforums.org/showthread.php?t=779297)
the guy posted a link that he thought is his solution and he says that it fixed it and it seemes exactly the same as this one

---

### Post by UnderRedMountain on 2008-05-02
Okay, finally figured out how to follow those directions
I edited the compiz file to contain

LIBGL_ALWAYS_INDIRECT="true"
SKIP_CHECKS="yes"

at the top, and tried to run compiz, still got the same error message:

```
joe@joe-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2562 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


```

Ahh, i have an integrated graphics card. That just came to mind... I dont know what it is, but might my problem have anything to do with that?

---

### Post by UnderRedMountain on 2008-05-04
Okay...
It seems like there are a lot of people with Compiz problems, I don't know if that is the norm, of if that is just because of Hardy coming out.

: /

I am pretty sure I have an integrated video card, I don't know what it is though... maybe that would help.

So, two questions.

How can I figure out what my video card is?

How can I enable the proprietary drivers for the card, once I know what it is?

Again, thanks for all the help everyone.

---

### Post by netanakin on 2008-05-04
Actually i had a similar problem wen i had gutsy installed (since i had onboard graphic card (Intel 865) and low system memory of 256mb i was not able to run compiz.but installing xserver-xgl helped me 2 run compiz,but my pc got cluttered up and became almost unresponsive.

Hence i ripped off gutsy and installed hardy.At first when starting compiz i wasn't able to enable desktop effects, but when i used :

sudo dpkg-reconfigure xserver-xorg

to reconfigure my xorg, i became lucky since hardy then automatically detected by current graphic cad all my resolutions and my monitor in one go. I was not needed to type in any kind of configuration.And finally compiz worked on my system and faster than before.

It seems that ur onboard graphic card is Intel 845 but i do not know weather it is compatible to run compiz, but u can try what i did. wish u good luck.

---

### Post by UnderRedMountain on 2008-05-10
How do you uninstall gutsy and install hardy, without completely reformatting the system?

I hope theres a way, I'm having a lot more problems with the new version than I ever did before.

---

### Post by anton on 2008-07-02
I'm having the same problem with a machine with an Intel 82845G/GL graphics chip.  I've tried adding the following two lines to the compiz file:

```
LIBGL_ALWAYS_INDIRECT="true"
SKIP_CHECKS="yes"
```

but I still get the following error message when running compiz:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2562 (rev 01) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Segmentation fault
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

Can anybody suggest a solution?

---

### Post by missy_mcmissus on 2008-11-01
I also have this graphics card:
```
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)

```

and get a similar error message as the previous poster (Segmentation fault).

```
$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 00:02.0 0300: 8086:2562 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: Segmentation fault
not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present.
aborting and using fallback: /usr/bin/kwin
kwin: it looks like there's already a window manager running. kwin not started.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6b0e767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb6b0e81e]
#2 /usr/lib/libX11.so.6 [0xb6cdf518]
#3 /usr/lib/libX11.so.6(XFreeCursor+0x25) [0xb6cbb8f5]
#4 /usr/lib/libqt-mt.so.3(_ZN11QCursorDataD1Ev+0x3f) [0xb702b389]
#5 /usr/lib/libqt-mt.so.3(_ZN7QCursorD1Ev+0x5a) [0xb702b58e]
#6 /usr/lib/libqt-mt.so.3 [0xb702b5d5]
#7 /lib/tls/i686/cmov/libc.so.6(__cxa_finalize+0xb1) [0xb7bfb3b1]
#8 /usr/lib/libqt-mt.so.3 [0xb700b3a3]
#9 /usr/lib/libqt-mt.so.3 [0xb74d53ec]
#10 /lib/ld-linux.so.2 [0xb7ef6fcf]
#11 /lib/tls/i686/cmov/libc.so.6(exit+0xd4) [0xb7bfb084]
#12 /usr/lib/libkdeinit_kwin.so [0xb7e89307]
#13 /usr/lib/libX11.so.6(_XError+0xfe) [0xb6cd873e]
#14 /usr/lib/libX11.so.6 [0xb6cdfe5c]
#15 /usr/lib/libX11.so.6(_XReply+0x15a) [0xb6ce021a]
#16 /usr/lib/libX11.so.6(XSync+0x6a) [0xb6cd424a]
#17 /usr/lib/libqt-mt.so.3(_ZN12QApplication5syncXEv+0x32) [0xb700e306]
#18 /usr/lib/libkdeinit_kwin.so(_ZN12KWinInternal11ApplicationC1Ev+0x153) [0xb7ec1d43]
#19 /usr/lib/libkdeinit_kwin.so(kdemain+0x269) [0xb7ec2499]
```

I used to be able to run beryl in Ubuntu Edgy with this card. Then I turned it off for a year or so and tried again now with hardy, and I get the above error message.  Most of the posts I've seen about this card don't show 'Segmentation Fault' after "texture from pixmap" (though the poster right before me in this thread does).

If others with this video card have some suggestions, that would be great.

The attachment dialog isn't working for me, so I'm pasting my xorg.conf:
```
Section "Files"
    Fontpath    "/usr/share/X11/fonts/misc"
    Fontpath    "/usr/share/X11/fonts/cyrillic"
    Fontpath    "/usr/share/X11/fonts/100dpi/:unscaled"
    Fontpath    "/usr/share/X11/fonts/75dpi/:unscaled"
    Fontpath    "/usr/share/X11/fonts/Type1"
    Fontpath    "/usr/share/X11/fonts/100dpi"
    Fontpath    "/usr/share/X11/fonts/75dpi"
    Fontpath    "/usr/share/fonts/X11/misc"
    # path to defoma fonts
    Fontpath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load        "i2c"
    Load        "bitmap"
    Load        "ddc"
    Load        "extmod"
    Load        "freetype"
    Load        "int10"
    Load        "type1"
    Load        "vbe"
    Load        "dri"
    #added
    Load        "glx"
    Load        "GLcore"
    Load        "v4l"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option      "CoreKeyboard"
    Option      "XkbRules"      "xorg"
    Option      "XkbModel"      "pc105"
    Option      "XkbLayout"     "us"
    Option      "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option      "CorePointer"
    Option      "Device"                "/dev/input/mice"
    Option      "Protocol"              "ImPS/2"
    Option      "ZAxisMapping"          "4 5"
    Option      "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
    Driver      "wacom"
    Identifier  "stylus"
    Option      "Device"                "/dev/input/wacom"
    Option      "Type"                  "stylus"
    Option      "ForceDevice"           "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver      "wacom"
    Identifier  "eraser"
    Option      "Device"        "/dev/input/wacom"
    Option      "Type"          "eraser"
    Option      "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver      "wacom"
    Identifier  "cursor"
    Option      "Device"        "/dev/input/wacom"
    Option      "Type"          "cursor"
    Option      "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
    Identifier  "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    Boardname   "i810"
    Busid       "PCI:0:2:0"
    Driver      "i810"
    Option      "XAANoOffscreenPixmaps" "true"
    Option      "DRI"   "true"
    VideoRam    65536
    Screen      0
EndSection

Section "Monitor"
    Identifier  "DELL D1626HT"
    Modelname   "Custom 1"
    Option      "DPMS"
    HorizSync   30-107
    VertRefresh 48-160
    Gamma       1.0
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Device      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    Monitor     "DELL D1626HT"
    Defaultdepth 24
    SubSection   "Display"
           Depth        24
           Modes        "1024x768"      "800x600"       "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier   "Default Layout"
    Screen       0      "Default Screen" 0 0
    Inputdevice  "Generic Keyboard"
    Inputdevice  "Configured Mouse"
    Option       "AIGLX"        "true"

    # Uncomment if you have a wacom tablet
    #    InputDevice    "stylus"    "SendCoreEvents"
    #    InputDevice    "cursor"    "SendCoreEvents"
    #    InputDevice    "eraser"    "SendCoreEvents"
EndSection

Section "DRI"
    Mode    0666
EndSection

Section "Extensions"
    Option         "Composite"    "Enable"
EndSection

Section "Serverflags"
EndSection


```

---

