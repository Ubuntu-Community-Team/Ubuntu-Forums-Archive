---
title: "Wubi 7.04.04 installer gives false &quot;not enough free space...&quot; error"
date: 2008-02-23
forum: General Help
---

### Post by Sorandal on 2008-02-23
Hi, I’m new to these parts.  I’ve been trying to install Ubuntu with Wubi-7.04.04.  When I try to open the installer I get an error that says: Not enough free space.  At least 4 GB are required.”  After deleting a few things on my 10GB hard drive I have 4.57GB free, and I’m still getting this message.  I’m running XP pro on a dell inspiron 8000.  Any thoughts are greatly apreciated!

---

### Post by ago on 2008-02-23
Wubi actually needs 5GB free, 4GB for minimum installation + 700MB for ISO + a bit of space not to starve your system

---

### Post by Sorandal on 2008-02-23
Thanks ago, that fixed the problem, unfortuanatly I had another install issue

I am able to get through the windows part of the instalation, select Xubuntu, and reboot, and select ubuntu (rather than windows).  When it gets to “storing base system” it loads to 74% (where it says “storing language”) and stays there.  After almost a half hour nothing changed, so I rebooted, loaded windows, and deleted some more files in case it still needed more disk space to complete the install.  I uninstalled the partially set up version of Xubuntu and redid the download and install as before.  It again froze up at 74% “storing language”.  Ring any bells?  

Also for future reference should this be a separate thread since my first question was answered, or is it better to keep them together since it is the same installation that we are talking about?

thanks

---

### Post by Sorandal on 2008-02-24
okay, so I freed up a bit more space and got to 52%, then freed a total of 5.51GB on my hard drive and I got to "Select and install software" and it stopped at 1% (configuring language-package-en-base).  Is it possible that it would need more than 5.51GB of disk space to install?  If so is there a lot more to the installation after this, I'd like to get some idea of whether it would be possible to free up enough space on this computer?
thanks

---

### Post by ago on 2008-02-24
It might also be a memory issue, 256MB is the bare minimum for Wubi. At that level your luck may vary.

---

### Post by Sorandal on 2008-02-25
I think you're right about the ram, I guess I'll have to use a different install method.  Thanks for your help!

---

### Post by Sorandal on 2008-04-05
Just wanted to let you know that it worked fine when I added a bit more ram.  Thanks for the help

---

### Post by dually on 2011-02-21
I too have been trying to run wubi.  After 5 hours there was a not enough disk space error and the install could not complete.

So I opened up the file tree and found a folder named Ubuntu on the C drive, which was 150gb or so in size!! In other words, all the free space on my hard drive.  Is wubi trying to create a partition with the entire remainder of my hard drive?

I wonder if the problem was caused by trying to run the installation off of an external usb drive.  Anyway, I was able to uninstall so now I'm trying to reinstall from a 2gb flash drive.

---

