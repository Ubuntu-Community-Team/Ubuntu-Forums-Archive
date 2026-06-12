---
title: "VMware issue..."
date: 2007-12-15
forum: General Help
---

### Post by Moonfrost on 2007-12-15
Hi, my prolem is that I uninstalled VM ware but telling by the free space on my hard drive it seems the Virtual machine and virtual hard disk didn't delete themselves...anybody know where they could be? I looked everywhere including hidden folders and nothing! I really want to free up 10 GB of space please!!

---

### Post by fjgaude on 2007-12-15
Norally the vmx is in /var/lib/vmware/Virtual Machines/

---

### Post by HermanAB on 2007-12-15
I believe that this is a bug in Ext3.  It *may* fix itself after fsck and a reboot.  It may fix itself one day when the phase of the moon is just right. 

This is the main reason why I don't use Ext3 if I can help it.  I rather use JFS which doesn't waste disk space like that.

---

### Post by Moonfrost on 2007-12-15
> **fjgaude said:**
> Norally the vmx is in /var/lib/vmware/Virtual Machines/

It tells me that the directory doesn't exist...

---

### Post by Shazaam on 2007-12-15
Have you looked in /home? And /usr?
As an aside, I keep my vm's in a Desktop folder. Easy to get at and delete if I need to.

/home/username/Desktop/Goodies/vmware/Mandrake.vmx
/home/username/Desktop/Goodies/vmware/Massive Multi-Boot.vmx
/home/username/Desktop/Goodies/vmware/DSL.vmx
/home/username/Desktop/Goodies/vmware/Win98SE.vmx
/home/username/Desktop/Goodies/vmware/WinXP.vmx
(edited out my username)

---

### Post by fjgaude on 2007-12-15
Really, a normal install puts them in /var/lib/vmware... Say, how did you install them to begin with?

---

