---
title: "New lamp server questions"
date: 2006-12-19
forum: General Help
---

### Post by wldmn13 on 2006-12-19
](*,) 

I am a linux idiot newbie.

After trying and failing to setup the GUI ubuntu, then setting up a server and trying to install apache, etc. then realizing what a LAMP server was and installing that instead:

My current method of getting files onto the LAMP server is downloading it from my working windows machine and burning it on a cd, which only works after a day and half of trying unsuccesfully to mount the cdrom. This is laborious and wasteful of my cdroms, so I'm looking for another way.

I have a USB jump drive, but after the abortion that was me trying to mount the cdrom, I don't think I'm ready to try and decipher google results for how to use the jump drive.

My other thought was to use the internet on the lamp server itself, but I can't find any information on that. Is there a browser on the lamp server, or am I going to have to burn another cd with a tar.gz file on it? I tried tar'ing firefox, but I don't know what to do now that the files are on the hard drive.

This thread [http://www.ubuntuforums.org/showthread.php?t=212458&highlight=lamp+browser](http://www.ubuntuforums.org/showthread.php?t=212458&highlight=lamp+browser) mirrors my frustrations pretty well, but I opened every single one of the pages suggested to help ease the learning process and as soon as I'm done typing this I will begin perusing each of those links.

Thanks in advance for any help.

---

### Post by mayonaise15 on 2007-01-05
Hey, I hope it's not too late for you to see this reply wldmn13.

What I would recommend is to set up an SSH (aka Secure SHell) access on your LAMP server.  SSH allows you to remotely log into your LAMP server from another computer.  There is a great SSH client for Windows called PuTTY. [It can be found here.]("http://www.chiark.greenend.org.uk/~sgtatham/putty/")  The really cool think about SSH is that you can run a LAMP server without having to hook up a monitor/keyboard/mouse to it.  All it needs is an ethernet cable and a power cable.

To transfer files between computers I would recommend SCP (aka Secure CoPy).  A great GUI program for Windows called WinSCP, [which can be found here.]("http://winscp.net/eng/download.php")  I tend to think of WinSCP like a regular FTP client, except much more secure.

[Here is a link to the Ubuntu Wiki on SSH.]("https://help.ubuntu.com/community/SSHHowto")  It will be able to help you with installing and getting things set up.  Best of luck to you!

---

