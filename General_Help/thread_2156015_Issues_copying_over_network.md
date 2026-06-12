---
title: "Issues copying over network"
date: 2013-06-20
forum: General Help
---

### Post by andrewgerm on 2013-06-20
Good day all

I have had a few issues copying files / folders from network locations to my laptop.
 
The laptop is running 13.04, with all recent updates, and connected via cable. When copying files, only a few seems to copy correctly, on most occasions. The issue doesn't seem size dependant, as some files are under 1MB.

Most of the time, I am trying to copy from a Vista 64 machine, although this has occurred a few times when copying from a 12.04LTS system.

I had this problem when the laptop was running 12.10, with Unity 2D. A complete re-install (not upgrade) to 13.04 with LXDE has the same issues.

Any pointers on this? I have looked at several search results online, but none seem to resolve the issue.
Thank you in advance :)

---

### Post by TheFu on 2013-06-20
Perhaps if you named the programs used and explained how the files are shared, someone could help?

I use ssh/scp/sftp all the time and samba sometimes after mounting the Windows folders to my Linux machines.  Usually those copies are from a CLI interface.  I can't help if you are using a GUI, sorry.

---

### Post by andrewgerm on 2013-08-01
Sorry for the delayed reply. I was away from the PC, and then, of course, the forums were down.

I have been using sftp, and have moved a lot of my network admin work to ssh. Most of the time this works great. Still file copy issues though. In the GUI, I have changed to Thunar, as I read in several places that Fileman had an issue with copying a large amount of files or large files, via the network.

Copy speeds are still extremely slow, copying between 13.04 desktop to 13.04 sever.
I am also still having the problem of copying stalling when copying from a Windows share, and opening files over the network (e.g. opening a .doc in Writer) doesn't work at all. What I have to do is copy the file to the local machine (if that works) and then open the file from there.

Any further suggestions greatly appreciated :)

---

### Post by TheFu on 2013-08-01
> **andrewgerm said:**
> Sorry for the delayed reply. I was away from the PC, and then, of course, the forums were down.

I have been using sftp, and have moved a lot of my network admin work to ssh. Most of the time this works great. Still file copy issues though. In the GUI, I have changed to Thunar, as I read in several places that Fileman had an issue with copying a large amount of files or large files, via the network.

Copy speeds are still extremely slow, copying between 13.04 desktop to 13.04 sever.
I am also still having the problem of copying stalling when copying from a Windows share, and opening files over the network (e.g. opening a .doc in Writer) doesn't work at all. What I have to do is copy the file to the local machine (if that works) and then open the file from there.

Any further suggestions greatly appreciated :)

If this were happening on my machines, first I'd gather some **facts and data**.  Facts like:
* network connection data - cards, router, switches, and cables.
* disk performance data - how fast are the disks, how are they connected, 
* the type of mount used to access remote files. Without this knowledge, we are pissing in the wind. 
* test transfers - for specific sized files, how long does a transfer take - going each way?  Small files, large files, huge files?  For each test, what is the Mbps transfered?  I'd be very careful to know if I were using MBps or Mbps units.

Also, I'd try these things capturing real-clock times and computer time using the **time** program. I would avoid as many layers as possible until I figured out what the root cause for "slow" is.  GUI tools are usually the issue and next to impossible to troubleshoot inside.

That would be my performance testing.  Then there is the issue of opening remote files.  
* How are they mounted?  nfs, cifs, gvfs, sshfs, some other way?
* Does the selected method support file locking as required by the GUI tool used?
* Is any virtualization used?  VirtualBox mounts?

I've had an issue where Geany (a GUI file editor) wouldn't save files on a CIFS mounted area due to unsupported file locking. This stuff that seems simple, is really complex.  I'd remind myself about that constantly.

Anyway, that is how I'd attack this issue.

---

### Post by Wayne_Shumaker on 2013-08-01
How do you mount the windows share in Linux?

---

