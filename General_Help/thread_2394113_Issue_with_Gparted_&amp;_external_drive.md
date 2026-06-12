---
title: "Issue with Gparted &amp; external drive"
date: 2018-06-12
forum: General Help
---

### Post by heroquestelf on 2018-06-12
Before I start, I am running Ubuntu MATE 18.04 LTS on a Dell Inspiron with a 3.2 GHz processor
 
 
 I am having a bizarre problem with an external hard drive that is driving Gparted CRAZY.
 
 
 The hard drive is a Maxtor One-Touch II 200 GB hard drive. It’s formatted with a NTFS partition type, and the computer identifies it as “/dev/sdc1”.
 
 
 What’s really strange about it, is that once Gparted gets done freaking out, it seems to read the drive fine. When I launch the “Disks” program, it reads it fine. Disks has no problem reading it or identifying it. When I launch Nautilus it works fine. I have no problem reading files from the drive, or with saving or deleting files.  
 
 
 The issue I am having has to do with what happens when you enter in a “sudo Gparted” command. You get the following set of errors.  
 
 ```

======================
 libparted : 3.2
 ======================
 Error fsyncing/closing /dev/sdc: Remote I/O error
 Error fsyncing/closing /dev/sdc: Remote I/O error
 Remote I/O error during write on /dev/sdc
 Error fsyncing/closing /dev/sdc: Remote I/O error
 Error fsyncing/closing /dev/sdc: Remote I/O error
 Error fsyncing/closing /dev/sdc: Remote I/O error
 Error fsyncing/closing /dev/sdc: Remote I/O error
```
 
 
 Now, like I said, once it gets done spewing these errors at me, it seems to work fine.  
 
 
 Can anyone give me any idea what’s going on here?

---

### Post by TheFu on 2018-06-12
External? How connected?   eSATA or something bad?  eSATA provides the full SATA command set, while the other connection types do not.  Also the disk controller might not be well supported.

---

### Post by ajgreeny on 2018-06-12
You should never use **sudo Gparted** as the command to open the GUI application gparted; either start it from your menu as normal or use command **gparted-pkexec** if you have to use the command line. Note also that it is gparted, not Gparted; Linux is case sensitive, unlike other OSs.

You can cause problems of file ownership in your home leading to inability of logging in as that user if you use sudo with some GUI applications so **never use sudo with a GUI application; it is for command-line apps only.**

I regret that with the info you have given I can not give you any possible solutions, but I suggest that you open gparted properly and see if that helps in any way.

---

### Post by heroquestelf on 2018-06-12
No, it's connected via USB.

---

### Post by TheFu on 2018-06-12
> **heroquestelf said:**
> No, it's connected via USB.

USB storage .... meh. Try a different cable and a different port on the computer.  If you are connected via USB3 port, try a USB2 port too.  If there is a USB hub involved, that can confuse storage. Remove it.   And there is some "fancy" USB storage from well-known storage vendors that includes firmware that just doesn't work with Linux. That doesn't  happen much anymore, but 5 yrs ago, it was a thing.

Moving on.  Does parted work?  What about fdisk?

To expand on  ajgreeny's comment, you can use **sudo -H gparted**.  The main issue with sudo is that it doesn't  change  the HOME directory to the userid you've escalated into. The -H option forces that. It would be a good idea to remove all root-owned files from your HOME.  They can cause permissions failures and some programs will crash.
And just to be pedantic, almost every OS is case sensitive except 1 that happens to be popular.

BTW, check the system log files. Any more error messages there about the disk?

---

