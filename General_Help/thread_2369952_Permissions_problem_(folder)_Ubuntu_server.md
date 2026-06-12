---
title: "Permissions problem (folder) Ubuntu server"
date: 2017-08-28
forum: General Help
---

### Post by mwoosley on 2017-08-28
Hello everyone, I hope everyone is doing great ;-)

Today, I was learning how to mount my USB drives from the command line, but I ran into a snag that I hope is easy to figure out.

Please allow me to summarize what happened... I plugged in my USB drive and then entered the command 'fdisk -l' from the command line.  I noted my device name.  I then created a directory in my /dev folder called usbdrive1 or /mnt/usbdrive1.  Next I mounted the drive with the 
'sudo mount /dev/sde1 /mnt/usbdrive1'  This worked fine as I verified it with 'mount | grep sde1, which returned the drives info.  It's the next step where I cannot figure out what I'm doing wrong... I tried to place a file in the usbdrive1 folder with the following command... 
'echo linux is great > testfile.txt

Immediately after hitting enter, I got the error '-bash: testfile.txt: Permission denied

I don't know why I'm not able to create this file as I'm the owner of the folder (root) and the permissions for the owner are rwx.  The group and others permissions are r-x and r-x.  I am not experienced enough to know if I need to change the group permissions or not.  If that is ultimately what the problem is, then does  that mean every time I create a folder I would need to change permissions on the group?  

Thanks in advance for any advice

---

### Post by TheFu on 2017-08-29
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
You need to learn that stuff if you plan to be a user on any Unix-like system.

Also, rather than describing the permissions, please just post the output from an **ls -l** for the files and directory where the files sit.

```
drwxrwxr-x  2 root   root   4096 Aug 29 19:59 ./
```

BTW, I hope you are NOT root.
We also need to know what file system is being used on the usb drive.  If it isn't a Linux file system, then owner, group and other permissions are set at mount time. It is impossible to change them after-the-fact.

Look up how to force a specific uid, gid during the mount if you use NTFS or FAT-anything.

---

### Post by mwoosley on 2017-08-30
Thanks for the heads up... I am doing my best to grasp the permissions concepts as I perform these tutorials and quite frankly, I have discovered the best source of information is straight from Ubuntu and not from other 3rd parties.  Don't get me wrong, there are very talented tech personnel out there who know their Linux, but there are also many more who strive to throw out their own versions of what they believe works best and it doesn't always pan out that way for everyone.  As of late, I have discovered that reading the Ubuntu documentation has been the most helpful with the ever so often help from the community.  

My issue is that I am still not grasping the concept on 'why' I'm not able to 'write' a file to a sub-directory called usbdrive2 located in the mount directory (/mnt).  The problem arose when I tried to create a file using the echo command ('echo linux is great > testfile.txt') and it provided a '-bash: testfile.txt Permission denied' error.  As a newbie trying to pick up on what might be wrong, my ls -l response is 'drwxr-xr-x 2 root root 4096 Dec 31 1969 usbdrive2.   I recognize that root is the user and group, but why aren't I given the opportunity to 'sudo in' to create this file?  The only way I was able to get in was to change ownership to me and ultimately it changed back to root, which also caught me off guard.

To test my own theory on my own home directory (where I am the owner), I was in fact able to perform the write procedure to my documents folder there.

I'm not sure what else I could provide to help someone Help me, but I sure need help understanding this.

Thanks.

---

### Post by TheFu on 2017-08-30
Non-Linux file systems do not support Unix-like permissions. It is that simple.  Unless you specifically formated the USB drive to a different file system, it came with one that doesn't support changing permissions. Didn't I say that above?  

At mount time, you _may_ set the default permissions for all the files/directories on the mounted storage.  Not all file systems are created equal.  It matters in many ways - this is one.

Your HOME is probably on an EXT4 file system.  Permissions, ownership work there.

I have no idea what you mean by "sudo in"  - that's a completely new term to me.  If you are using a GUI, I cannot help. I find GUIs support about 10% of what I need, so they aren't worth learning for most things.

Basically, at your stage, you need to start thinking and knowing that Unix is a multi-user OS from top to bottom.  Permissions matter.  They are the core of the Unix security model.  Permissions control access to pretty much everything.  When a program/process is launched, it runs with an effective userid and effective groupid.  Thest things control what access it has on the system ... using all the file permissions you'd learn at the already provided link.  Even hardware access it controlled by these permissions.  It really is very elegant.  That link is Ubuntu provided.

Please, please, please, whenever posting code or output, use "code tags."  Adv Reply (#).

BTW - Linux isn't Windows. ;)  There are many different concepts at the core.  I see you are understanding it, a little more.

---

### Post by HermanAB on 2017-08-30
A simple solution to your access problem is to create a subdirectory on the USB device with your user:group.  You will then have access to it, same as to your home directory.

---

### Post by TheFu on 2017-08-30
> **HermanAB said:**
> A simple solution to your access problem is to create a subdirectory on the USB device with your user:group.  You will then have access to it, same as to your home directory.

Which will only work if the storage has a Linux file system.

---

### Post by mwoosley on 2017-08-31
TheFu, thanks for providing feedback as it is very helpful.  I am using Ubuntu Server, strictly command-line.  

First, in order to be in more compliance, please let me know what you mean by using "code tags" and/or Adv Reply (#).  

And finally, I do understand that there are ext3/4 designed for Linux and NTFS file systems designed for Windows, but if I created an entire array of devices formatted in ext4 format on my Linux server, would I be able to place absolutely any type of file onto those devices?  Are there any restrictions to file type conflicts with files created on a Windows system and stored on a Linux file system?  I apologize if these questions seem overly simple, but I just want to ensure that I enjoy a smooth transition from Windows to Linux ;-)

Thanks again for your help TheFu ):P

---

### Post by TheFu on 2017-08-31
Bit are bits.  File systems don't care.  I've never heard of any incompatible files between different file systems.  
Each file system has limitations on total number of entries, sizes of files and which characters can be used in the file and directory names.  In general, ext4 supports larger everything when compared to NTFS and much larger when compared to FAT-whatever.  You may not have realized this, but microsoft has silently changed NTFS versions over the years.  They haven't done that with FAT32 or exFAT.

However, Windows can't read ext4, jfs, zfs, xfs, file systems natively.  You can provide access from Windows system to the files over the network, if you like. There are multiple methods for this.

My signature has a link about "code tags".  It makes viewing command output here much easier. We are uses to seeing it, know the format of the command output and prefer it.  Plus it prevents misinterpretation, since we get to see the raw output. That is always better than an interpretation of the output from someone struggling to understand or having an issue.

Which file system is being used? How can we help without that critical information?

The only time I use NTFS or FAT-whatever is when there isn't any other choice. It is just a bunch of hassle under Linux, a multi-user OS.

Linux supports 10-50 different file system types.  Sorta like different vehicle tires. Each type was designed for a specific purpose to be optimized.  Lacking any specific requirement, ext4 is a good choice for a general purpose, fast, reasonably safe, file system.  I wouldn't use ext3 anymore.  There are times where ext2 makes sense, usually just for /boot/ partitions.  There are times when xfs or zfs each make sense.  I wouldn't touch btrfs - others will disagree on that.

There is a wikipedia article about *file systems* that might be helpful. If you like, read it.

---

### Post by mwoosley on 2017-09-04
Thanks for the update and the tips on the different file system traits.

---

