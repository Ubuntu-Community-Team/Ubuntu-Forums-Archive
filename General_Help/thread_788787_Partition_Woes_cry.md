---
title: "Partition Woes *cry*"
date: 2008-05-10
forum: General Help
---

### Post by samurailink3 on 2008-05-10
Something terrible has just happened. I made a huge mistake and deleted my partition table on my 500G external drive. It was a pure accident, but the changes were written. I've already tried to make fdisk create a new NTFS partition on the drive, but to no avail. I used only fdisk, not mkfs, I know this deletes data. It would be ok if I only used this for games and such, but it is a complete backup of my home machine, my music, classwork, pictures, you get the idea. Does anyone know of anything to help me get my partition back? Or at least a way to pull off the data and burn it to DVD?
Help me UbuntuForums.com, you're my only hope.

---

### Post by Herman on 2008-05-10
Deleting your partition table would not have been a very difficult problem if you had asked for help right away. [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk") can be installed in Ubuntu or in the Ubuntu Live CD and TestDisk can scan a hard drive for the start sectors of deleted partitions and offer you a list of them. You can decide which ones you would like to have written to a new partition table.

Here's a link to a page where I have recorded a couple of examples of how TestDisk worked for me when I tried it out, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html").

If TestDisk can't do it for you, you can probably still recover your files with photorec, which is a progam that comes with TestDisk.

You can read about TestDisk and PhotoRec at TestDisk's website: 
**[[B]TestDisk** - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk")[/B]


Regards, Herman :)

---

### Post by samurailink3 on 2008-05-10
Ah ha! I will install that! I have stumbled upon a program known as Active@ Partition Recovery. After running that, it found and mounted the drive successfully. Next time, I'll be more cautious. Thanks for the tip, I'll be sure to install it! Thanks!

---

### Post by Herman on 2008-05-10
:) Okay, I'm glad you got your files all back safe 'n sound.

Ubuntu Rescue Remix has TestDisk in it and some other good recovery programs as well.
If you want all the best professional recovery software, get Ubuntu Rescue Remix, and practice with it on an old hard disk when you have some spare time.
That way you'll already know what to do when you or a friend of yours has an emergency.
Like a fire drill, it helps if you practice when it is only a mock 'emergency'.
Ubuntu Rescue Remix was command line only the last time I tried it out, I think it still is.
[Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/").

---

