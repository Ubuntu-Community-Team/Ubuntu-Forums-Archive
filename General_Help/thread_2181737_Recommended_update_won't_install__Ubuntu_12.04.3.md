---
title: "Recommended update won't install  Ubuntu 12.04.3"
date: 2013-10-18
forum: General Help
---

### Post by John_Carver on 2013-10-18
"/proc file system utilities" will not install as a recommended update.
I am not enough of an expert to figure out the problem even by looking at the description and reference.
Is it possible a future update will correct this?

---

### Post by vandorjw on 2013-10-18
I am not quite sure what you asked, but I think the answer to your question is, "not likely".

Could you describe in as much detail as possible how you were trying to install "/proc file system utilities" ?

I am not trying to be mean, but your original question didn't make sense, and I'll tell you why.

The proc file system is a pseudo-file system which is used as an interface to kernel data structures.  It is commonly mounted at /proc.  Most of  it  is  read-only,  but  some  files  allow  kernel variables to be changed.

So knowing this, its not possible for you to install an update to /proc, since you cannot write to /proc.

file system utilities - There are thousands of file system utilities. It depends on what FS you are running on. I think the default is ext4 on Ubuntu.

Microsoft uses NTFS, there is also FAT32, btrfs, etc.

To update your system, please run

```

sudo apt-get update

```

followed by

```

sudo apt-get upgrade

```

---

### Post by John_Carver on 2013-10-19
Have done an update and upgrade is already Ubuntu 12.04.03
Only update is the file I mentioned in the /proc file system utilities
The file name is:  procps (size 226kB)
I am using the default "update manager" to get updates and install them.  This won't install!
File system ext4

---

### Post by grahammechanical on 2013-10-19
Do you get an error message? If so, what is it? Sometimes upgraded packages are put into the update channel but are not installed because they depend on newer libraries that are not yet available to be put in the update channel. Sometimes packages are downloaded but not installed and then a few days later the other libraries (dependencies) appear in the update channel and then it all gets installed.

The important question is this, Are you still able to use the OS?. 

Regards.

---

### Post by John_Carver on 2013-10-19
OS works great.  I have read where this is a root command line (s) that control kill, etc
Here are the not installed comments.

installArchives() failed: Setting up procps (1:3.2.8-11ubuntu6.1) ...
start: Job failed to start
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 procps
Error in function: 
Setting up procps (1:3.2.8-11ubuntu6.1) ...
start: Job failed to start
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1

I am hoping your follow up comments come true.  Something later will come along.
In the meantime, I am still breathing and full of life

---

### Post by jalirious2 on 2013-10-22
This is solved [http://ubuntuforums.org/showthread.php?t=2181086&highlight=procps](http://ubuntuforums.org/showthread.php?t=2181086&highlight=procps)

---

