---
title: "help to analyse bootchart &amp; dmesg output to reduce boot time"
date: 2013-04-08
forum: General Help
---

### Post by chinmay3 on 2013-04-08
Hello community members.
I have hp-pavilion g series with 4gb ram & amd quad core processor. i am multibooting with ubuntu, kde , linux mint & win 7 (can't remember when i booted it last time). The problem i am facing that is very long boot ( about 85 secs & 105 sec from pressing on switch& choosing user account). I googled forum for its solution but i am confused with applying those solution since they are for specific problem of their system. I am posting dmesg & bootchart output. Please help me to find what making so much to boot.
Thanks in advance.

---

### Post by tgalati4 on 2013-04-08
Can't read your bootchart.  Try using pastebin so that we can see the original resolution of the chart.

Basically, look for the  processes that have long bars and lots of IO (hard disk access) and IO-Waits.  The ideal boot chart would have high CPU and high disk IO compressed to the left as much as possible.  Areas where both CPU and disk are low are slack areas that just waste boot up time--those are the areas to focus on for speed up.

---

### Post by oldfred on 2013-04-08
The entries in your dmesg are these:

 > [    7.593624] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   10.208231] usb 6-1: USB disconnect, device number 2
[   27.685440] Adding 4881404k swap on /dev/sda6.  Priority:-1 extents:1 across:4881404k 
...

  >  [   51.005864] [fglrx] Reserved FB block: Unshared offset:1fff4000, size:c000 
[ 2105.772605] r8169 0000:03:00.0: PME# enabled



Do you have a USB flash drive (USB6-1?) or other device plugged in?

But the main issue the r8169 driver? Is that correctly installed? Or is it the entry before which is your fglrx driver?

---

### Post by chinmay3 on 2013-04-08
Thanks for reply.
Bootchart--- [http://www.freefilehosting.net/linuxbox-precise-20130408-4](http://www.freefilehosting.net/linuxbox-precise-20130408-4)
I have no usb flash or any other usb device connected during boot. & i have ATI/AMD FGLRX DRIVER installed.

---

