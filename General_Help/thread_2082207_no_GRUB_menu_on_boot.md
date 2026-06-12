---
title: "no GRUB menu on boot"
date: 2012-11-08
forum: General Help
---

### Post by badtedd on 2012-11-08
Ok, i am kinda of a newbie when it comes to ubuntu and linux, (been using it for few months and like it), but i have a problem during boot, no menu shows up when grub starts. I have a win7/ubuntu 12.04 64bit dual boot, tried holding shift key(no effect), tried pressing and holding esc(nada), tried using live cd to repair grub, no effect, tried boot repair, only to get a msg asking me if a hard drive with 12.04 is removable drive(which it is not) after clicking recomended repair msg comes up asking me to download a 64bit version of boot repair(i tried to no avail) this is my boot info [http://paste.ubuntu.com/1343748/](http://paste.ubuntu.com/1343748/) and if anyone could help me or point me in the right direction/post would be much appreciated.
I will be away from computer for a few days(business trip), so pls have some patience with me and my replys...thx

---

### Post by oldfred on 2012-11-08
You have Windows in BIOS/MBR on sda and gpt partitioning in sdb. You do have an efi partition and a bios_grub partition. The efi partition would be  used to boot if you were using UEFI which it seems you system has.

But since Windows is in BIOS mode it is best to keep Ubuntu in BIOS mode. With gpt partitioning you need the bios_grub partition and that looks like it is correct.

The other issue we seem to have with some systems is very large / (root) partitions. My normal suggestion is to have a smaller / (root) of 25GB or so and use the rest of the drive for /home, data or other users, but keep root smaller.

You can easily test if smaller root solves your issue, by using gparted to shrink your sdb4 to less than 100GB.

Note that parts of grub & kernel are above 100GB in drive, gparted will move those when you shrink partition.

```
=================== sdb4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 134.728878021 = [COLOR=Red]144.664031232  [/COLOR]boot/grub/core.img                             1
 362.431781769 = [COLOR=Red]389.158162432[/COLOR]  boot/grub/grub.cfg                             1
  22.814990997 = 24.497410048   boot/initrd.img-3.2.0-29-generic               2
  30.317119598 = 32.552759296   boot/initrd.img-3.2.0-32-generic               2
 194.193092346 = [COLOR=Red]208.513245184 [/COLOR] boot/vmlinuz-3.2.0-29-generic                  1
  24.568103790 = 26.379800576   boot/vmlinuz-3.2.0-32-generic                  1
  22.814990997 = 24.497410048   initrd.img.old                                 2
  24.568103790 = 26.379800576   vmlinuz                                        1
 194.193092346 = [COLOR=Red]208.513245184[/COLOR]  vmlinuz.old                                    1
```

---

### Post by badtedd on 2012-11-15
hi, sorry for a long time since original post, but got back home, tried to shrink a partition with gpart, shrank it to 93gb, tried to reboot, still the same problem...(this was the result [http://paste.ubuntu.com/1359508/](http://paste.ubuntu.com/1359508/) ), downloded a yann's secure version of 64bit ubuntu 12.04, run live cd, run boot repair, rebooted, no success (result [http://paste.ubuntu.com/1359528/](http://paste.ubuntu.com/1359528/) )...at this point got sidetracked and lost my train of thought, said f... it all and reinstalled anew.....
oldfred thanx for your help and my appologies for taking a while, also sorry for not sticking longer with the problem and doing a fresh install, i am sure that there may have been a way to restore everything, but i just needed the comp.....

---

### Post by oldfred on 2012-11-15
Glad you have it working.

I still see grub4dos in there. With 2 drives you should not really need that. You can leave Windows boot loader in Windows drive and with grub2 in Ubuntu drive boot from Ubuntu drive. But what every you prefer is fine.

---

