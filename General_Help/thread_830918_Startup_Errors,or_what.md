---
title: "Startup Errors,or what?"
date: 2008-06-16
forum: General Help
---

### Post by 0bbe on 2008-06-16
I'm asking for your help on this problem of mine,everytime I try to start my PC I get this screen after the Ubuntu load screen;
[[IMG]http://img77.imageshack.us/img77/3618/bild040ty6.th.jpg[/IMG]](http://img77.imageshack.us/my.php?image=bild040ty6.jpg)

I've got it to start 2 times using Recover mode,but most of the times when i use it I receive this screen,and after it to same as screen 1.
[[IMG]http://img77.imageshack.us/img77/2875/bild041cw2.th.jpg[/IMG]](http://img77.imageshack.us/my.php?image=bild041cw2.jpg)

Always when I shut Ubuntu down I receive some error messages.
I think it started after I started shutting down PulseAudio,tough when I last time got it running I didn't kill PulseAdio but still got error messages.

So I need help fixing this,please.

---

### Post by ibuclaw on 2008-06-16
Looks like a hard drive problem/the kernel isn't finding the hard-drive at bootup.

Do you have your Ubuntu LiveCD on you? If so, you'll need to boot up into it.

Regards
Iain

---

### Post by danwood76 on 2008-06-16
The message on the screen:

> 
status {DRDY ERR}
error {UNC}

Indicates disk read errors which are normally caused by bad sectors. (hard disk could be on its way out)

Restart in recovery mode and run a checkdisk by using the following command, this will automatically fix errors for you.
```

fsck -ACaf

```

---

### Post by VMC on 2008-06-16
It appears the hard drive has some hard sector errors. Very little if anything can be done. Read this almost exact same issue:
[http://ubuntuforums.org/showthread.php?t=796492](http://ubuntuforums.org/showthread.php?t=796492)

You could run somthing like Spinrite on the drive. [It does a low-level format], but depending on the size of your drive it could take several days to finish and then not recover fully. Drives are cheap compared to the anguish of trying to save it.

---

### Post by 0bbe on 2008-06-16
Tinivole:

I tried it that way,didn\t work I\m afraid.

(Ah writing from Ubuntu Live CD so Keyboard isn\t configured.)

danwood76:

It still goes around till screenshot1 after trying to recover now.

VMC:
I guess youre right this harddisc had some issues before aswell,but after formatting it it worked flawlessy till now.
Anyways I have a new harddisc on this Pc aswell,tough its running my Windows.
Is there btw any way I could save my 3rd partition of that disc(3rd partition is where I have all my music etc) so it woudn\t get overwrited by Ubuntu?

---

### Post by anibalrojas on 2008-06-22
Edit the kernel entry in the grub starup menu and add the pci=nomsi parameter to the end of it.

--
Aníbal Rojas
[http://laracaraoscura.com](http://laracaraoscura.com)
[http://anibal.rojas.com.ve](http://anibal.rojas.com.ve)

---

