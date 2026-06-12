---
title: "&quot;Starting up...&quot; takes 5min."
date: 2008-06-11
forum: General Help
---

### Post by JSquirrel on 2008-06-11
Hello, I just installed ubuntu, it's pretty good. The only problem I'm facing right now is the slow start up. I don't mean the splash screen, as soon as it appears it only takes about 1 more min. but before the splash screen it says "Starting up..." and thats where it takes about 5min.

Thanks

---

### Post by ugm6hr on 2008-06-11
Try this: [http://ubuntuforums.org/showpost.php?p=4218621&postcount=106](http://ubuntuforums.org/showpost.php?p=4218621&postcount=106)

---

### Post by JSquirrel on 2008-06-12
I used "sudo gedit /etc/usplash.conf" to edit my original to:
xres=320
yres=240
and then I used:
"sudo update-usplash-theme usplash-theme-ubuntu"
but it still takes very long.

Sorry :frown:

---

### Post by ugm6hr on 2008-06-12
Maybe this?: [http://ubuntuforums.org/showthread.php?t=580903](http://ubuntuforums.org/showthread.php?t=580903)

---

### Post by Pjotr123 on 2008-06-12
Probably this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 3 )

---

### Post by JSquirrel on 2008-06-15
Sorry for the late reply (busy),
I've tried both solutions but there is still this black screen which says "Starting up..." and the computer does absolutely nothing for a looong time :mad:.

I'll try boot chart. Ill edit once I have the results.

edit: well bootchart gave me an error (apparently I added the wrong path at the end of the "kernel" line) but that was after the "Starting up..." screen which means boot chart wouldn't be able to chart the important part anyway.

therefore the time wasting takes place in:
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=cb3ce43d-c989-406d-954c-44435f5dffd9
and not in:
/boot/initrd.img-2.6.24-16-generic

---

### Post by creed50 on 2009-10-30
same here it takes sooooooooooo long to boot up  thats my bootchart   [https://wiki.ubuntu.com/BootCharting...20091030-1.png]("https://wiki.ubuntu.com/BootCharting?action=AttachFile&do=view&target=urox-desktop-karmic-20091030-1.png")

---

