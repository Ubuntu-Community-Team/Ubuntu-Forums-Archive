---
title: "gftp messing up permissions"
date: 2008-01-21
forum: General Help
---

### Post by Majorflam on 2008-01-21
I am running Ubuntu with a Windows XP dual boot.

I have a partitioned space on my hard drive, and it contains backups of my web directory. I can mount this drive in Ubuntu without any problems. However, when I upload any updated files to the web server using gftp, all the file permissions get messed up.

Last night, I uploaded about 5 new files (php and html), and then I couldn't access the site at all, I was receiving a permissions error (you don't have permission to accesss / on this server).

It basically made the entire site unaccessible. In the end I had to boot into windows and delete the entire website using coreftp, and then upload the backups again.

What a nightmare!

I'm trying to move away from Windows entirely, but I cannot afford to encounter major problems like that. Does anyone know how I can upload to a server using FTP without destroying the permissions?

Any help would be very much appreciated.

---

### Post by Majorflam on 2008-01-21
Anyone have any ideas on how to remedy this? An alternative program? Some settings needing tweaked?

I'm googling for info, but nothing is specific to my problem.

TIA.

---

### Post by erfahren on 2008-01-21
what filesystem is that other partition formatted to? I know that FAT32 can screw up file permissions that are set in Linux. 

I've never had any trouble with gftp like you describe (not saying I don't believe you) - anyway, you could try Filezilla - it's available in Synaptic.

maybe it's possible the configuration files are messed up for gftp - you could try renaming the ~/.gftp folder in your home (its a hidden directory - Ctrl+H to view) - gftp will then create a new one, you'll just have to put in all of your information again.

---

