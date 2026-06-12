---
title: "Change /home to existing NTFS partition?"
date: 2007-07-01
forum: General Help
---

### Post by onestep on 2007-07-01
I dual boot Windows Vista & Ubuntu Fiesty. On Windows I moved "My Documents" to it's own NTFS partition. In Ubuntu I have read/write access to "My Documents" using ntfs-config. 
I would like to use "My Documents" as my /home in Ubuntu AND still have access to it in Windows.
Is this possible? If so, are there any concerns I need to be aware of? Finally, how do I do this?

Oh yeah, I'm a Linux NOOB who's very impressed with Ubuntu Fiesty!

---

### Post by element3260 on 2007-07-01
I don't believe its possible because NTFS doesn't support permissions, and your home folder relies alot on permissions. When i first started using Ubuntu i tried to do something similar to that with a FAT32 partition and it killed my install (since I was a noob).

---

### Post by bodhi.zazen on 2007-07-01
Support is available to read-write a ntfs partition, but not use a ntfs partition as home or / partially due to permissions.

---

### Post by onestep on 2007-07-01
> **bodhi.zazen said:**
> Support is available to read-write a ntfs partition, but not use a ntfs partition as home or / partially due to permissions.

Is there a file system that can read-write in both Linux & Windows? If there is and I reformat the "My Documents" partition to it would I then be able to use it as /home in Ubuntu & "My Documents" in Windows?

---

### Post by bodhi.zazen on 2007-07-01
> **onestep said:**
> Is there a file system that can read-write in both Linux & Windows? If there is and I reformat the "My Documents" partition to it would I then be able to use it as /home in Ubuntu & "My Documents" in Windows?

ext3

use this to mount it in windows : [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by onestep on 2007-07-01
> **bodhi.zazen said:**
> ext3

use this to mount it in windows : [http://www.fs-driver.org/](http://www.fs-driver.org/)

That looks like it would work!
How would I then change my /home to the separate ext3 partition?

---

### Post by Bachstelze on 2007-07-01
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by bettlebrox on 2007-07-01
If all you want to do is to be able to see  your "My Documents" directory  in your Ubuntu desktop, and your Windows driver is mounted, you could make a symbolic link to it.

E.G.

If your Windows C: drive is mounted on /media/sda2, you can create a symbolic link like this:

[INDENT]ln -s /media/sda2/Documents\ and\ Settings/mtimony/My\ Documents/ ~/Desktop/[/INDENT]

>How would I then change my /home to the separate ext3 partition?
You would need to repartition your drive.

---

### Post by onestep on 2007-07-01
> **bettlebrox said:**
> If all you want to do is to be able to see  your "My Documents" directory  in your Ubuntu desktop, and your Windows driver is mounted, you could make a symbolic link to it.



What I'm trying to accomplish is to have one "MyDocuments" /home folder that is shared by both Windows and Linux and is on it's own separate partition. I would like to have each operating system in it's own partition.

Right now, I do have links in Linux /home that point to Windows "MyDocuments"
"MyDocuments" is on it's own partition, seperate from both Windows and Ubuntu.

---

### Post by bettlebrox on 2007-07-01
Just point the link to the "My Documents" directory on the Windows partition and mount the partition so that the user and group ownership is yours. A few years ago I tried to use the Windows driver for ext3 filesystems and it was really, really flakey (it could be better now).

---

