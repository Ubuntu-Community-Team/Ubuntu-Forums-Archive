---
title: "Severe Problem, Can't Boot"
date: 2008-06-27
forum: General Help
---

### Post by patrickaupperle on 2008-06-27
I have a severe problem. My computer won't even boot with the Linux Hard drive. Right now I am using the windows HD. Please help. When I boot it says "GRUB" at the top of the screen. Then nothing. On the HD I had 3 real partitions plus an extended containing 2 more logical partitions. I had Ubuntu, openSUSE, and Home for SUSE because I had not changed ubuntu to use it, yet (and really did not plan to). I then made a partition for my music (one of the 2 logical partitions, the other being swap) and tried to set it as such from ubuntu. I changed the ownership from root to patrick. Now I can't even get to the grub menu. Please help!!

---

### Post by ajmorris on 2008-06-27
hi there,
you say it says GRUB but then nothing... no errors or anything
Also you say now i cant even get back to the grub menu, you mean upon booting it doesnt show up?

AJ

---

### Post by BobbyIceCubes on 2008-06-27
I just made a post regarding booting with Windows a minute ago...  Did Windows successfully shut down, or was it hung...

---

### Post by patrickaupperle on 2008-06-27
When I boot I see the BIOS screen, then a black screen that says "GRUB" at the top and nothing else. No error messages. That is on a completely separate HD then windows.

Edit: No The grub menu does not show up at all. The grub menu is supposed to show up.

---

### Post by ajmorris on 2008-06-27
> **patrickaupperle said:**
> When I boot I see the BIOS screen, then a black screen that says "GRUB" at the top and nothing else. No error messages. That is on a completely seperate HD then windows.

You could try re-installing grub to the mbr.

1) Boot into a linux live cd
2) Run a terminal
3) run ```
sudo grub
```
3) ```
find /boot/grub/stage1
```
4) ```
root (hd#,#)
``` (where #,# are the numbers output from command number 3)
5) ```
setup (hd0)
```

Please note, since you have more than one linux OS installed, step 3 will output more than one result, just pick the one that you have configured your grub menu.lst in, and that you would like re-installed to the MBR. NOTE: Grub does devices starting from 0, i.e, your partition number 1 on hard disk 1, would be hda1 or sda1 in fdisk, in grub, it is (hd0,0)

AJ

---

### Post by patrickaupperle on 2008-06-27
> **ajmorris said:**
> You could try re-installing grub to the mbr.

1) Boot into a linux live cd
2) Run a terminal
3) run ```
sudo grub
```
3) ```
find /boot/grub/stage1
```
4) ```
root (hd#,#)
``` (where #,# are the numbers output from command number 3)
5) ```
setup (hd0)
```

Please note, since you have more than one linux OS installed, step 3 will output more than one result, just pick the one that you have configured your grub menu.lst in, and that you would like re-installed to the MBR. NOTE: Grub does devices starting from 0, i.e, your partition number 1 on hard disk 1, would be hda1 or sda1 in fdisk, in grub, it is (hd0,0)

AJ

I don't have a live cd right now, but I will DL and burn one and get back to you on that. 

Edit: Would a Linux Mint live cd work?

---

### Post by patrickaupperle on 2008-06-27
I ran the repair section of the openSUSE installation DVD and now I can boot openSUSE. Unfortunantly there is no entry for Ubuntu now. Please help me add Ubuntu back to the grub menu.

---

### Post by enchesss on 2008-06-27
use the mint cd and reinstall grub using reply #5

---

### Post by patrickaupperle on 2008-06-27
> **enchesss said:**
> use the mint cd and reinstall grub using reply #5

Will I have the suse grub menu? 
edit: Would a suse live cd work better?

---

### Post by ajmorris on 2008-06-27
you have already added the SUSE grub to the mbr, so, you can boot SUSE, mount your ubuntu partition (mount /dev/<device> /mnt/<mount point) sudo fdisk -l can help you find the device for ubuntu.
Then just copy your ubuntu **entries** from /boot/grub/menu.lst on your ubuntu partition, to /boot/grub/menu.lst on your suse partition. reboot and you will have SUSE and grub entries.

AJ

---

### Post by patrickaupperle on 2008-06-27
> **ajmorris said:**
> you have already added the SUSE grub to the mbr, so, you can boot SUSE, mount your ubuntu partition (mount /dev/<device> /mnt/<mount point) sudo fdisk -l can help you find the device for ubuntu.
Then just copy your ubuntu **entries** from /boot/grub/menu.lst on your ubuntu partition, to /boot/grub/menu.lst on your suse partition. reboot and you will have SUSE and grub entries.

AJ

Unfortunately, that did not work. I get an error when I try to boot Ubuntu. Maybe I should just forget about ubuntu and go all opensuse. I am going to try the grub thing from openSUSE. (Not a live cd.)

---

### Post by patrickaupperle on 2008-06-27
> **ajmorris said:**
> You could try re-installing grub to the mbr.

1) Boot into a linux live cd
2) Run a terminal
3) run ```
sudo grub
```
3) ```
find /boot/grub/stage1
```
4) ```
root (hd#,#)
``` (where #,# are the numbers output from command number 3)
5) ```
setup (hd0)
```

Please note, since you have more than one linux OS installed, step 3 will output more than one result, just pick the one that you have configured your grub menu.lst in, and that you would like re-installed to the MBR. NOTE: Grub does devices starting from 0, i.e, your partition number 1 on hard disk 1, would be hda1 or sda1 in fdisk, in grub, it is (hd0,0)

AJ

Will this still work even though my openSUSE grub does not have Ubuntu?

---

### Post by patrickaupperle on 2008-06-27
I Erased my entire hard drive and put open suse on the only non swap partition I made. No more problems. :)

---

### Post by ajmorris on 2008-06-27
> **patrickaupperle said:**
> I Erased my entire hard drive and put open suse on the only non swap partition I made. No more problems. :)

you didnt need to do that, you could have just added the device out the front of your ubuntu kernel line in menu.lst so that SUSE could pick up the ubuntu boot files, however, if you're happy, then i am :)

AJ

---

### Post by patrickaupperle on 2008-06-28
> **ajmorris said:**
> you didnt need to do that, you could have just added the device out the front of your ubuntu kernel line in menu.lst so that SUSE could pick up the ubuntu boot files, however, if you're happy, then i am :)

AJ

I know I did not have to. I almost cried after I did, because there was an extremely simple solution over on the openSUSE forums.:lolflag: Oh well, I may come back, though. Though I think I will go to straight debian lenny, though. Can the version of compiz in lenny do what the openSUSE version will do? (mostly the cube deformation)

---

