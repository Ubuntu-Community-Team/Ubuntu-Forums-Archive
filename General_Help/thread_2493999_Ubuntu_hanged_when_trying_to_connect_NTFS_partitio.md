---
title: "Ubuntu hanged when trying to connect NTFS partition"
date: 2024-01-02
forum: General Help
---

### Post by readableauthor on 2024-01-02
Using Ubuntu 22.04.3, updated often.
When I clicked on an NTFS partition in the file manager my GUI froze and I had to reboot my laptop. Now I have some bad links in my /media:
```

user@hp-laptop:/media/user$ ls -la
total 20
drwxr-x---+ 5 root root 4096 Jan  2 14:32 .
drwxr-xr-x  3 root root 4096 Jan  1 14:43 ..
drwx------  2 root root 4096 Dec  7 16:47 Data
drwx------  2 root root 4096 Jan  2 14:28 Data1
drwxrwxrwx  1 user user 4096 Jan  1 21:57 Data2

```
I have a dual-boot Windows system and I think it happens after I booted into Windows once.
The problem went away after the reboot but the partition is now named differently in terminal.
Are there any logs or crash reports I should look into?

---

### Post by yancek on 2024-01-02
>  the partition is now named differently in terminal.

What is the difference?  What was it named before and what is it named now.  You need to be more specific about the problem.  dmesg and other log files are in the /var/log directory.

Also, you might explain what the 'it' is that happens after booting into windows.  Are you referring to the GUI freezing?

---

### Post by readableauthor on 2024-01-02
> **yancek said:**
> What is the difference?  What was it named before and what is it named now.  You need to be more specific about the problem.  dmesg and other log files are in the /var/log directory.

Also, you might explain what the 'it' is that happens after booting into windows.  Are you referring to the GUI freezing?
In UI it's "Data". "Data" and "Data1" from terminal are dead links. "Data2" is now working.
"it" is Ubuntu freezing. I had some work done, rebooted to Windows, rebooted to Ubuntu, and the problem appeared.

---

### Post by readableauthor on 2024-01-02
I've looked at logs and I have a lot of those around that time:
```

^@^@^@^@^@^@^@^@^@^@^@^@^@

```

---

### Post by tea for one on 2024-01-02
When you booted into Windows, did Fast Start Up become enabled?
This puts the ntfs file systems into hibernation for quick access when rebooting into Windows.
Unfortunately, it leaves the shared drives in an inconsistent state, preventing Ubuntu from mounting them properly.

---

### Post by readableauthor on 2024-01-02
Fast Startup was disabled and is still disabled

---

### Post by readableauthor on 2024-01-02
> **tea for one said:**
> 
Unfortunately, it leaves the shared drives in an inconsistent state, preventing Ubuntu from mounting them properly.
That usually results in error on Ubuntu side, not a freeze

---

### Post by MAFoElffen on 2024-01-03
'tea for one' was referring to Windows fastboot, which is trunns the power condition of poweroff to suspend/hibernate, which means (for Windows) that leaves the NTFS filesystem in an open state...

You said that (if you did go to the Control Panel's Power button behavior) setting's checkbox is not checked, so not enabled. <-- Do not assume that, please recheck it.

Why? Things happen. Are these ntfs drives internal or USB connected in enclosures?

---

### Post by readableauthor on 2024-01-03
> **MAFoElffen said:**
> 'tea for one' was referring to Windows fastboot, which is trunns the power condition of poweroff to suspend/hibernate, which means (for Windows) that leaves the NTFS filesystem in an open state...

You said that (if you did go to the Control Panel's Power button behavior) setting's checkbox is not checked, so not enabled. <-- Do not assume that, please recheck it.

Why? Things happen. Are these ntfs drives internal or USB connected in enclosures?

I know, I did go and check (Fast Startup is disabled). This drive is a single drive of my laptop. Windows and Ubuntu are installed on it.

---

### Post by MAFoElffen on 2024-01-03
And you are mounting an NTFS partiton on it with what command or fstab line?

---

### Post by readableauthor on 2024-01-03
Just using Nautilus and Ubuntu defaults

---

### Post by yancek on 2024-01-04
>  I had some work done, rebooted to Windows, rebooted to Ubuntu, and the problem appeared. 				 			  			   		 			 			 			 

The above quote is from your post #3.  It would be interesting to know what 'work done' means.  Your Data2 which you say 'works', has read/write/execute permissions for everyone meaning anyone can deliberately or accidentally delete everything on that directory or mount point.  There is never a valid reason to do that.

---

### Post by readableauthor on 2024-01-04
> **yancek said:**
> The above quote is from your post #3.  It would be interesting to know what 'work done' means.  Your Data2 which you say 'works', has read/write/execute permissions for everyone meaning anyone can deliberately or accidentally delete everything on that directory or mount point.  There is never a valid reason to do that.

work done = I just used my web browser and didn't use NTFS. The "everything" permissions are Nautilus defaults I guess

---

