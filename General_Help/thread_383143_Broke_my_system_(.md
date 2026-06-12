---
title: "Broke my system :("
date: 2007-03-12
forum: General Help
---

### Post by Josey on 2007-03-12
I resized my ntfs partition and created a fat32 with the free space.  Now when I boot i get grub error 17.  I think the problem is that grub can't mount the ntfs now because there were errors while partitioning.  chkdsk /p from the winxp recovery console fixed that.  I resized the partition back to exactly what it looked like before but I still get error 17.

My cd rom is on the fritz and I can't boot from it so reinstalling isn't an option. 

If only I could boot from a live disk I could fix grub.   :(

edit: **[COLOR="Red"]solved[/COLOR]**.... reinstalling grub with super grub disk fixed the problem.  See post below for details.

---

### Post by m.musashi on 2007-03-13
I'm guessing that adding the fat partition has changed the partition names so that grub can no longer find the files. The easiest fix is to use the Super Grub Disc but if you can't boot from a CD then that won't work.

Try editing the grub lines that looks like
```
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda6 ro quiet splash
```
If you previous partition was named sda5  (or hda5) for example, the addition of the fat partition may have caused it to be renamed sda6 (or hda6). If you can't boot a CD then it may be some guess work but with some trial and error it will work. You also need to change the hd0,5 part as well. The "5" in this case will always be 1 less than the sdax part. So if your boot directory is on sda4 for example the other one should read (hd0,3). Hope that makes sense. Good luck. You might also try borrowing or buying a new CD drive but this should get you going once you find the right partition.

---

### Post by chewearn on 2007-03-13
I'm not sure if this is the definitive method, but I find that it works on my system:

When you first boot up, I assumed that you actually got to the boot menu (since you mentioned that you got grub error 17, I think this mean no problem up to Stage 1.5).

At the menu, instead of selecting ubuntu (where it will lead to error 17), you press c.  This will give you the grub> prompt.

First, you need to locate the kernel:
```
find /boot/vmlinuz-2.6.17-11-generic
```

Your kernel might be different version; while typing, you can [tab] to autocomplete (if you don't know the exact kernel letters).

It might take some time for grub to spit out the answer.  You will get something like (hd0,5).  This mean hda6.  Then in the following commands, substitute the appropriate partition/device, with your kernel location (make sure you type exactly, since you cannot cut and paster).

```
root (hd0,5)
kernel /boot/vmlnuz-2.6.17-11-generic root=/dev/hda6 ro
initrd /boot/initrd.img-2.6.17-11-generic
boot
```

This should get you going into ubuntu, but make sure to edit menu.lst once you are in.

---

### Post by Josey on 2007-03-13
Thanks for the replies but with error 17 you don't get to any menu's.
You need to boot from something besides the hd at this point I believe.

For any poor soul that ends up with error 17 and no cd boot options...

After fixing the partition with winxp chkdsk /p which I used by downloading the floppy version of the windows recovery console and then resizing back to the original size with partition magic floppy rescue disks I still got grub error 17.  Perhaps I should have just skipped fixing the partition resize which I assumed is what would fix it since that's what broke it.  Focusing on reinstalling grub may have saved me a lot of headaches but live and learn I suppose. 

[Super Grub Disk]("http://supergrub.forjamari.linex.org/") is the boot floppy I used.
Then I simply followed the instructions here.
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by zvacet on 2007-03-14
Boot up your CD and pick &#733;Restore broken system&#733; option.Continue with dialogues until you have to choose your root device.It is probably second,cose you are dual-booting.If that is O.K. dialogue will continue and you will see more options.Select&#733;Reinstall GRUB boot loader&#733;.You will be asked where you would like to install grub.type hd0 and continue.GRUB will be reinstalled and you will be back in &#733;Rescue operations&#733;.Select &#733;Reboot the System&#733;.

---

### Post by m.musashi on 2007-03-14
> **Josey said:**
> Thanks for the replies but with error 17 you don't get to any menu's.
You need to boot from something besides the hd at this point I believe.

Sorry, I got ahead of myself. Grub won't load because most of the files are located on a partition that's been moved. I don't know how to edit or fix that if you can't boot something. I think the SGD is the best option if you can boot it. Sounds like you found a way to do it with a floppy so that's good.

Is all well now?

---

### Post by Josey on 2007-03-14
Yep it's working perfectly again.  Basically I just needed to reinstall grub to (hd0).

---

