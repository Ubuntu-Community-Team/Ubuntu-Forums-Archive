---
title: "Issue changing permissions on external hard drive Ubuntu 12.04"
date: 2013-08-04
forum: General Help
---

### Post by chimmy on 2013-08-04
Hello,
I'm trying to use an external hard drive (formatted from my installation of ubuntu 12.04) to backup a macbook pro. I tried using it with the macbook but found I can only read from the drive when it is mounted there.. When mounted in ubuntu, I do the "ls -l" command and I get:


drwx------ 1 crang crang 4096 Aug  3 23:02 hard_drive_name


(crang being my username, I own the thing!!)

As you can see, I can read, write and execute from this one computer, but as far as I understand I can't do anything on another computer.. so I've been trying to change the permissions on the drive. In the ubuntu terminal I put in:


sudo chmod -R 777 /media/hard_drive_name


I get no error messages but afterward the drive still seems to have all of the same permissions.
In verbose mode it shows all files having their permissions changed. for example:


 mode of `/media/hard_drive_name/home/sammyd/CortexCommand/Techion.rte/Effects/Glows/.svn/tmp/props' changed from 0700 (rwx------) to 0777 (rwxrwxrwx)


Can anyone tell me what is going on? Or offer an alternative solution for using the hard drive with the Macbook? Thanks!

---

### Post by Bucky Ball on 2013-08-04
You say you formatted it in Ubuntu but don't say what as. EXT*, NTFS, HFS? What? You also mention it is an external hard drive but not how it is connecting. USB (2 or 3), eSATA, Firewire? ;)

---

### Post by chimmy on 2013-08-04
Thanks for your reply! The file system is EXT4. The hard drive is an IDE hard drive that I'm connecting to the system through a "USB 2.0 drive mate," which converts normal IDE and SATA hard drives into USB drives. 

I should update you on my more recent attempts... I attached the hard drive to the motherboard with an IDE cable and tried the chmod command again. I got the same result...
Is there anything you can suggest? Any more info required?

---

### Post by Bucky Ball on 2013-08-05
Is the HDD known to work? Have you tried another drive with the drive mate?

If it is not working with the Drive Mate, OR the motherboard, could be hardware prob. IDE HDDs are generally aged now.

---

### Post by Bucky Ball on 2013-08-05
Is the HDD known to work? Have you tried another drive with the drive mate?

---

