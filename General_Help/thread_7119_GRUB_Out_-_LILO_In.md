---
title: "GRUB Out - LILO In"
date: 2004-12-04
forum: General Help
---

### Post by Thanatos9602 on 2004-12-04
OK, I'm a total hardheaded newbie to linux. I'm a power-user in DOS & Windows. Learned computers before windows. Makes it very hard to unlearn & learn linux. I use Win98SE faithfully. I also have DamnSmall on 'hda6'. My old HD throws the numbers in the partitions off. I put Ubuntu on 'hda4'. I tried to get it to install LILO. I know that & how to play with it. NO GO. It wouldn't do it. I loaded GRUB instead. I have spent the last three days trying to figure how to edit GRUB & can't seem to get a handle on it. How can I uninstall Grub & install Lilo. Maybe, reformat the linux partitions, do the fdisk/mbr, fixboot & then install Ubuntu first without lilo or grub & then dsl to do the lilo thing?? Sorry for all the trouble. Maybe in 12years I can learn linux like I know windows??? I just can't seem to find the grub files it says to edit. What is the file manager in Ubuntu?? In dsl, it is emelfm. I like it a nice to pane file system. Also, how do I mount my windows drives in Unbuntu. I don't see a fluxbox anywhere. Sorry again for the stupid questions & thank you for your time.  ](*,)

---

### Post by Thanatos9602 on 2004-12-04
OK, 'bout got the edit thing right. It now reads: 98, bun, other operating systems, memory test, dsl. Got to get dsl up to number three, but maybe I can handle that. I still need to know how to mount drives, so I can move stuff of Win drives to linux drives. I don't have a linux modem yet. I always figure, "What the heck!", if I mess up, just format & reboot. I save all the important stuff on my old 6.4G Maxtor HD. Any help with the mount junk & file explorer type thingy, greatly appreciated. Thanks a million. Still trying. ](*,)   :?

---

### Post by IAmNotPhillip on 2004-12-04
This dosen't really belong here, but to mount your drives, try
```
sudo nano /etc/fstab
```

then add this line
```
/dev/hda1       /media/winC     ntfs    rw,users,dmask=0222,fmask=0333 0       0
```

finally, create the folder /media/winC and reboot.

---

### Post by Thanatos9602 on 2004-12-04
Thanks. I'll try & keep it in the proper forum from now on. I made a slight boo-boo in playing in the config files & had to reformate the Ubuntu drive & reinstall it. Man, this stuff takes longer than any windows program to boot. Interesting to watch though. Wish me luck with the rest. Thanks again.  :-D   :p

---

### Post by Thanatos9602 on 2004-12-05
It worked fine. I also made a folder & line for winG which is my hold drive. I made them vfat instead of ntfs, because I run 98Se. I put in a folder for my dsl as ext2, but when I try to access it, it says to many drives mounted. I can't unmount a drive. When in terminal, I type " unmount /dev/ hda?" it says it can't find the unmount command. Also have a few more questions. I'll start a new thread called "Master User" or something like that. Thanks for the help. I also found a couple tricks I'll put in the other thread. Thanks a million for the help. =D>  :o  Hell, cheers. Have a cold one on me. I can't find the beer mug toast icons anymore?? Thanks.

---

### Post by TravisNewman on 2004-12-05
it's umount, not unmount. And the error that says too many drives mounted sounds like what I get when I try to mount the extended partition (which has no data) instead of the logical drive inside the extended partition.

Again, can a mod with  power here move this to its proper location

---

