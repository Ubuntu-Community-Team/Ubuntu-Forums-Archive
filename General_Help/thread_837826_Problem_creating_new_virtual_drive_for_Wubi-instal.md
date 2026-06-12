---
title: "Problem creating new virtual drive for Wubi-installed Ubuntu"
date: 2008-06-22
forum: General Help
---

### Post by fritzophrenic on 2008-06-22
I have installed Ubuntu with Wubi so that I can give Linux a try before I "go all the way," so to speak.

Part of the Linux experience for me will be trying to get all my games working, for which I understand I need to use Wine. Regardless, when I ran Wubi, I (perhaps stupidly) only gave it a 5GB virtual disk. Good for my first few weeks of playing with Ubuntu, but now it's time to try re-installing my games, and I need more space.

So, I followed these instructions to create a new virtual disk, with the intention of just giving it over to Wine to use as its fake C: drive:

[https://wiki.ubuntu.com/WubiGuide#head-5aac3daad4eb9fcc3502ba1a4d6891b71b050b1d](https://wiki.ubuntu.com/WubiGuide#head-5aac3daad4eb9fcc3502ba1a4d6891b71b050b1d)

Using these instructions, I believe that I successfully created a 9GB virtual disk named wingames.disk.

Then the trouble started.

In Ubuntu, I cannot locate the disk image created. I can locate the file in /host/ubuntu/disks perfectly fine, and verify that it shows 9GB. But, there is no disk mounted to use this space.

I consulted #ubuntu on freenode, and they had me try to mount it manually with mount -a. I tried a few variations of this as well, some using the full path to /host/ubuntu/disks/wingames.disk, but none of them did anything. I got a message saying that there was no entry for this disk in /etc/fstab.

Before manually editing the /etc/fstab file without knowing what I was doing, I checked the file in Windows to make sure I could see the disk file there. Now, it gets more interesting.

Windows reports that the file size is 9GB exactly (good) but it also reports "size on disk" as 204.4MB. Yes, a 9 gigabyte disk image apparently only takes 200 megabytes to store.

Just to make sure there wasn't something funny about the type of file in general, I checked, and the file created by Wubi, root.disk, shows as 5.12GB on disk, for a 5.12GB file. No surprises there.

Any help would be appreciated. I would _love_ to know what is going on, but I will also accept a better solution to my initial problem.

Before it is suggested: No, I am not yet ready to create a "real" Ubuntu install using a partition. I like Ubuntu so far, but until I use it to play my games (the primary purpose of this old computer I'm on right now), I am not ready to make the switch. And if I switch, I will most likely just wipe away Windows entirely from this computer and use Linux exclusively on it, though I may try another distro or two first.

---

### Post by fritzophrenic on 2008-06-26
Anyone?

---

### Post by minhmeoke on 2008-06-29
Why not just resize your existing /home with lvpm? [http://lubi.sourceforge.net/lvpm.html]("http://lubi.sourceforge.net/lvpm.html")

Also, are you using any type of compression on your windows filesystem? Since qemu basically creates a big empty file, windows might just compress it to save space.

---

### Post by ago on 2008-06-30
The steps are:

1 create a file:
dd if=/dev/zero of=/host/ubuntu/disks/mynewdisk.disk bs=1M count=10000

2 format the file
mkfs.ext3 /host/ubuntu/disks/mynewdisk.disk

3) create a mountpoint (an empty directory where the virtual disk will be mounted)
mkdir /mynewmountpoint

4) add it to /etc/fstab
/host/ubuntu/disks/mynewdisk.disk /mynewmountpoint ext3   defaults,loop  0 0

5) mount
mount /mynewmountpoint

---

