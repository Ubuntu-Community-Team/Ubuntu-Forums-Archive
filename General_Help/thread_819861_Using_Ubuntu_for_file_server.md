---
title: "Using Ubuntu for file server"
date: 2008-06-05
forum: General Help
---

### Post by oobsniper2000 on 2008-06-05
Howdy.  I'm new to Ubuntu so forgive the ignorant questions.  My unix/linux skills would be considered "uniformed at best and dangerous at worst" :)  I've been poking around to get an idea of how to setup my system but there's a lot to learn and it's easy to go down rabbit holes for hours.  So, I figured that I'd post my target system here and ask for tips & pointers to more specific info about the things I really need to consider for this particular system.

I'm setting up a safe file backup system and I plan to use a cheap PC, Ubuntu, and external eSATA RAID boxes for a file server.  I will run it on my lan at home and will really only use it to backup data from Windows machines.  I know there are many ways to do this in general, but I've chosen to do this for these reasons (among others):

1.  I want the data stored on external, fully hardware RAID, independent from the server system.
2.  I want to start learning Ubuntu and unix/linux in general.

So, here are some specific questions just to get started:

1.  I want the data on the external raid box to be portable yet protected.  For instance, I want to be able to connect it to other machines (unix, windows, macs, etc.) and be able to access it with password protection.  And hopefully w/o installing drivers on the host system.  What's the best file system to use?

2.  Is SAMBA the best way to go?  I don't even know yet if it is the only way :)

3.  Should I use the Ubuntu server, or desktop version?

There are plenty of other questions I don't even know to ask yet...

And sorry if y'all already have plenty of threads on this exact topic!

---

### Post by cmnorton on 2008-06-05
These forums in particular and some other forums are a good place to learn about Ubuntu and linux.

You can nstall regular desktop Ubuntu, and then add server components, especially build-essential. In this way, you'll start with a graphical environment. I have a KDE workstation, even though I spend most of my life at the command line, but it is helpful to have a GUI to do other work. With a graphical environment you can use command line (x-terms) all you want.

I can see some advantages to installing Ubuntu server, and then installing the desktop things you like. I have never tried it and cannot imagine its not being possible, but I'd start with the desktop install approach first.

If you are sharing from Windows to Linux, SAMBA is the best way to go, and you can do linux to linux SAMBA sharing as well.

---

### Post by cariboo on 2008-06-05
On the other hand I would install the server version first and then add a lightweight gui. I used Windomaker for years even though I spent most of my time in a terminal. Using the server distribution makes it easier to setup file sharing whether it is samba or nfs. Moving your external raid array to different computers may not work the way you expect it to, as i know for sure that windows cannot read hard drives formated as ext3, I'm not sure about OSX.

Jim

---

### Post by indytim on 2008-06-06
> 
as i know for sure that windows cannot read hard drives formated as ext3, I'm not sure about OSX.


Sorry mate, not exactly true.  Checkout [http://www.fs-driver.org/]("http://www.fs-driver.org/") .  I've been using it a couple of years to read-write to ext3 partitions from Win2k.

IndyTim

---

### Post by oobsniper2000 on 2008-06-06
Thanks for the help.  So far I'm thinking that I'll go with Ubuntu Server & install a simple desktop.  This machine will be nothing but a file server, so keeping it lean will be a good thing.

---

