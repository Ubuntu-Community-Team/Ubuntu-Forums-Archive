---
title: "Programs freeze randomly on Live USB"
date: 2013-07-04
forum: General Help
---

### Post by skylarmt on 2013-07-04
So, I'm using my 12.10 Lubuntu Live USB because my hard drive is failing.  This is happening semi-randomly, and it doesn't happen on other computers booted off the same iso.  Ny computer is an HP Mini 210-1000.  What happens is a program (Firefox, Chromium, PCmanFM, etc.) will just freeze for several seconds, usually when I try to edit a text box, use a menu, or open a drop-down box.  The little CPU meter in the taskbar shows the CPU is maxed out, but Htop running on a text terminal doesn't agree.  It shows that nothing unusual is happening.  This is getting really annoying, and it didn't happen on the 12.04 installed on my hard drive.  Anybody have any suggestions on why this is happening and what I can do to fix it?  Thanks!

---

### Post by DeathByDenim on 2013-07-04
Running from a USB stick will generally be slower, because read/write operation take a lot more time compared to an internal hard drive. That will cause freezes every now and then. I'm afraid there's not much you can do about that.

As to htop and the little CPU meter disagreeing, I'm not sure why that happens, but it may be because you have a multi-core processor maybe. I think htop will show you the cumulative usage, which means that if you have a 4 core CPU, then if one core is running at 100%, htop will only show 25% in total, whereas the little CPU meter may be showing the CPU usage for that one core. It may also be that the little CPU meter gets upset because of the freezes and report invalid values. The latter seems more likely, because I think the freezes are caused by the low read/write speed for USB sticks.

In any case, you might want to plunk a new hard drive in that computer. :)

---

### Post by sudodus on 2013-07-04
1. I think you can change the setup of htop to show not only your own processes, but also system processes (and it should show the same as the indicator).

2. Can you see if there is also some disk activity, for example swapping between RAM and the swap partition?

3. Will the the computer always recover from freezing? Otherwise you might have problems with the memory. This can be checked with memtest at the the first menu during boot.

---

### Post by skylarmt on 2013-07-04
The RAM is fine, I checked it along with the hard drive.  The freezing happens when the hard drive is unmounted I think.  The problem always goes away after several seconds.  I have never before had this problem with any liveusb on any computer.  It's not broken, just a major inconvience.

---

### Post by sudodus on 2013-07-04
If you have enough ram you can load the whole content of the live usb into ram. I think the boot option is 'ram' or 'toram' (might differ between distros). Then you will probably not experience such lagging. (toram according to this link)

[http://askubuntu.com/questions/28671/distro-that-i-can-load-into-ram](http://askubuntu.com/questions/28671/distro-that-i-can-load-into-ram)

---

