---
title: "boot issue after install"
date: 2015-06-11
forum: General Help
---

### Post by eipapp on 2015-06-11
I've tired to install Ubuntu Mate 15.04 which I was using in a dual boot system but now want to use as a stand alone OS.
Had no problems installing but then it wouldn't boot. From experience it seems I have to make a change to the grub menu
to include nomodeset after "quiet splash" for it to work properly. My question is, can I make this change to the grub menu 
before or during or after the install process so that when I'm done it will most likely boot as it should ?


Thanks,
Bruce

---

### Post by QDR06VV9 on 2015-06-11
To edit Grub2 during the boot process try the following:
  1.Immediately after the BIOS splash screen during boot, press and  hold the SHIFT button. This will display you grub containing a list of  kernels and recovery options.
2.Press "e" to edit the first kernel displayed
3.Find the line ending with quiet splash. Add your boot option before these key words - i.e. so the line looks like [...]nomodeset quiet splash
So it should look like this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
4.Press CTRL + X to boot
Then if satisfied with the results see this to make it permenant [http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu/38782#38782](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu/38782#38782) post #38
Fingers Crossed with what you think will happen.
Cheers

---

### Post by eipapp on 2015-06-11
Not so sure that hold the "SHIFT" button thingy is going to work for me but willing to give it a go.
FWIW I have a HP Pavilion 23 desktop computer that came with Win 8 as default but erased it to install linux
and have been running linux (mostly Ubuntu) on it for the past year+ 

Bruce

---

### Post by Bashing-om on 2015-06-11
eipapp; Hello l

Wine8==UEFI interface and in this instance it is the escape key that grub will recognize. There is only a 3 second window of opportunity and pressing releasing the escape key is the better way to get grub's attention.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by eipapp on 2015-06-12
SUCCESS !!!
FWIW : I elected to try Mate before installing. I then opened Gparted and deleted all partitions then installed Mate 15.04. On initial boot I hit Ctrl + Alt + F1 (which may or may not have been necessary) after which it booted into Mate.
Once there, I executed sudo nano /etc/default/grub etc. to make the changes to the grub menu. On re-boot it came right up and has been working great ever since.
Thanks for everyone's help with this issue. Much appreciated. 
Bruce

---

### Post by Bashing-om on 2015-06-12
eipapp; Great;

Glad ya up and running. As you are now booting with the boot parameter "nomodeset" - that options disables Kernel Mode Setting - You might want to consider installing a proprietary graphics driver. That though is the subject of a new thread.


[INDENT][INDENT]I wish
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

