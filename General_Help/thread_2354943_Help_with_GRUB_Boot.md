---
title: "Help with GRUB Boot"
date: 2017-03-07
forum: General Help
---

### Post by epicdragon44 on 2017-03-07
Hello everyone!

Recently, I installed Fedora on a separate partition from my main partition, Kubuntu. However, I didn't post this in the Kubuntu section because this pertains to ALL Ubuntus and Fedoras...
How do I change who is in charge of the Boot? Like, the Boot menu/Grub menu?

Currently, after installing Fedora, the Fedora GRUB menu has taken over the boot menu, and it's ugly. I want Kubuntu to be in charge of the boot menu/ boot sequence and everything else.

So how do I change who is in charge of booting, especially the Boot menu?

Thank you!

---

### Post by mikewhatever on 2017-03-07
You could use the <grub-install /dev/sdX> command in Kubuntu. It would take charge of the initial boot process, but I don't know about "everything else", whatever you mean by that. That command should also detect Fedora's boot loader, and add it to bootmenu. For more info, take a look at 
<grub-install --help>. The <sdX> part is usually the HDD's MBR you want to boot from, for example /dev/sda, /dev/sdb, etc.

---

### Post by DuckHook on 2017-03-07
*While running within Kubuntu*, you only need do:```
sudo grub-install
```Because you've installed it before, you need not specify /dev/sd[x] again (unless you really want to). The GRUB in your MBR or wherever you have it will be replaced with the Kubuntu version.

The next time a Fedora GRUB update is pushed out, it will take over GRUB again and you will have to repeat the above process. Since GRUB is not updated that frequently, it is only a minor annoyance.

---

### Post by epicdragon44 on 2017-03-08
Thank you!

---

### Post by epicdragon44 on 2017-03-08
It says Grub-install: error: install device isn't specified. How do I fix this?

---

### Post by DuckHook on 2017-03-08
Then you need to figure out where you initially installed GRUB to when you installed Kubuntu. For example, if your Kubuntu install is on /dev/sda, then:```
sudo grub-install /dev/sda
```This is just an example. You must use your own proper /dev/sd[x].

---

### Post by efflandt on 2017-03-08
If you have more than one Linux OS on your system, they should NOT use the same location for grub, or only have grub installed on one of them (that you use most often). Otherwise each OS would step on the other when updating grub and you may not know which is in control at any given time. The only disadvantage to only having one grub is that when your secondary system does major updates (like new kernel) that requires reboot, you will need to boot the primary Linux and (sudo) update-grub.

For example while trying out both Lubuntu and Ubuntu in different partitions with a common /home partition on 32 GB SD booted on a tablet PC, I only installed grub in the mbr from one of the systems and not the other. Its internal 32 GB SSD has Win7 Pro. I have to hold the Windows button while turning it on, or have a keyboard attached to press F12, to select the SD if I want to boot that instead of SSD.

---

### Post by epicdragon44 on 2017-03-09
Oh I see. Thank you!

The problem resolved itself anyways because Kubuntu stopped working for some reason, and seeing that I didn't have much in it in any case,  I did a re install and now it is working perfectly. Thank you all for the help anyways, this is why Ubuntu is the best!

---

### Post by oldrocker99 on 2017-03-09
It's great that you've solved your problem. Please mark this thread as [SOLVED] using the Thread Tools at the top of this thread, so as to help other users.

---

