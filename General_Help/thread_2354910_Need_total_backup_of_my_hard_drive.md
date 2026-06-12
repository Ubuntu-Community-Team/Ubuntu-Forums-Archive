---
title: "Need total backup of my hard drive"
date: 2017-03-07
forum: General Help
---

### Post by steve169 on 2017-03-07
I am trying to set up a total backup system for my solid state hard drive, which has both Windows 7 and Ubuntu 16 installed.

I would want to make weekly incremental updates to keep the backup up to date.

The layout of the disk:

[INDENT] sda1 is the Windows 7 installation (58.59 GiB, ntfs).

[/INDENT]
[INDENT]sda2 is where I keep data files for both Windows and Ubuntu (329.57 GiB, ntfs).

[/INDENT]
[INDENT]The rest of the drive is dedicated to the Ubuntu 16.04.2 operating system (55.09 GiB, ext4 and 3.87 GiB linux-swap).
[/INDENT]

I have a 3-terrabyte external hard drive where I keep backups.

Before I installed Ubuntu, I used Norton Ghost 15. It's great for Windows, but it won't back up the Ubuntu system.

[B]My goal is to have a complete backup of this hard drive so that if/when there's a crash or a virus attack, I can restore the entire hard drive from my backup.
[/B]
Is this possible?

---

### Post by SuperFreak on 2017-03-07
[Redo]("http://redobackup.org/") which is graphical will work but sometimes has some quirks to it's operation.
[Clonezilla]("http://clonezilla.org/") is another option but is not graphical

Both work from Live disks or Live Usbs
Make sure you have enough space on the backup disk

---

### Post by steve169 on 2017-03-07
Dear SuperFreak,

Thanks for the tips. I'll give them a try.

---

### Post by SuperFreak on 2017-03-07
Personally I use Redo and haven't tried Clonezilla. One problem with Redo I have found is sometimes during backup my screen goes black and there is no way of being certain when the backup is finished(PC doesn't respond to mouse or keyboard once it goes black). Only way I have found to avoid this is to move the mouse while the screen is working every 15-20minutes. I believe that others have complained about this on the Redo forums but I don't think the software is currently being developed. Clonezilla may be a better bet but it has a bit more of a learning curve. I still use Redo and have restored a PC with Win 7 with it.

---

### Post by Kris_M on 2017-03-07
I use Clonezilla. Ubuntu/win7

---

### Post by howefield on 2017-03-08
Clonezilla is a tremendous application, I use it most days but the flaw in using it with your stated criteria is that it lacks support for incremental backups. I generally take an image of the OS after a pristine install and then further images every month or so depending on the number/size of the updates since the previous image. Each image checked for restorability and the previous image(s) deleted. That takes care of the OS

Many would scoff at imaging the OS given how "easy" it is to reinstall.

Data is taken care of separately with rsyncs to a NAS and several external storage disks. Generally, it is the data that's important.

---

