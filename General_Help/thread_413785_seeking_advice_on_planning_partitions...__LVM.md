---
title: "seeking advice on planning partitions...  LVM?"
date: 2007-04-19
forum: General Help
---

### Post by VCSkier on 2007-04-19
I've generally always had three partitions on my hdd.  One for the current stable release of ubuntu (my main usage), a second for the development release of ubuntu (or another distribution, for toying with), and then a third for my swap.  My issue though, is that when a new release comes out, I like to do a fresh install, and I think I''d like to create a common /home partition so I can more easily access my files from either distribution/release.  Additionally, then I will have less work whenever I do a fresh install as I will only have to reformat my /, not my /home, right?  I'm wondering though if I could simplify things by using a separate /boot partition too.

Will I need to be using LVM to do this?

Also, I have an external hd that I haven't used since I left Windows.  Will that complicate things?  I don't usually use it, but I'd like to be able to hook up to it every now and then, and just have it mounted as /media, or something.

Finally, will the location or order of my partitions make any difference?

Thanks!

---

### Post by zeekay on 2007-04-19
I use the Ubuntu LiveCD partition wizard, it's great.

I usually set up my HD this way:

swap                          1Gb
"/"             ext3          10Gb
"/home"    ext3 <all the free space to>

Might be a lil' too much for a swap ot for a linux one, but I rather have more than enough space for them.

About your ntfs HD, Ubuntu will most likely recognize and mount it, so you can copy and execute the files you want from it. :)

---

### Post by mac.ryan on 2007-04-20
> **VCSkier said:**
> Will I need to be using LVM to do this?

If I understood correctly what you want to do, I would say not... You will need 4 prtitions (ubuntu + 2nd distro + home + swap) so you can achieve that by simply setting up 4 primary partitions (the limit for each physical drive) or any other combination of primary + extended partitions.

I don't see the purpose of a separate /boot partition (normally you make that when you have your tree distributed on the network, so that you keep the boot on the machine you work on, in case you lose the access to the network).

LVM would offer more flexibility in that you have higher level of freedom in moving/shrinking/merging partitions. I am currently trying to install this configuration myself, but it is less obvious that it seemed a the beginning... :-/

---

### Post by VCSkier on 2007-05-01
But I would like to be able to boot independently of my two root partitions.  What I mean is, if I reformat one, I'd still like to be able to boot to the other, regardless of which I reformat.

If I make a /boot partition, then it will be able to provide the booting to both, or either, /root partitions, right?  I will just have to remember to give that partition as /boot whenever I'm running a distro's installer?  Will the installer then just add it's boot data to the boot data currently on that partition?

---

### Post by mac.ryan on 2007-05-01
> **VCSkier said:**
> If I make a /boot partition, then it will be able to provide the booting to both, or either, /root partitions, right? 

Yes, you are right: grub (that in ubuntu is in the /boot directory, but could be anywhere else) need to be in a "safe place" if you want to keep it running even when you uninstall an OS. However, this still doesn't imply you will need to use LVM, as a combination of primary and extended partitions will work even better (not all the system recognise LVM units at boot up).

Also, if you would like to spare a partition, you could wish to have a boot-disk (CD, USB, floppy...) for those times of installation/uninstallation...

>  I will just have to remember to give that partition as /boot whenever I'm running a distro's installer?  Will the installer then just add it's boot data to the boot data currently on that partition?Not exactly. You don't tell the kernel where the boot loader is. You rather do vice-versa: you tell the boot loader the location of the kernel. So, what you should do, is just adding in the menu.lst file an entry with the reference data of the newly installed OS.

In my experience, I all the time left the newer OS to re-install grub (it might be a newer version, and at least I would be sure the installer would already configure properly the launch parameters of GRUB for itself). Then I would simply merge the previous menu.lst (with the right params for all the pre-existing OSs) with the newer one.

---

### Post by VCSkier on 2007-05-04
OK, this is what my partition table looks like now.

sda1 - "/boot"
sda4 - "/home"
sda2 - LVM
->sda5 - "/" (stable distro)
->sda6 - "/"root (testing distro)
->sda7 - swap

I've installed Ubuntu first (my stable, on sda5), but Ubuntu puts its kernel on /boot, and then when I run the installer for my unstable distro (Sidux, or Arch if I can get it working, on sda6) and have it mount /boot on sda1, it always reformats sda1 during the installation, and I lose my Ubuntu kernel.  So, do I need to move my kernels off of /boot, and into their respective "/" partitions?  If so, is there anything else I need to move with it?  Thanks.

---

### Post by mannheim on 2007-05-04
Sharing a /boot partition between different distributions can create more problems than it solves: each distro wants to update the grub configuration.

A better solution is to let the root filesystem for each distro just contain its own boot directory as usual, so each one has its own /boot/grub/menu.lst. Then install **grub in its own partition**. Eg, from the terminal command-line do something like:

```
sudo mkdir /mnt/tmp
sudo mount /dev/sda9 /mnt/tmp
sudo grub-install /dev/sda --root-directory=/mnt/tmp
```

This will write grub's first stage to the MBR in sda and write grub's other files in /mnt/tmp/boot/grub. Then you can do:

```
sudo gedit /mnt/tmp/boot/grub/menu.lst
```

and make the menu.lst look something like this:

```
default         0
timeout         6

title           Ubuntu Linux on hda6
savedefault
configfile      (hd0,5)/boot/grub/menu.lst

title           Ubuntu on backup partition hda5
savedefault
configfile      (hd0,4)/boot/grub/menu.lst

```

The configfile commands get grub to load and display the menus from the menu.lst file of the distributions on the other partitions. When all this is done, you have grub living on sda9, and you can boot to two distributions (on sda5 or sda6 in the example above), each of which has its own boot partition and its own menu.lst maintained independently.

---

