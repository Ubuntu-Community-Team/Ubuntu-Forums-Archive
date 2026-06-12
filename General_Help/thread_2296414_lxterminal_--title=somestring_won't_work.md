---
title: "lxterminal --title=somestring won't work"
date: 2015-09-25
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2015-09-25
I could swear that

lxterminal --title=somestring

used to work. But not now, not for me.  Neither does

lxterminal -t somestring

This is under openbox in Trusty, so I tagged this Lubuntu, though strictly speaking I installed from the mini.iso and I don't have the full Lubuntu DE.

So does it work for anyone useing lxterminal in Lubuntu Trusty? If so, maybe I've left something out in the way of some undocumented dependency. If not, maybe it is just a bug. Any enlightenment appreciated.

---

### Post by Dreamer Fithp Apprentice on 2015-10-23
Shameless self bump.

I'd appreciate it if someone who uses Lubuntu (or any setup with lxterminal under openbox) would try this and tell me if it works for them. Yes or no, either would at least give me a clue. BTW "lxterminal -T sometitle" doesn't work for me either. Nor do these work if I put the title string in "-marks.

The reason I want this is so I can run a script in a window that I can control (such as focus, iconify, etc.) with wmctrl commands IN THE SCRIPT, so I can, for example, have it iconify while it is doing something and call attention to itself when it is through. In the past I've done this by invoking the script to run in a titled window with "lxterminal -t sometitle -e scriptname" and using the -a option to wmctrl to specify the window to act on by title. But it quit working.

 Perhaps there are other ways to do this and I'd welcome suggestions on that as well. If I can't make lxterminal work, maybe I'll try xvt. I'd probably switched already anyway if it weren't so darned hard to get xvt to use a decent font.

---

### Post by vasa1 on 2015-10-23
```
$ lxterminal -t blah
$ lxterminal -t "blah blah"
```both work in the Openbox session of Lubuntu 14.04.


```
$ apt-cache policy lxterminal
lxterminal:
  Installed: 0.1.11-4ubuntu3
  Candidate: 0.1.11-4ubuntu3
  Version table:
 *** 0.1.11-4ubuntu3 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
$ 
```

```
$ apt-cache depends lxterminal
lxterminal
  Depends: libc6
  Depends: libgdk-pixbuf2.0-0
  Depends: libglib2.0-0
  Depends: libgtk2.0-0
  Depends: libvte9
  Depends: libx11-6
  Conflicts: lxterminal:i386
$
```

---

### Post by Dreamer Fithp Apprentice on 2015-10-24
Thanks, Vasa1.

==========================================
tldr summary:

Seems to be a bug in the 32 bit software, but shows up only in  restricted circumstances that are easily avoided,, at least for the cases I've checked.
==========================================

Some interesting commands there I didn't know. I get:
```
me@u32:~$ lxterminal -t blah
me@u32:~$ # ^ gave me an untitled lxterminal window
me@u32:~$ lxterminal -t "blah blah"
me@u32:~$ # ^ gave the same result, an untitled lxterminal window
me@u32:~$ apt-cache policy lxterminal
lxterminal:
  Installed: 0.1.11-4ubuntu3
  Candidate: 0.1.11-4ubuntu3
  Version table:
 *** 0.1.11-4ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
        100 /var/lib/dpkg/status
me@u32:~$ apt-cache depends lxterminal
lxterminal
  Depends: libc6
  Depends: libgdk-pixbuf2.0-0
  Depends: libglib2.0-0
  Depends: libgtk2.0-0
  Depends: libvte9
  Depends: libx11-6
me@u32:~$
```So I have to assume this is a bug in the 32 bit version of one or more of the above.

BUT: I've been stupid - in practice this turns out to be unimportant. When I write scripts, I often test a command in a terminal to be sure I remembered the syntax correctly. That's how I ran into this issue. In actual USE, I'd be following the t option with an " -e somecommand". I just noticed one of my old scripts that uses this is still working, so I tested with -e options:
```
me@u32:~$ lxterminal -t blah -e ls
```
elicits a barely visible flicker, presumably a titled terminal window opening and closing, whereas:```
me@u3:~$ lxterminal -t blah -e sleep 6
```gives me a properly titled lxterminal window.

Thanks again, champ.

---

