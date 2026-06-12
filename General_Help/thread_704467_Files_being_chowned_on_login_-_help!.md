---
title: "Files being chowned on login - help!"
date: 2008-02-22
forum: General Help
---

### Post by samkline on 2008-02-22
Hi,

I just followed [[this guide](https://help.ubuntu.com/community/FolderEncryption)] to encrypt my home directory (which I did on my old Ubuntu box and it worked fine) and now I'm having problems.

I started by coping my home directory to another directory, then created the encrypted FS, then mounted the encrypted FS and copied all the files in my home directory back.

It works, and my home directory is encrypted, but now I'm getting problems with file permissions. When I logged in I got a message saying my .dmrc file was being ignored and I should fix its permissions - so I chmodded it to 0644 and chowned it to my username. Then I logged in, and didn't get the error message. But after logging in, the .dmrc and .xsession-errors files are both owned by root again. The permissions of .dmrc is rw for owner and nothing else. Permissions of .xsession-errors is rw for owner and r for group/other.

I also have other problems: I can't save files in Firefox (no permission), and even just right clicking in Nautilus and choosing "Create Document -> Empty File" creates a blank, read-only file owned by root!

Both the encrypted folder (unmounted) and the folder where it is mounted are owned by me. I think I followed the guide exactly, and it worked last time I did it (on Feisty). What can I do to fix this (other than get rid of encryption)?

Edit: There is nothing relevant in .xsession-errors.

Thanks!

---

### Post by cmnorton on 2008-02-22
I do not have a fix for you, but have seen this error, and here is further info:

[http://ubuntuforums.org/showthread.php?t=77143](http://ubuntuforums.org/showthread.php?t=77143)

[http://ubuntuforums.org/showpost.php?p=3302702&postcount=2](http://ubuntuforums.org/showpost.php?p=3302702&postcount=2)


Our application is a user, and anyone who uses the application belongs to that user's group; and needs write privileges in the application's directories, because the database and report directories belong to the application. Therefore, the application's home directory's permissions are 770. 

Sometime after RHEL3, gnome would report the error you got . None of the users (clients) log in using X, so I've learned to live with gnome squawking about this.

I believe this is security-related, based on your home directories permissions. I never looked into it further than that.

---

### Post by samkline on 2008-02-22
I did try changing the owner and permissions of my files, but the ownership/permissions of those files were changed every time I logged in.

I did find out how to fix this:in [FONT="Courier New"]/etc/security/pam_encfs.conf[/FONT], I had to add "--public" as an encfs option. Otherwise every file I tried to create would be owned by root.

---

