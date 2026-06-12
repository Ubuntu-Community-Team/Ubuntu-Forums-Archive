---
title: "2 permissions questions."
date: 2008-02-11
forum: General Help
---

### Post by miesnerd on 2008-02-11
Honestly, there was only one question, but in trying to tackle the first question, i caused the second question. Luckily, i think those that are better versed than I am can easily solve both with just a few lines in the terminal.

First off, I have a new machine and im running 64 bit (7.10) ubuntu on it. I took a hard drive out of my old tower and threw it into an external usb case with intent to covert it into my storage drive (by deleting everything except the contents of the home folder).
It is currently mounted as /media/disk
the user that needs read/write access is miesnerd.
i know this is something like chown 755 or chmod 677 or something like that, but I dont know exactly what it should be and how to enter it into the command line with all the right variables.
I just want to be able to mount this drive as an external that I can save my important data on, so if I need to reinstall or install a second OS, its all on a totally seperate partition/disk.


Secondly, in my attempt to fix this, now when i log in, i get a message that reads "User's home/ .dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions, Users's $HOME directiory must be owned by user and not writable by any other users.

Thanks again people!
Miesnerd

---

### Post by The Avatar of Time on 2008-02-11
I do a sudo chown yourname:yourname /whatever for instance if i didnt own my home folder and wanted to i would: 

sudo chown william:william /home 

or 

sude chown yourname:yourname /media/disk 

to make you the owner of that external disc. Then if the read and write properties are wrong right click on you home folder and go to properties>permissions and change accordingly, I think a sudo chown -R yourname:yourname /whatever would do a recursive own ensuring that you own everything else in the folder/s as well. but it may be sudo chown yourname:yourname -R /whatever yeah I think that's the right way. Good luck.

---

### Post by MighMoS on 2008-02-11
chown will CHange the OWNership of the files (a "-r" after it will do it recursively, meaning all files and folders in that folder), and a chmod changes the permissions (mod stands for mode, but that doesn't really reflect today too well).

So chown -r [USERNAME] /media/disk/ should work to give your user access to everything. The quickest way to fix your other problem would be ```
chmod 644 ~/.dmrc&&chmod 700 ~
``` if I understand your problem correctly. 

The numbers represent permissions for the owner, then group, then everyone else.
4 = read, 2 = write, and 1 = execute, and you add them together. Note that directories must have read and execute set (other wise you can only see what's in directories, but not really access them).

---

