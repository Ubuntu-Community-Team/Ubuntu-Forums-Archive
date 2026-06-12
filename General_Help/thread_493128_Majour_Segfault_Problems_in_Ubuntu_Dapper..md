---
title: "Majour Segfault Problems in Ubuntu Dapper."
date: 2007-07-05
forum: General Help
---

### Post by DM was on fire! on 2007-07-05
Okay. I've been running Linux about three years now, about two and a half of it was spent running various versions of Lindows/Linspire.
Well, about a year and a half ago, I started having majour problems with Linspire when my browser would crash or freeze, or other applications woud. It would get so bad (every now and then my panel would crash), and then it would kernel panic.
The main reason I'm on Ubuntu now is because I got tired of the kernel panics and decided to try 

Well, about three weks later, I started having the same problems. Browser crashes and freezes (not as frequent as the crashes). When I downloaded StepMania 3.9 RC, it would crash in the main thread (I still keep it on root every now and then to see if it won't crash. It doesn't work). 
Since I started running Ubuntu, I've learned a bunch of tricks, like running programs in terminal. Whenever they crash, I get some sort of segmentation fault message. I'll supply them later.

Out of the four browsers (Firefox, Epiphany, Opera and Konqueror), Konqueror is the most stable. It still crashes, but not as bad.

I'm also having problems when it will just lock up out of the blue (I'm not able to type, move my mouse or anything), and sometimes it will take me back to GDM.

All I know is it's really ticking me off.
So, tell me. How do I fix a segfault? I know it has something to do with memory management, and something's getting into the memory it shouldn't, but do I put new memory sticks in, or do I replace the motherboard?

Thanks for your time, guys. :D
- DM

---

### Post by pjkoczan on 2007-07-05
> **DM was on fire! said:**
> Okay. I've been running Linux about three years now, about two and a half of it was spent running various versions of Lindows/Linspire.
Well, about a year and a half ago, I started having majour problems with Linspire when my browser would crash or freeze, or other applications woud. It would get so bad (every now and then my panel would crash), and then it would kernel panic.
The main reason I'm on Ubuntu now is because I got tired of the kernel panics and decided to try 

Well, about three weks later, I started having the same problems. Browser crashes and freezes (not as frequent as the crashes). When I downloaded StepMania 3.9 RC, it would crash in the main thread (I still keep it on root every now and then to see if it won't crash. It doesn't work). 
Since I started running Ubuntu, I've learned a bunch of tricks, like running programs in terminal. Whenever they crash, I get some sort of segmentation fault message. I'll supply them later.

Out of the four browsers (Firefox, Epiphany, Opera and Konqueror), Konqueror is the most stable. It still crashes, but not as bad.

I'm also having problems when it will just lock up out of the blue (I'm not able to type, move my mouse or anything), and sometimes it will take me back to GDM.

All I know is it's really ticking me off.
So, tell me. How do I fix a segfault? I know it has something to do with memory management, and something's getting into the memory it shouldn't, but do I put new memory sticks in, or do I replace the motherboard?

Thanks for your time, guys. :D
- DM

Segmentation faults *usually* aren't the fault of hardware. They're caused by bad memory management within a program. However, if these problems are happening randomly and for a lot of different programs, I can think of two reasons.

- Virtual memory corruption caused by race conditions. If two programs try to mess with virtual memory at the same time without appropriately locking the other out, bad things will happen. Program A, for instance, will overwrite a memory page that program B needs, and program B won't know (well, the kernel won't know, but it's essentially the same thing) that the data is bad. If a lot of programs were running when you noticed the segmentation faults, it might point to this.
- Your hardware (probably memory) is having problems. You should run memtest (available via grub or off of an install CD) and see if any problems arise.

If the seg-faults are happening predictably and only for a couple of programs, then it's probably the result of bad memory management within said programs. You should file bug reports to the appropriate parties, and/or use gdb or valgrind to see where the problems may be occurring.

That's the best advice I can give for now, until specific error codes or programs are given.

---

### Post by DM was on fire! on 2007-07-05
Okay. :D
The programs that I've been having the problems in are Firefox, Epiphany, Opera, Konqueror, RealPlayer (which won't crash as much as the others), and Nautilus, which are also the main programs that I use.

I've been running Konqueror on Terminal, and here's what I've gotten. I'll run Firefox on it in a few minutes.

> ashleigh1992@ashleigh1992:~$ konqueror
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QFont::setPixelSize: Pixel size <= 0 (0)
konqueror: WARNING: non-standard HTMLElement::scrollIntoView() not implemented
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(process:7118): GLib-GObject-CRITICAL **: gtype.c:2215: initialization assertion failed, use IA__g_type_init() prior to this function

(process:7118): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  10
  Minor opcode:  0
  Resource id:  0x3a00008
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3a00008
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  25
  Minor opcode:  0
  Resource id:  0x3a00008
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(process:7215): GLib-GObject-CRITICAL **: gtype.c:2215: initialization assertion failed, use IA__g_type_init() prior to this function

(process:7215): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed
Adobe FlashPlayer: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  10
  Minor opcode:  0
  Resource id:  0x3a00008
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3a00008
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  25
  Minor opcode:  0
  Resource id:  0x3a00008
libpng warning: tRNS chunk not allowed with alpha channel
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)
QFont::setPixelSize: Pixel size <= 0 (0)

But I was thinking that was because Konqueror is meant for the KDE rather than Gnome.

EDIT - Okay, I got the one (or rather, I got one) for Firefox:

> /opt/firefox/run-mozilla.sh: line 131:  9536 Segmentation fault      "$prog" ${1+"$@"}


When I tried to run Epiphany in Terminal, and I got this:

> ashleigh1992@ashleigh1992:~$ epiphany

(epiphany:9614): libgnomevfs-WARNING **: Failed to create service browser: Bad state


Oddly enough, it didn't give me a segmentation fault when it crashed. Weird.
I can also supply my crash info for StepMania 3.9 RC if needed.

And finally, when Konqueror crashes, I get a signal eleven SIGSEGV in either Konqueror or nsplugin.

---

### Post by DM was on fire! on 2007-07-07
*pokes at thread*
Just out of curiosity, how long is a Memtest supposed to take?
It was taking for ever, so I ended up shutting it off at the halfway point. XD

Also, would a bad motherboard battery affect it? I know the battery in my motherboard is going out, because almost every time I turn my computer on, I have to resync my time. ^^;;

---

