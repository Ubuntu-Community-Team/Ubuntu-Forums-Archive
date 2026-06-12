---
title: "GRUB problem : Stage 1.5 in infinited loop"
date: 2007-05-07
forum: General Help
---

### Post by metalseb on 2007-05-07
Hi everybody. I'm facing a weird problem with GRUB since a few weeks now. Started when I upgraded my kernel 2.6.17.10 => 2.6.17.11 on my Edgy.

Now, at boot time, I get a "stage 1.5 loading" message in infinited loop, you know printed all over the screen again and again and nothing happens. Filesystem is okay since I still can boot my OS with a 'Grub Boot Disk' [-o< 

Trying to reinstall GRUB, either by shell or by grub-install does not help. device.map is okay. menu.lst is okay (Since I can boot with the help of GBD).

My hardware configuration is as follow (cut'n'paste from fdisk -l, things are in French)

```

Disque /dev/sda: 250.0 Go, 250059350016 octets
255 têtes, 63 secteurs/piste, 30401 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disque /dev/hdc: 80.0 Go, 80026361856 octets
255 têtes, 63 secteurs/piste, 9729 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/hdc1               1        9347    75079746   83  Linux
/dev/hdc2            9348        9729     3068415    5  Extended
/dev/hdc5            9348        9729     3068383+  82  Linux swap / Solaris

```

Before the kernel update this configuration was working okay. So I bet something has changed, but what ?

Any help would be greatly appreciated. Googling does not help either and booting from CD is ... well .... boring ?

Cheers mates

---

### Post by gallan on 2007-05-07
This sounds a bit like my problem

The loader gets to GRUB 1.5 while booting then starts a reboot, indefinitely.  I must use the Ubunt disk and reinstall Ubuntu to break out.  Then the system works once and I can boot properly to XP or Ubuntu; the next time I reboot I am again in the loop

Gary

---

### Post by Bigbluecat on 2007-05-07
We need a little more information in order to help with this.

Can you post the contents of your menu.lst back here.

Also. When in the liveCD open a terminal and enter:

> sudo grubThis will bring up the grub command line. Then:

> find /boot/grub/stage1This will tell us where grub thinks the boot files reside.

Post the result back here also.
Lastly:

> quitWill get you out of grub.

Once we have this info we an try to see what is amiss.

---

### Post by metalseb on 2007-05-07
Problem is solved. 

When I tried to reinstall grub using the shell (booting from a rescue CD), I got a strange 'cannot embed e2fs_stage1_5, this is not fatal'. Obviously it was, indeed !

File was present in /boot/grub however, but I copied the one found in /lib/grub/i386-pc over the original one.

Then, starting another setup(hd0) did not displayed the 'cannot embed' error message.

Things just started to work again since then. I am now able to boot again from the hard disk.

Strange isn't it ?

---

### Post by Bigbluecat on 2007-05-07
Glad to hear it is solved

---

### Post by ronmarley1 on 2007-05-30
This same issue has happened to me two times over the last two days.  I restored GRUB using the Super Grub Disk.  After that, all is well.  I'm just wondering what the cause is.

---

### Post by Gauchoo1234 on 2008-07-05
> **gallan said:**
> This sounds a bit like my problem

The loader gets to GRUB 1.5 while booting then starts a reboot, indefinitely.  I must use the Ubunt disk and reinstall Ubuntu to break out.  Then the system works once and I can boot properly to XP or Ubuntu; the next time I reboot I am again in the loop

Gary

Hello Gary, I have EXACT THE SAME problem!

How did you solve it?

---

### Post by Gauchoo1234 on 2008-07-07
> **Gauchoo1234 said:**
> Hello Gary, I have EXACT THE SAME problem!

How did you solve it?

up

---

### Post by Gauchoo1234 on 2008-07-08
> **Gauchoo1234 said:**
> up

up

---

### Post by Gauchoo1234 on 2008-07-11
> **Gauchoo1234 said:**
> Hello Gary, I have EXACT THE SAME problem!

How did you solve it?

up :(

---

