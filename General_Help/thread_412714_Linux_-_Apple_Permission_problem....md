---
title: "Linux - Apple Permission problem..."
date: 2007-04-18
forum: General Help
---

### Post by madcow72 on 2007-04-18
I recently made an external hard drive for a friend and placed some videos and TV shows on it for him.  I have an Ubuntu box, but he uses a MacBook.  The first time I tried formatting the drive like normal in gparted and placing the videos on, but it was unreadable by his computer.  So then I tried formatting the drive to NTFS using a Windows XP box and placed the videos on again using my Ubuntu box.  This time, he can view the files and view the videos, but does not have permission to write to the drive.  I apologize that this is such a simple permissions question, but how does he change permissions so that he will have full access to the drive?

Thanks!

---

### Post by TheWizzard on 2007-04-18
i'm not sure what kind of structures apple can read / write. fat32 is usually ok to use on different os's.

---

### Post by madcow72 on 2007-04-18
You're right about the filesystem being the problem.  I've realized that Macs can read NTFS systems, but can't write natively to one.  I found out about [MacFUSE]("http://code.google.com/p/macfuse/") from Google which uses ntfs-3G and is supposed to allow users full access to the NTFS filesystem.  The second problem, I just realized, is that his home computer is Windows ME.  (Yes, I've made sure he understands that of all the bad Windows distributions out there, this is the worst - still no change.)  Windows ME was before NTFS and so doesn't read or write natively.  Probably, the easiest thing to do is just pull all files off the drive, have him reformat it, and then place the files back on.

So, I'm changing the purpose of this Thread to the following:

What is the best filesystem for full accessibility across Linux, Windows, and Mac OSX?  Fat32 will work, but I believe it is an inefficient filesystem and a lot of space is lost.

---

### Post by TheWizzard on 2007-04-20
> **madcow72 said:**
> What is the best filesystem for full accessibility across Linux, Windows, and Mac OSX?  Fat32 will work, but I believe it is an inefficient filesystem and a lot of space is lost.

i'm afraid you'll have to stick to fat 32 for full accessibility across Linux, Windows, and Mac. 

it's not a big problem to use fat32 for data storage. however, fat32 does get defragmentated quickly, so use ext3 for the files you're working on.
see:
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

