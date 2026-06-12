---
title: "framebuffer device problem"
date: 2007-12-27
forum: General Help
---

### Post by ckth on 2007-12-27
Hello.

Inspired by [this thread]("http://ubuntuforums.org/showthread.php?t=260946") on text-based systems, I was trying to run graphical applications from the command line, links2 and mplayer being amongst the first test subjects. 

However, trying to run "links2 -g example.html" returns the following error:

```
(*) DirectFB/Core: Single Application Core. (2007-08-07 19:21)
(*) Direct/Memcpy: Using MMXEXT optimized memcpy()
(!) Direct/Util: opening '/dev/fb0' and '/dev/fb/0' failed
--> No such file or directory
(!) DirectFB/FBDev: Error opening framebuffer device!
(!) DirectFB/FBDev: Use 'fbdev' option or set FRAMEBUFFER environment
variable.
(!) DirectFB/Core: Could not initialize 'system' core!
--> Initialization error!
```

Indicating that I have no framebuffer devices /dev/fb*. 

The output of mplayer is similar in tone;
"mplayer -vo fbdev example.mpeg" complains that it "can't open /dev/fb0; No such file or device"

The output of fbset confirms this:
```
fbset -iv
open /dev/fb0: No such file or directory
```


(Searching on the internet, I find several posts on similar problems, including [one]("http://ubuntuforums.org/showthread.php?t=362158") on the Ubuntu forums, but they're all unanswered.)
The [tldp HOWTO]("http://tldp.org/HOWTO/Framebuffer-HOWTO-5.html") on Framebuffers is quite simply beyond my league; I could follow the instructions, but I have no idea what they are about.

I'm running a vanilla Gutsy install on Intel hardware (more specifically, the Intel 915 series of graphics cards) and a Pentium 4 3GHz machine, and have not tweaked or modified anything major.

Adding the option "vga=791" to the defoptions line in /boot/grub/menu.lst causes *no* change in the virtual console resolution or behaviour.
 
I would really like to get the framebuffer going, as I spend quite some time on virtual consoles. Does anyone else have this problem? Any help would be appreciated.

---

### Post by ckth on 2007-12-27
Can *anyone* running Gutsy manage to get the framebuffer going?

It appears this is a crippling bug in Gutsy that I can't understand the details of:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/135613](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/135613)

None of the proposed solutions ([http://ubuntuforums.org/showthread.php?p=3331275](http://ubuntuforums.org/showthread.php?p=3331275)) work, with either 2.6.22-14 or 2.6.22-15.

Any help, details or confirmation would help.

---

### Post by Factory on 2008-01-30
I'm getting similar error s when trying to run zsnes from a command line.

Running Gutsy as well.

---

### Post by ckth on 2008-02-04
I found a solution to that; posted here: [http://ubuntuforums.org/showthread.php?t=652038](http://ubuntuforums.org/showthread.php?t=652038)

-ckth

---

