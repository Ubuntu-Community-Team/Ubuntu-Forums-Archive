---
title: "Where is the windows installed ubuntu partition on the drive?"
date: 2014-01-30
forum: General Help
---

### Post by kurzanski-thomas on 2014-01-30
Hello,

I installed ubuntu from windows on my laptop's drive (on a 40Gb partition). Then My latop died and I took the drive and put it on an ubuntu running computer (with its own separate drive). So now I would like to recover the files I had on the ubuntu partition. I'm browsing the drive, I can see the windows files but not the ubuntu ones. Where are they located? Is it possible to recover them ?

Thanks!

---

### Post by westie457 on 2014-01-30
Welcome to UF.

When you did the installation did you use the Windows based Installer (wubi.exe)?

If you then look in the Windows Folder for one named Host. The files should be in there.
It should be possible to recover them.

My memory on this is a bit hazy as have not used Wubi for 3 years or more.

---

### Post by Impavidus on 2014-01-30
In case of wubi there is no real Ubuntu partition. It's a virtual partition.

Mount your Windows partition on your working Ubuntu machine. I think there must be an Ubuntu directory somewhere, where you can find a file named root.disk (I think, I never used wubi myself). It must be a large file, somewhere between 5 and 30GB, containing the entire wubi-ubuntu file system. Mount this file at any convenient mount point and you should be able to access your files. You may need root permissions.

---

### Post by oldfred on 2014-01-30
If you made a 40GB partition, that must have been a d: drive in Windows as the largest wubi can be is 30GB. It is root.disk.

mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)
mkdir /mnt/windows
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

or:

[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

---

### Post by Frogs Hair on 2014-01-30
> [COLOR=#000000] (on a 40Gb partition)[/COLOR] Wubi has 30Gb maximum unless manually expanded. If you did install with Wubi see the other posts.

---

### Post by kurzanski-thomas on 2014-01-30
Well it seems it was a 30 gb partition. Thank you all, I did what [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711") suggested i.e. :
mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/ubuntu

And it worked!

---

