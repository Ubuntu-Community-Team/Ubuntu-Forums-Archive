---
title: "Problem with installing and removing packages in ubuntu"
date: 2017-02-16
forum: General Help
---

### Post by bilalhabshi on 2017-02-16
I am running ubuntu for the first time in my life. I am able to update the packages easily. But I can't remove or install packages/software(anything using *sudo apt-get install or remove*). Here is the output on entering an install/remove command:

```
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following additional packages will be installed:
      blt idle-python3.5 python3-tk tk8.6-blt2.5
    Suggested packages:
      blt-demo tix python3-tk-dbg
    The following NEW packages will be installed:
      blt idle-python3.5 idle3 python3-tk tk8.6-blt2.5
    0 upgraded, 5 newly installed, 0 to remove and 345 not upgraded.
    Need to get 647 kB of archives.
    After this operation, 2,345 kB of additional disk space will be used.
    Do you want to continue? [Y/n] y
    Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 tk8.6-blt2.5 amd64 2.5.3+dfsg-3 [574 kB]
    Get:2 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 blt amd64 2.5.3+dfsg-3 [4,852 B]
    Get:3 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 python3-tk amd64 3.5.1-1 [25.1 kB]
    Get:4 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 idle-python3.5 all 3.5.2-2ubuntu0~16.04.1 [40.5 kB]
    Get:5 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 idle3 all 3.5.1-3 [2,800 B]
    Fetched 647 kB in 5s (121 kB/s)  
    Selecting previously unselected package tk8.6-blt2.5.
    dpkg: unrecoverable fatal error, aborting:
     reading files list for package 'anacron': Input/output error
    E: Sub-process /usr/bin/dpkg returned an error code (2)

```
And here are the solutions I have already tried and there is no success.

[https://ubuntuforums.org/showthread.php?t=1232143&p=10010092#post10010092](https://ubuntuforums.org/showthread.php?t=1232143&p=10010092#post10010092)

This thread is telling about editing 'status' section, where the 'anacron'  is mentioned, but there is only 1 line that mentions this package.

Here is that line:

```
    Recommends: apport-gtk (>= 2.8-0ubuntu3), python3-aptdaemon.gtk3widgets | synaptic (>= 0.75.12), software-properties-gtk, anacron, python3-aptdaemon
```

After that another package is started. 

Also, I have tried this thread but no success:
[http://askubuntu.com/questions/591855/how-can-i-fix-e-sub-process-usr-bin-dpkg-returned-an-error-code-2](http://askubuntu.com/questions/591855/how-can-i-fix-e-sub-process-usr-bin-dpkg-returned-an-error-code-2)

Hope, I will be able to find some help here. 

Thanks,

---

### Post by ian-weisser on 2017-02-16
"No success" is very vague. What *exactly* did you try, and what was the complete result? Please be detailed.

What is your skill level? Do you understand what the commands in the AskUbuntu answers?

The error message tells you which file is corrupted. Did you see that line of the error message?

---

### Post by Bucky Ball on 2017-02-16
Welcome. And also the release you are using, please (Ubuntu 14.04 LTS, Xubuntu 16.04 LTS? or something else ...).

For what it's worth, try this:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

Getting the same errors after the autoremove command?

---

### Post by howefield on 2017-02-16
Moved to the "*General Help*" forum.

---

### Post by Impavidus on 2017-02-16
> **bilalhabshi said:**
> I am running ubuntu for the first time in my life. **I am able to update  the packages easily.** But I can't remove or install  packages/software(anything using *sudo apt-get install or remove*). Here  is the output on entering an install/remove command:```
    0 upgraded, 5 newly installed, 0 to remove and **345 not upgraded**.
```That's a contradiction: 345 packages have not been upgraded. **sudo apt-get update** is just to refresh the lists of available packages, **sudo apt-get upgrade** is for the actual upgrades. I suggest you run Bucky Ball's commands.

```
    Get:1 http://us.archive.ubuntu.com/ubuntu **xenial**/main amd64 tk8.6-blt2.5 amd64 2.5.3+dfsg-3 [574 kB]
```That must be 16.04.

```
    dpkg: unrecoverable fatal error, aborting:
     reading files list for package 'anacron': **Input/output error**

```I/O errors are nasty. They indicate the problem is not a confused package manager, but a problem at a deeper level. Possibly file system damage or hard drive failure. I assume you've got backups, right? In that case, nothing can go wrong.

---

