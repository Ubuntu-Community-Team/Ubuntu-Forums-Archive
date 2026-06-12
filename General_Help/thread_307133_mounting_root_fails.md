---
title: "mounting root fails"
date: 2006-11-26
forum: General Help
---

### Post by elektronaut on 2006-11-26
Hi,

I already [filed a bug](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/73300), but I guess it's more likely to get a quick advice what to do in this situation here in the forum. As I have already written the best description I can give in launchpad, I'll simply paste the text here:
-------------------
this happened on a Dapper system:
I was copying a movie from a cd to the hard disk. While burning the cd on another computer before, the program reported an error at the end of the process. As I could watch the movie nearly till the end, I didn't care. Now, while copying as mentioned before, the copy process stalled just before the end. The system froze. I couldn't even restart the X server or get to another console. I had to reboot using "Ctrl-Alt-SysReq + RSEIUB". But the startup process stopped and reported this error:

udevd-event[3243]: wait_for_sysfs: waiting for 'sys/devices/platform/i82365.0/bus' failed

Searching for this line, I found bug [#32446](https://launchpad.net/bugs/32446). But the people there reported about kernel upgrades, which is not the case here, so I decided to file a new bug. Following the advice given there, I chose an older kernel in grub, this time 2.6.15-26-386. Now I got the error message again, but after a little while it disappeared and the boot process finished it's tasks. Again following an advice given there, I called "update-initramfs -u -k 2.6.15-27-386". But this didn't help. I still can't boot kernel 2.6.15-27-386. Any advice what to do now?

---

### Post by mayonaise15 on 2006-11-26
Well, this is a bit over my head.  I did find another post that may lead you down the right track: [http://ubuntuforums.org/showthread.php?t=224426]("http://ubuntuforums.org/showthread.php?t=224426")

There is also a link in that thread that you should check out.  Best of luck to you.

---

### Post by elektronaut on 2006-11-26
Thanks for pointing out those threads, I didn't find them when I was searching for answers. Reinstalling the newer kernel did the trick. Lesson learnt: Always have a second kernel in your boot partition!

---

