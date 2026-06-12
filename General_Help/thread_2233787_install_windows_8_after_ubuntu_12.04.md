---
title: "install windows 8 after ubuntu 12.04"
date: 2014-07-10
forum: General Help
---

### Post by lucas21 on 2014-07-10
hello guys :),

i have go ta little problem with installing windows 8.1 as second partition. i have already installed ubuntu 12.04. i heard that you could just create a second partition and install windows on it, but its apparently not than easy. if have a couple problems and questions. so first do i really need to delete all my ubuntu stuff to install windows? and are there any other ways to create second partitions than gparted?

thanks a lot :D

---

### Post by grahammechanical on 2014-07-10
> [COLOR=#000000] do i really need to delete all my ubuntu stuff to install windows?[/COLOR]


What are you talking about? Who told you that? You need a partition to install Windows in. And that most probably means that you need to shrink and move the 12.04 partition to create unallocated space that can be used to create a new partition. The best tool to do that is Gparted because it is a Linux tool. Do not try to resize or move a Linux partition using a Windows utility.

If we wanted to resize and move Windows partitions then it would be best to use Windows tools to do it. And, yes resizing and moving partitions does carry the risk that we will loose data. An OS may fail to load. It is a risk and that is why we get warnings about but it is not inevitable that we will loose data but backup is the sure policy.

Windows 8 will not install unless first we use the Windows tool provided to format the partition. Then the installer will allow us to install into it. You should also know that the Windows installer will insert its own boot loader which will not list any OS other than a Microsoft OS. So, you will no longer be able to boot Ubuntu. You will need to install Grub to the MBR

Regards.

---

### Post by lucas21 on 2014-07-10
thanks! i have some problems with gparted, thats why i'm asking. im not able to do anything (unmount, resize or delete) there are many errors and i'm trying to fix them right now...

---

### Post by Zukaro on 2014-07-10
It sounds like you're trying to unmount the partition which contains root.
Is this an error message you get?

> The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.

If so the solution would be to boot up from a LiveUSB or LiveCD of Ubuntu or another Linux distro (GParted Live would be good for this task), start GParted and resize your partitions this way.  As you wont be running off the partition you're trying to unmount, which is likely what's happening.  Then you'll be able to resize it.

I suggest making a backup first however, as it's always possible to lose data when resizing partitions and such.

---

### Post by oldfred on 2014-07-10
You cannot use gparted if you install it in your working system to modify the working system. You then need to use it from a liveCD, DVD or flash drive. You can use a gparted in your install on other drives or unmounted partitions. But you cannot unmount your working partition.

Is Ubuntu installed in BIOS or UEFI. 
Is drive partitioned MBR for BIOS or gpt for UEFI. Although Ubuntu will boot from a gpt drive with either UEFI or BIOS, Windows will not.
Best to install Windows in the same boot mode.

You still have to make sure you have Windows 8 fast boot or always on hibernation off if dual booting (even if two Windows versions).

---

### Post by lucas21 on 2014-07-10
thanks so much for your help! :D

---

### Post by pauljwells on 2014-07-10
All good points. I've been installing and dual-booting linux and windows for years and I still get cold sweats thinking about stuff like this! (FWIW, I'm considering installing W8 onto a blank partition on my, currently perfectly functioning 14.04 install!) BACK UP EVERYTHING!!! would be my advice. Even if you get the install to work first time, you'll probably realise that you would rather have done something differently anyway, so if you can wipe and reinstall everything you'll have a better system / be a happier person as a result. It took me several attempts on a single OS installation of 14.04 on a UEFI system to get everything 'just right'

---

### Post by lucas21 on 2014-07-18
after doing everything needed before installing windows i have only one problem left. launching windows doesn't work ... :(
i downloaded the .iso and put it on a cd but if im trying to launch it from there, it is showing a almost black screen for about 10 seconds and after that launches ubuntu.

im not sure why but i would be very pleased for telling me why :D

---

### Post by oldfred on 2014-07-18
If CD it may not be correct? I thought Windows needs at least a DVD and now like Ubuntu most installs use flash drive. If not correct booting, then it just reverts to next device in boot order or hard drive.

Is Ubuntu in BIOS or UEFI boot mode? DVD or flash drive must be in correct boot mode.

Windows 7 DVD defaults to only install in BIOS mode, and must be copied to flash drive and modified to boot in UEFI mode.

If BIOS:
Do you have a NTFS formatted primary partition with the boot flag. Or unallocated space and available primary partition(s)? Windows only installs to primary partiitons with MBR partitioning.

---

### Post by coffeecat on 2014-07-18
> **lucas21 said:**
> 
i downloaded the .iso and put it on a cd 

Do you mean a Windows 8 ISO? It wouldn't fit on a CD. If you mean a DVD, then how did you burn the ISO to the DVD? Where did you get the ISO?

---

### Post by lucas21 on 2014-07-18
it sais the windows8.iso about 2.7 MB tall and i downloaded it from a not official site, but it worked for everyone so i think its not cause of the actual .iso file

---

### Post by lucas21 on 2014-07-18
also how do i know my boot mode?

---

### Post by lucas21 on 2014-07-18
sry GB not MB

---

### Post by coffeecat on 2014-07-18
> **lucas21 said:**
> it sais the windows8.iso about 2.7 MB tall and i downloaded it from a not official site, but it worked for everyone so i think its not cause of the actual .iso file

I take it "Not official" means neither Microsoft nor an accredited Microsoft distributor of Windows images. 

Sorry - we don't support that here. From the forum [Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules"):

> We do not support circumventing TOS, EULA, etc here. 

Thread closed.

---

