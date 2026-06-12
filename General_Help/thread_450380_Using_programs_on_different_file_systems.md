---
title: "Using programs on different file systems"
date: 2007-05-21
forum: General Help
---

### Post by Nehvrook on 2007-05-21
Hi, just a quick question. I heard that writing files to an NTFS hard drive from Linux can really mess with that (the ntfs) partition (Though I've also heard there are some new drivers that will let you read/write without issues).

I have a dual boot PC with Linux on one hard drive and windows on the other. I have some drivers on Windows that let me see my Ubuntu hard drive's file system (Which I think is ext3). If I install and run windows programs on the Ubuntu hard drive (So the files are saved on the Ubuntu hard drive but the programs are run from windows) will this cause the same (Or any other) problems as writing files from Linux to windows? Or is this safe to do?

---

### Post by phidia on 2007-05-21
It seems like it should work without problems. If the programs are in your normal user directory and windows doesn't have the ability to change the linux install system files everything should be good.
You might want to check this [http://ubuntuforums.org/showthread.php?t=443571&highlight=ntfs+read+write](http://ubuntuforums.org/showthread.php?t=443571&highlight=ntfs+read+write) 
for read write of NTFS in ubuntu.

---

### Post by ghell on 2007-05-21
NTFS is closed source so things like ntfs-3g are basing themselves on educated guesses and trial and error.

I think NTFS has a mechanism in it to stop writes from damaging the system, which means if its going to break it it just cancels the write. This makes writing to NTFS unreliable from outside of windows. Recent versions of ntfs-3g etc don't seem to have many problems (I'm sure they do have some problems though) writing to NTFS so I don't know if it is still recommended to mount NTFS partitions as read only on linux.

However, reading the NTFS partition should be fine and since your linux file system probably isn't closed source it should, in theory, be fairly safe to read from and write to from Windows, as long as the software you are using is pretty stable.

If you have enough space on both drives, I would keep your windows programs on the windows drive and linux programs on your linux drive and feel relatively free to move documents between them.

---

### Post by Nehvrook on 2007-05-21
Yeah, that's what I will be doing really. It's just that I use my Windows partition for gaming, and it's got a while yet but it will soon fill up. I was wondering if it would be alright to install a game to my linux hard drive and play it in windows. I know I can do it on my FAT32 external and it worked fine. It worked fine on my NTFS hard drive too. But I've re-formated that NTFS hard drive with Linux and I don't wanna skrew my Linux install up.

---

