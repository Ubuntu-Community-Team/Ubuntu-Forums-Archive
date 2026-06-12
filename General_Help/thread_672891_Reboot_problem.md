---
title: "Reboot problem"
date: 2008-01-20
forum: General Help
---

### Post by xodroolis on 2008-01-20
Reboot problem
When i turn on the pc when i get to the screen with the ubuntu log and the loading bar, it crashes as soon as it starts filling the bar. always at the same point. i have to press the reset button for the computer to responce to something. And then the same again. i must put the ubuntu boot cd, and choose from the list: boot from first disk drive, in order to solve this problem. after that i may have no problem for 1 or 2 boots. and then the same again.
I have ubuntu gutsy
and i recently installed kernel check and after i built latest kernel, i did not configure anything by myself. do i have to configure there something?

---

### Post by aphirst on 2008-01-20
There may be a problem with your MBR. (master boot record)

```
sudo grub

grub> find /boot/grub/stage1
 (hdx,y) # this will be where your MBR is
grub> root (hdx,y)
grub> setup (hdx)
```

you'll need (probably) to reconfigure your /boot/grub/menu.lst for your booting partitions.

I got the inspiration from a GFXBoot tutorial by PingunZ on this site, the url of which eludes me...

---

### Post by xodroolis on 2008-01-20
```
grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

```
this is what i get. what should i do next?

---

### Post by aphirst on 2008-01-22
As far as memory serves you just need to ensure that your /etc/fstab and your /boot/grub/menu.lst are accurate. I can't post mine because im on a $hit3 windoZe machine (at school :P ) but i will when i get home.

Then it should *crosses fingers* work :D

---

### Post by pointone on 2008-01-22
I doubt this problem has anything to do with GRUB or the MBR, since it only occurs AFTER Ubuntu has already started loading. When it occurs, try booting from the live CD and check /var/log/dmesg for errors. Better yet, just post the file here.

---

### Post by xodroolis on 2008-01-23
i dont know... as a matter of fact... system starts with no problems now...
but when it happened i tried to start from the live cd and nothing happened either... 
after some resets i was able to boot the system. now its been days with no problem. thanks anyway

---

