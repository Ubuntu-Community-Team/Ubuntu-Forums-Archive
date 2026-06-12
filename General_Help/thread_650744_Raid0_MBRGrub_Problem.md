---
title: "Raid0 MBR/Grub Problem"
date: 2007-12-26
forum: General Help
---

### Post by LuckyX2 on 2007-12-26
On my computer I have one ide drive and two sata drives that are in a Raid0. I installed xp onto the Raid0, and partitioned the ide drive into a ntfs partition with vista, an ext3 partition and a swap partition. I installed Ubuntu 7.10 on the ext3 partition and wrote the grub loader to the default drive (hd0). I restarted and got a disk boot failure. Restarted again but this time changed the boot order of the drives in the bios. Then it froze loading grub with grub error 21. Then I decided to reinstall Ubuntu but this time write the Grub loader onto hd1. That was a bad idea, now the only way to get my computer working is to turn off the raid in the bios. When I do that Grub loads but only recognizes Ubuntu which is what im using at the moment. When I leave the Raid0 on it freezes on the raid loading screen at boot-up. Please, can someone tell me how to fix this so I can boot into Vista or Xp. All of my important files are on the Raid drives which I currently have no idea how to access them

thank you very much

---

### Post by LuckyX2 on 2007-12-27
bump

anyone?

I was thinking that if i deleted grub off of the raid disks that it would fix it, I just want to get rid of ubuntu completely and reinstall it correctly afterwards. Will super grub disk help with getting rid of grub? I already tried repairing the installation with vista and xp to no avail. I thought that would definitely work by overwriting the MBR with the Vista/Xp MBR.

thanks everyone

---

### Post by fjgaude on 2007-12-27
Maybe this post will lead to understadning:

[http://ubuntuforums.org/showthread.php?p=4023200&highlight=raid#post4023200](http://ubuntuforums.org/showthread.php?p=4023200&highlight=raid#post4023200)

What we have here is grub and mbr being done correctly for the install. Lots to learn when doing these kinds of things... it has taken me much time to stop the panics. Read the man page for grub than for update-grub and grub-install. It's marvelous that Linux has all this power but we first have to first understand how to use the power. <smile>

---

