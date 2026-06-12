---
title: "Boot vista if external drive isn't plugged in, Show grub if it is - How do i do this?"
date: 2008-06-03
forum: General Help
---

### Post by nappymonster on 2008-06-03
Hi all,
I'm running a dual boot with vista and gusty and my laptop. However gusty is on my external drive, so if i unplug it, grub loads, gets confused and gives an error (i think it's error 21). How Do i make it so that windows will auto boot if no drive is plugged in, and if one is it will bring up grub and ask? Possibly something to do with installing grub on the external (though i'm not sure)

According to my Grub menu.lst file:
Vista is on (hd0,1) - but there is only the 1 partition; the one vista is on. Shouldn't it be hda0,0?
Gusty is on (hd1,0)

Thanks,
Nappymonster

---

### Post by Zorael on 2008-06-03
The solution that springs to mind would be to set your boot order (in the BIOS setup) to boot from your external drive first if present, and if not, boot from your first (Vista) HD. Then put grub on said external drive and just a vanilla MBR on the Vista drive.

---

### Post by nappymonster on 2008-06-03
I haven't tried in along time, but trying to boot from the external hard drive last time just made it hang... I'll try again later and get back. Also, that sounds complex/i don't really understand. How do i put grub on the external, and what is meant by vanilla the MBR?

Finally, can anyone verify if this would be a good method?
[http://www.supergrubdisk.org/wiki/GrubOnRemovableExternalHardDisk](http://www.supergrubdisk.org/wiki/GrubOnRemovableExternalHardDisk)

---

### Post by NilsE on 2008-06-03
To avoid doing anything to your internal drive and make Ubuntu boot from the external drive do the following

1) Remove or disconnect your internal drive
2) Boot from the Ubuntu CD with the external connected
3) Select install and the only drive it should find is the external
4) Complete the install and it will put grub on the external.
5) Shut down and hook your internal back up.
6) Go into BIOS settings and set the external drive to boot first, and 
7) Set internal drive to boot second

To boot Ubuntu, plug the external in and let it go

To boot Vista, either select temporary boot from internal or don't plug in the external.

That is how I set mine up and it works every time.

---

### Post by timcredible on 2008-06-03
you can boot and run from an external drive, if that will work for you.  click [here]("http://ubuntukids.org/blog/?p=69") for instruction i used to make it work.

---

### Post by meierfra. on 2008-06-03
Yes you can use SuperGrub to solve part of your problem. You can use to it Fix the MBR of your internal drive and to install grub to the MBR of the external drive. But you also have to edit the "menu.lst"  before you use supergrub.


```
gksudo gedit /boot/grub/menu.lst
```

Change "#groot (hd1, ?)" to "groot (hd0,?)". So change the first number to "0" and do not change the second.

Then

```
sudo update-grub
```


Click on "Dual" in my signature for instruction to solve the whole problem from within Ubuntu, without having to use Supergrub:

(There is a small problem with the howto: "ms-sys" is not in the 8.04 repositories. You can get "ms-sys" from [URL="http://packages.debian.org/etch/ms-sys"]
http://packages.debian.org/etch/ms-sys[/URL]. Choose the i386 version, install by  right clicking)

---

### Post by meierfra. on 2008-06-03
Just noticed that you have vista. Then there is another way to accomplish your goal:

 Change menu.lst   as in the previous  post.
Also change "timeout 10" to "timeout 1" and "#hiddenmenu" to "hiddenmenu" in menu.lst.

 Get EasyBCD (see my signature). Then follow these instruction to add Ubuntu to the vista bootloader:

[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")

---

### Post by nappymonster on 2008-06-04
Thanks guys, but will your (meierfra.'s) method work with the fact that if i unplug my external drive, it still works?

---

### Post by meierfra. on 2008-06-04
Yes. Step3 of my instructions restore the MBR of your internal drive. This makes sure that you will boot directly into Windows, if the external drive is unplugged.

---

