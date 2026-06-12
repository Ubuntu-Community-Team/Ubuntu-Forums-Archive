---
title: "Accidentally installed Ubuntu 16.04 onto the wrong drive."
date: 2017-10-19
forum: General Help
---

### Post by rick-blacker on 2017-10-19
Hey all, I have three hard drives.
1) Windows 10 install
2) Windows spare drive used for file storage, some apps get installed onto this drive, etc... Just a secondary drive.
3) Ubuntu 16.04

Yesterday I wanted to wipe my Ubuntu hard drive and put a fresh Ubuntu install onto it.  I had been doing a some Linux development a year ago.  I needed to do some new development and just wanted a fresh clean install and to overrite the existing install.  Well, that's not what happen. Somehow I managed to install Ubuntu onto my secondary Windows spare drive I use for files and what not.

For sanity sake, I booted up into Windows. Windows no longer sees the hard drive in Explorer.  However, I can see it in the Disk Management app that comes with Windows. When I look at it, this is what I see. 
[ATTACH=CONFIG]277175[/ATTACH]

Is there ANY chance that either of those partitions MIGHT still have my old Windows files/apps and what not?  If so, how can I recover them?  Or is this just a complete loss?

---

### Post by oldfred on 2017-10-19
I am not seeing 3 "drives". 
In Linux a drive is a physical hard drive or flash drive. Windows is the only one that confuses drive with partitions.
The second partition on the first drive in Ubuntu is sda2, but in Windows that could be a second drive.

I only see two NTFS partitions, your boot & main install.

Post this:
sudo parted -l

How did you erase/reformat Linux partition?
Best to use Windows tools for Linux and Windows tools only for NTFS partitions. Windows does not correctly see Linux partitions, so you are not sure what  you are working with.

---

### Post by untrustytahr on 2017-10-19
> **oldfred said:**
> ...
Best to use _Windows tools for Linux_ and Windows tools only for NTFS partitions..

Looks like Satya Nadella got a hold of oldfred's credentials ;)

---

### Post by rick-blacker on 2017-10-19
Hi Oldfred.
Yes, you're correct, that image only shows two physical hard drives.  At the time I took a screen pic, I did NOT have the original ubuntu physical hard drive plugged in.  What that image shows is my normal Windows hard drive and the (what was my windows extra hard drive) hard drive that I accidently installed Ubuntu on.


I'm currently running a Windows file recovery app to see if it can recover my files. It seems to have a found a ton of them if not all. But, it's still scanning.  I know that just because it can find reference to them does not mean it will actually restore them.  

I will look into the apps you mentioned as well.

---

