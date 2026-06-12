---
title: "Files On Windows"
date: 2012-10-15
forum: General Help
---

### Post by PadiSka on 2012-10-15
Hi,

I have a dual boot system with Windows and Ubuntu and I was wondering: is there any advantage/disadvantage to having files that are regularly accessed by Ubuntu mounted to my Windows OS/partition.  For example having a music file that is saved on my windows partition but is constantly opened and played on Banshee music player in Ubuntu.

Question in summary is if there are any reasons why I shouldnt do this? Or why it wouldnt be optimal etc.

Thanks Guys.

---

### Post by DarkAmbient on 2012-10-15
Two reasons I can think of is that you need to mount the windows-partition yourself before accessing any files on it via some application in Ubuntu. If you manage to setup to automount it on boot then that's not a problem though. 

The other thing is that the Windows-partition (most likely) has a NTFS-filesystem. I don't think you'll get any problem from playing media-files, but if you decide to, for example, share some media-folder on the windows-partition over network in Ubuntu, then it will most likely be problems. I've also had issues with starting scripts or some install-files from the NTFS-disk.

Can't really go into details about why, this is just issues I've encountered myself.

---

### Post by Cavsfan on 2012-10-15
+1 ^^
I suggest you read from windows files but, do not update anything on windows from Ubuntu.
Windows has a user journal that keeps track of every change that is made and if you make a change outside of windows that will not be tracked and could cause you problems.
I would suggest you copy the files from windows to Ubuntu and use them there but, not vice versa.

---

### Post by robtygart on 2012-10-15
I agree with you! I would want to access the Windows drive to play my music, why use up all the extra space (Unless you got it)....

You will need to mount or Auto-mount the drive. (As said above don't write to it, only read files.)

---

