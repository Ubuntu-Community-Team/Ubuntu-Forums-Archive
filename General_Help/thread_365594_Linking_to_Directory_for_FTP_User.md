---
title: "Linking to Directory for FTP User"
date: 2007-02-19
forum: General Help
---

### Post by Ohmz on 2007-02-19
I have my computer set up as an FTP server for sharing files between me and my roommates. I have a large collection of files I want accessible at all times, but I want it in my home folder (as admin). When my roommate connects using Windows (FileZilla) he only has access to his home directory (obviously). Can I make a link to the directory in my home folder I want him to be able to access?

---

### Post by gitrdone3 on 2007-03-02
hey, i was looking to do something like this before and what i finally found was to create a folder in your ftp users home directory, backup /etc/fstab, then add the following line:

[INDENT]/home/you/folder_to_share /home/ftp/new_folder vfat bind 0 0[/INDENT]

changing the first part to your file directory and the second to your roomates directory. add more with more shares if you'd like. then save then remount everything using 

[INDENT]sudo umount -a && sudo mount -a[/INDENT]

or reboot. hope this helps. i'm new to linux myself, so maybe theres a better way

---

