---
title: "[SOLVED] Relocating Documents Folder"
date: 2008-03-25
forum: General Help
---

### Post by 3uph0riac on 2008-03-25
I currently have a dual boot setup between Ubuntu and Windows XP and am hoping to merge the documents into once place.

I have everything filed how I like it and all that is left is to redirect the Documents, Music, Video and Pictures shortcuts, etc to point to the new location.

First of all, how would I go about doing this, and when I log on, the drive is inaccessible. I need to go to open it through the computer menu and input my password since it belongs to root and I do not initially have priviliges.

So, how would I firstly automate the permission-giving, and secondly redirect everything?

---

### Post by milton1 on 2008-03-25
you should be able to automate the permission issue by changing the ownership of the mount-point for your documents. As for redirecting, you could make a sym-link from your home directory to the documents directory using ln.

---

### Post by kpkeerthi on 2008-03-25
> **3uph0riac said:**
> I currently have a dual boot setup between Ubuntu and Windows XP and **am hoping to merge the documents into once place.**

I have everything filed how I like it and all that is left is to redirect the Documents, Music, Video and Pictures shortcuts, etc to point to the new location.

[B]First of all, how would I go about doing this, and when I log on, the drive is inaccessible. I need to go to open it through the computer menu and input my password since it belongs to root and I do not initially have priviliges.
[/B]
So, how would I firstly automate the permission-giving, and secondly redirect everything?

Not very clear from your post. I assume you want to keep all the documents in the partition where XP is installed and use it from ubuntu.

**1. Locate the partition where XP is installed**
```
sudo fdisk -l
```
This should print something line below
```

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
**[COLOR="Red"]/dev/sdb1[/COLOR]**   *           1        4398    35326903+   7  **[COLOR="Red"]HPFS/NTFS[/COLOR]**

```

From now on I assume **/dev/sdb1** is your XP partition.

**2. Make /dev/sdb1 mount automatically at boot time**

1. Make folder where the XP partition will be mounted
```
sudo mkdir /media/Windows
```
2. Open fstab 
```
gksudo gedit /etc/fstab
```
3. Add this line to the end of the file
```
/dev/sdb1 /media/Windows  ntfs-3g defaults 0 0
```
4. Save & Exit. Reboot.

Your windows parition should be mounted automatically upon reboot. You will also find a desktop shortcut to it.

Open nautilus (home icon on your desktop), right-click and create shortcuts to the Video/Music folders under /media/Windows

---

### Post by andrewk8 on 2008-03-26
This is exactly what I want to do.  Does anyone else have any experience with this?

I have a clean Ubuntu 7.10 install on a NTFS partition through Wubi-7.10 Alpha (yes, it worked for me).  I'm assuming that my configuration behaves the same as an install on a real partition.  (If there are any Wubi issues, LET ME KNOW!)

What I would like to do is create symbolic links between my NTFS partition and my Linux "home" folder like these:
[LIST]
[*]/media/windows/Documents and Settings/(username)/My Documents
[*]/home/(username)/My Documents
[/LIST]
and
[LIST]
[*]/media/windows/Documents and Settings/(username)/My Documents/My Pictures
[*]/home/(username)/Photos (or /home/(username)/Pictures)
[/LIST]
and
[LIST]
[*]/media/windows/Music
[*]/home/(username)/Music
[/LIST]

The idea is to leave everything (documents, pictures, music, etc.) on NTFS, but have access to the same files in both Windows and Ubuntu.  Anyone see any issues with this?

---

### Post by 3uph0riac on 2008-03-27
Cheers kpkeerthi, I followed your instructions and everything is working exactly how I hoped it would. Sorry for the less than concise request.

andrewk8, I suggest you just do what kpkeerthi suggested and make links to the folders you want within the home folder...

> **kpkeerthi said:**
> 
Open nautilus (home icon on your desktop), right-click and create shortcuts to the Video/Music folders under /media/Windows

---

### Post by andrewk8 on 2008-04-01
Found an easier way to accomplish this.  Newbie-friendly.  Doesn't involve editing any system files.

Install "ntfs-config" using Synaptic.

Run the NTFS Configuration Tool (Applications, System Tools, NTFS Configuration Tool).  Check the boxes to enable write support for internal (and/or external) drives.

Open the File Browser.  Navigate to /media/C Drive/Documents and Settings/(username)/.  Select My Documents.  Choose Edit, Make Link.  Move the symbolic link to /home/(username).

---

