---
title: "Help with GRUB menu.lst edit"
date: 2007-02-08
forum: General Help
---

### Post by a5benwillis on 2007-02-08
I have been looking for a way to switch my xorg.conf at or before boot since I use my laptop screen at home and dual monitors at work. I found a helpful thread here and proceeded to implement the instructions found in this post:

[http://ubuntuforums.org/showpost.php?p=2013432&postcount=20](http://ubuntuforums.org/showpost.php?p=2013432&postcount=20)

When I select one of the boot options from my GRUB menu Ubuntu boots up to a root console instead of passing the XORG parameter like I would have expected. Can anyone tell me what I'm going wrong? I've attached a copy of the important part of my menu.lst

```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		SINGLE MONITOR- Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash XORG=single
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		DUAL MONITOR- Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash XORG=dual
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

```


As you can see the second and third items are the ones in question.

Thanks!
Ben

---

### Post by milton1 on 2007-02-08
menu.list index starts at zero. On this list, booting to DUAL MONITOR would be 

default   2

---

### Post by a5benwillis on 2007-02-08
Thanks for the reply but that did not help.

I even removed the default lines from the menu but I still get the root console login prompt.

Ben

---

### Post by a5benwillis on 2007-02-09
Can anyone shed some light on the GRUB menu? Specifically how to pass an arg from the boot line.

Thanks!

Ben

---

### Post by dagnabit dang doohickey on 2007-02-09
I looked at the post you linked to and your menu.lst looks fine as per the posters instructions. But, the thing is, the grub part of this xorg.conf juggling trick seems to not be the critical part. Most of the magic in this thing is when the script gets called at 'some' run-level and then juggles your multiple xorg.conf files.

The run-level symlink, the script, and your custom xorg.conf files might be the place to look.

---

### Post by a5benwillis on 2007-02-10
I created a script called xorg.sh
Placed it in /etc/inti.d
Made it executable
Made a sym link with this command:

```
sudo update-rc.d -f xorg.sh start 20 2 3 4 .
```

This shows up in /etc/rc2.d as:

```
lrwxrwxrwx 1 root root  17 2007-02-08 15:34 S20xorg.sh -> ../init.d/xorg.sh
```


The script does run but it never gets the correct arg because when I use one of the menu options I always get a root console instead of a normal boot like I get when selecting the first menu item.


This should just work, it doesn't seen very complicated.

Ben

---

### Post by dagnabit dang doohickey on 2007-02-10
You made the initial runlevel 2, which is what I would have probably done, since gdm starts in runlevel 2. But, if I remember correctly, gdm has a start order of S13, so your script should probably be given a start order of, say, S01 instead of S20 so the script can do it's thing before gdm starts.

---

### Post by a5benwillis on 2007-02-11
> **dagnabit dang doohickey said:**
> You made the initial runlevel 2, which is what I would have probably done, since gdm starts in runlevel 2. But, if I remember correctly, gdm has a start order of S13, so your script should probably be given a start order of, say, S01 instead of S20 so the script can do it's thing before gdm starts.

Ok, so i changed the run order to S01 and the problem booting up went away. Thanks!!!

No for the second problem. The script doesn't get the XORG attribute from the boot loader as it should. I added some error checking so that I would at least know if the script was fired properly but it isn't copying the xorg.conf file as it should.

Any ideas? Anyone?

Thanks!
Ben

---

