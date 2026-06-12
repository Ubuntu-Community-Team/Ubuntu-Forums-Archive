---
title: "How to use Ubuntu to Backup My NTFS-Windows systems?"
date: 2008-03-08
forum: General Help
---

### Post by MountainX on 2008-03-08
I'm thinking about using my Ubuntu machine to backup the Windows computers on my LAN. I'll be backing up to a TeraStation for now. My LAN is GigE. 

I suppose I could just use some Windows backup software on the Windows machine, but I want to move away from Windows and I don't want my backups to be in a proprietary format.

I thought it would be ideal if I can backup over the network. I don't really care about backing up the Windows OS files -- just the data.

What are my best options? Thanks.

---

### Post by Rocket2DMn on 2008-03-08
If you want to use a windows backup program, I suggest Cobian Backup - there aren't any proprietary formats, you can backup just the data, no compression if you want - and it's free.

For linux, I prefer a program called Simple Backup (sbackup).  You could use it to backup your windows stuff on the remote machine if you have the correct folder(s) shared and mounted on your linux machine with samba.  sbackup compresses its archives, which can be annoying if you're backing up a lot of videos, music, and photos since they take up a lot of space and are already compressed.  However, it is a nice, easy to use program.  If you find something better, let me know!

Both programs are also capable of doing incremental backups.

---

### Post by HermanAB on 2008-03-08
I install Cygwin with OpenSSH, then use rsync over ssh from Linux to backup the Windows machines.  This is the most reliable method I have found.

---

### Post by MountainX on 2008-03-08
> **HermanAB said:**
> I install Cygwin with OpenSSH, then use rsync over ssh from Linux to backup the Windows machines.  This is the most reliable method I have found.

Is Cygwin necessary only for SSH? The backups will all be conducted on my LAN, so SSH may not be necessary. I don't really want to install Cygwin on my Windows boxes. Can I use rsync without SSH?

---

### Post by MountainX on 2008-03-08
> **Rocket2DMn said:**
> If you want to use a windows backup program, I suggest Cobian Backup...

...If you find something better, let me know

For Windows, SyncBackSE is another good option. I can't say if it is better. 

It isn't free, but it is well-supported and really inexpensive. I paid $30 for a license that lets me run it on 5 computers. 

I've been using it to backup a Windows web server to a Linux FTP server and it works well. I hadn't thought about using it for my backups on my home network until you mentioned Cobian Backup...

But my real goal is to stop using Windows eventually, so the rsync and sbackup options are something I'll look into.

---

