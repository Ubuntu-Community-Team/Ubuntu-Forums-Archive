---
title: "Folder disappeared"
date: 2019-11-07
forum: General Help
---

### Post by heroquestelf on 2019-11-07
I am running a Toshiba Satellite P305 Laptop and I'm running Ubuntu MATE 14.04

I have a bit of a puzzle. I had a folder shortcut on my desktop that I deleted. I **specifically** told it that I **ONLY** wanted to delete the shortcut, and I did **NOT **want to delete the files in the folder. However, when I went looking for the folder i found it had disappeared as well. My trash is empty, so if I did delete it I don't know where it went. Can anyone help me retrieve these files?

---

### Post by TheFu on 2019-11-07
First, 14.04 free support for Mate ended a few years ago.  Please move to a supported release.  18.04 is the current LTS.  Not running supported releases opens you up to being hacked, especially if the system is on networks that you don't control - cafe, college, library, restaurant, hotels, .... 

I don't know what a "folder shortcut" is, but removing a *symbolic link* only removes the link, not the data where it points.

Perhaps you just don't remember the correct location where the symbolic link pointed?  If that is the situation, you can search for files using any number of tools.  **find**, **locate**, **recoll**, ....    If you google "linux find examples", that is probably the most helpful solution.  

If you want those files back, just use your most recent backup and restore them as needed.

If you don't have a backup, doing anything on the same partition, even running the OS, can be overwriting the data where those files were located.  Best to get another drive that is at least as large as the partition where those files were, then use a byte-for-byte copy tool like ddrescue to clone everything over to the other disk, so you can run data recovery efforts. If this is your best action, you'll want to stop booting from the OS and boot from a Try-Ubuntu install flash drive so the data left on the drive doesn't get overwritten.

Running any of those find, locate, etc. commands or installing anything or even just booting the system where log files are created can be overwriting the data you want to recover, if that data is on the same partition as the OS.  You've been warned.

Ubuntu Data Recovery Guide: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
If you are successful in recovering some of the data, I think you'll decide that having backups is much, much, easier.

---

### Post by HermanAB on 2019-11-08
Use the find utility to look for a file from your missing folder - then you will see the path to it:
$ find ~ -name *whatever*

---

