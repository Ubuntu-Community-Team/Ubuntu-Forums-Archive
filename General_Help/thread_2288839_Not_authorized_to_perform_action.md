---
title: "Not authorized to perform action"
date: 2015-07-30
forum: General Help
---

### Post by Ayush_Agrawal on 2015-07-30
I have dual partitioned my laptop: windows 8.1 and ubuntu 14.04 .

Everything was working fine until recently when I "Refreshed" my windows to fasten it up.

The problem is that I am unable to mount any of my window's drives (or any other external drive - pen drive & hard disk -  in that regard). 

The error: Unable to access “161 GB Volume”. Not authorized to perform operation. 


I am facing serious trouble. Help is needed at the earliest.

---

### Post by SeijiSensei on 2015-07-30
You must be the root user to mount filesystems. Use "sudo mount ..." and enter your login password when prompted.

---

### Post by Mark Phelps on 2015-07-30
> The problem is that I am unable to mount any of my window's drives 

Windows 8.1 and newer implement FastStartup by default.  This effectively hibernates ALL the Windows volumes when Windows is not running -- preventing you from mounting them.

You have to go into Windows 8.1, and using the Power options, disable FastStartup before you can mount Windows volumes in Linux.

---

