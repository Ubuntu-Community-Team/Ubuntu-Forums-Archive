---
title: "USB port that works on several PCs including Surface Pro 3"
date: 2016-11-11
forum: General Help
---

### Post by michox on 2016-11-11
Hey im currently trying to build a USB port that works on several PCs. The difficulty is, that it has to run on a Surface Pro 3. To get the touchpad working there, i need to update the kernel to an experimental driver. This works fine, but once it is updated, on any other PC it would only boot into emergency mode. If i try to update a persistent live system, the system gets crashed and won't boot anymore... Maybe im doing something wrong but i propably need 2 Systems on my Stick anyways. So i thought about creating a USB where the first partition ist a FAT32 Persistent Live USB with some extra space, so i can hide the Linux data in Windows and use it as a regular datastorage. 2nd part then would be a fully installed Version, updated to the experimental driver for the Surface. I found [this]("http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13426191#post13426191") Image but after i installed the Kernel i couldn't update the grub.cfg because there was no XXX.efi.signed for my Kernel version and it wouldn't boot either... The Keyboard wouldn't work while running on the livesystem of the above image, propably because the versions where to old for the surface cover... On my PC i have some troubles running Linux as well, but i think its because of my strange mainboard. Nearly every System i create needs different settings, and i couldn't get my internet running yet. Neither with ethernet, Wifi nor with tethering from my phone...

As im pretty new to Linux (about a week in, as long as i work on this problem now...), some help creating such an Image would be really nice.

---

### Post by sudodus on 2016-11-11
Welcome to the Ubuntu Forums *michox* :-)

I think your problem is big enough for a separate thread. So I will ask a moderator to move these two posts (yours and this one) to a separate thread and give it a good title, for example

***USB port that works on several PCs including Surface Pro 3***

---

### Post by sudodus on 2016-11-11
My old post is about old versions of Ubuntu (14.04.2 and 15.10 have old kernels).

Have you tried the newest versions of Ubuntu? Maybe the new long time release Ubuntu 16.04.1 LTS will work 'out of the box', or even more likely, Ubuntu 16.10. I suggest that you try them live and installed into USB pendrives. See this link

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by michox on 2016-11-12
alright i did it... I made a full install on a Stick with Volume for Storage and Surface Pro 3 support.
i basically followed [this ]("https://ubuntuforums.org/showthread.php?t=2309963#7")how to with a few changes. First of all i installed it on my PC and unplugged all other harddrives. Then the EFI partition was set up correctly, but still those [B]cp ../ubuntu/shimx64.efi bootx64.efi
cp ../ubuntu/grubx64.efi .
[/B]had to go into a folder called Boot in the directory above. Not sure if it changed something, but i also copied the shimx64 without changing the name. Either this or Ubuntu 16.10 instead of 16.04 seemed to do the trick! After the update i can boot into grub and there load either the surface kernel or the normal depending on what PC i am.
by creating an FAT32 Partition **before **creating the other partitions during installation and later formating to NTFS i made a Partition which i can use as a normal storage.
Only Problem, that it freezes sometimes, but that also might be a compatibility problem with my strange motherboard...

Thanks for helping :)

---

### Post by sudodus on 2016-11-12
Congratulations and thanks for sharing your solution :KS

---

