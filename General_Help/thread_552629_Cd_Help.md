---
title: "Cd Help"
date: 2007-09-16
forum: General Help
---

### Post by Unions on 2007-09-16
OK I want to copy a text file off a cd onto my hd IN TERMINAL
It is a "server.cfg" for a Counter strike source dedicated server.

---

### Post by celticbhoy on 2007-09-16
You say what you want to do, but what is the problem?

---

### Post by Unions on 2007-09-16
what is the terminal location i know it should be
# cd LOCATION
# cp server.cfg home/myname/srcds_l/cstrike/cfg

what is the location?? if its ona cd, in the drive?

---

### Post by sumguy231 on 2007-09-16
Try /media/cdrom, /media/cdrom0, or /media/cdrom1. But is there any particular reason you need to use the terminal instead of just using Nautilus?

---

### Post by bigboy_pdb on 2007-09-16
If you want to find out what directories are affiliated with certain devices in the command line, use the command "mount". The directories are listed followed by their corresponding devices followed by the file type followed by information about how the file system has been mounted. CD-ROMs are of type "iso9660". If you don't want to look through all of the lines to find what directory the CD-ROM is mounted to, you can use the command "mount | grep 'iso9660' ". This command sends the output of "mount" to a program called "grep" which will only print the lines containing "iso9660".

What was mentioned beforehand is only necessary if you need to work from a command line. What sumguy231 said to do (about using Nautilus) would be easier if all you need to do is copy a file. You can open it by going to "Places" -> "CD-ROM" in your upper panel. Also, when you insert a CD-ROM in the CD-ROM drive Nautilus should start up and display the contents of the CD. If you are uncertain about how to copy something using Nautilus then you can ask us, but it is similar enough to Windows Explorer (My Computer) that you should be able to figure out how to do it (assuming you've used that program in Windows).

---

### Post by Unions on 2007-09-17
probably shoulda mentioned im on ubuntu SERVER edition, thats why i wanted terminal.

---

