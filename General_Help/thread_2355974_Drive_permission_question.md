---
title: "Drive permission question"
date: 2017-03-18
forum: General Help
---

### Post by Music_Guy on 2017-03-18
I don't have a problem; however I want to see if I understand at least this one point about drives and permissions. I'm planning to restage my Ubuntu machine. It currently has 3 HDDs, one for the OS, one for a backup, and one for storing my recorded music. I'll do my best to set Ubuntu up as it is now in terms of computer names, owner, etc. However, if I do make a mistake and find that I cannot access the backup and/or the music drive, my understanding is that I should create a mount point under /media for the drive UUIDs, then change ownership of the drive(s) using the chown command. Is this correct?

Also, since I plan to set the computer up with dual boot with Fedora, can I set up a group with both the Ubuntu and Fedora users so that both can read/write/delete access the drives? 

Thanks.

---

### Post by deadflowr on 2017-03-18
> my understanding is that I should create a mount point under /media for the drive UUIDs, then change ownership of the drive(s) using the chown command. Is this correct?
No
No need to change any permissions for the drive itself.
Just check that any folders you want to access on the drive are accessible to you.

Ubuntu will allow you to mount devices/drives/whatnots in the Files program.
(look at the left sidebar for all available devices currently connected to your machine)
Click on any of the devices listed and the main window area will open to that location.
In the main window area it will show any folders that are on that device.
It is these folders that you will need to make sure you have access to.
(You can right click on any file or folder and go to properties to see who can access the files/folders)

When you use the Files program to mount devices the location in the file system is the /media folder, typically under a user-specific folder for the user like /media/bob/the-device-name

---

