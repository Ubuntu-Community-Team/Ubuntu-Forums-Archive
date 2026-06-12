---
title: "Ubuntu Doesn't Boot after Windows Recovery Panel's &quot;Fixboot&quot;"
date: 2008-03-30
forum: General Help
---

### Post by neo1991 on 2008-03-30
Hey guys,


Well, I'm new to Ubuntu, and to say that I love it would be an understatement. I'd rather not use a computer than go back to Windows at this point. However, I wanted to repair my windows installation for the purpose of running games on occasion. Anyway, I think I borked up Linux in the interim.

So, here's my setup. I have two WD hard drives, each identical, with 250 gigs. So, I installed Ubuntu on one of them, when the Windows one was unplugged. Installed beautifully, and I've already said how pleased I was with gutsy. So, I plugged in the Windows HDD, and I was hoping GRUB would magically appear and ask me which OS to boot from. Well, it didn't. It just booted directly to Ubuntu. 

So, I went into the Windows Recovery Console from the windows XP disk. It asked me which drive to use, and the only option was D:\windows, which I selected. Then, I did a "help," as I have no experience with this. Found the fixboot command, which seemed perfect. I used that command, and then it asked if i was sure I wanted to write a boot sector in F:\. Having no idea what disk F:\ referred to, I hit y, and it did it "successfully."

So, I boot  the system. Windows acted just as before....not existing at all. However, when I went on into Ubuntu to do some work, it didn't work! You know how the progress bar comes up under the Ubuntu Logo and the words Ubuntu? It just stops at about 1%.After a good long while it goes into this BusyBox commandline.

Needless to say, I'm completely lost. If you guys could help me out, you have no idea how happy I'd be. I'm afraid I screwed up my Ubuntu installation, by overwriting some important part of the boot. Is there any way to recover this?

Thanks,
George C. Linderman


EDIT: Awww, shoot. I think I just borked up my drive :( I went into the ubuntu CD, mounted my Linux drive, and it's empty but for three files (with gibberish names). I guess that means it's hopeless, right?

---

### Post by el_ricardo on 2008-03-30
hmmmm, seams odd! if you've only just installed ubuntu then you haven't got much to lose by reinstalling. You went wrong when you removed the windows drive while installing ubuntu. If you left it in then the ubuntu installer would have seen both OS's and configured its self accordingly. Reinstalling ubuntu with the windows drive inserted should get you what you were after.

The reason this happened is because the windows recovery console overwrites your MBR, regardless of what was on there before.

---

### Post by danwood76 on 2008-03-30
Not necessarily hopeless.

You could try running testdisk to see if it can recover your partitions, it may just be that windows being as stupid as it is has overwritten something crucial in your boot sector.

Testdisk is available from the repositories when using the live CD, you may have to set the multiverse repository to be on to use it.

---

### Post by trippinnik on 2008-03-30
1. Boot with any live CD (I've done it with Knoppix 3.x and Ubuntu)
2. Get a root shell and make a folder (mkdir ubuntu)
3. mount the root (/) partition of ubuntu (e.g. mount /dev/hdb ubuntu if you have two disks)
4. chroot the mounted partition (chroot ubuntu)
5. grub-install /dev/hda [1]
5. Exit the shell
6. Reboot

is one way i found: from [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)
basically when you recovered WIndows you overwrote the bit of code that loads Ubuntu with one that only loads windows.  The Ubuntu loader will detect both and allow you to boot to both.

---

### Post by xeth_delta on 2008-03-30
If grub was over-written, you can restore it from the live cd: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Good luck

---

