---
title: "fstab chmod help needed"
date: 2006-11-09
forum: General Help
---

### Post by skathrein on 2006-11-09
Here's my problem.  I have a second hard drive that I am trying to mount.  Mounting isn't the problem but I am having problems with permissions for new files.  The filesystem is **_ext3_**.  Here's what I have done so far:

I have mounted the drive using fstab and that seems to work fine.  My mount point is /media/Storage.  I have also used the following command to change permissions on all files and directories in the drive to allow read write execute permissions:

sudo chmod -R 777 /media/Storage

That command will properly change the permissions for all existing files, but any new files I add such as new documents are created as read/write for owner, but read only for group and others.  As for fstab, I've played around with the options such as defaults and users, but no luck.  

I guess what I'm looking for is maybe an option like umask=000/fmask=000/dmask=000.  However, I know I can't use these (and it won't let me as I've tried) because the filesystem is ext3 and not fat or ntfs.  Does anyone have any suggestions as to what fstab options or a different chmod command or anything else that would allow all future added files to be read write for everyone without having to run chmod everytime I add a new file?

---

### Post by krismatth3 on 2006-11-09
Edit: these instructions were incorrect, see below.

---

### Post by taurus on 2006-11-09
If you want to set permissions for rwx for everybody, then you can set that in your ~/.bashrc.  You need to add this line in there...

To edit it...
```
gedit ~/.bashrc
```

```
umask=000
```
Then, either log out and back in again or "source" it again so the new change will be in effect...

```
source ~/.bashrc
```

---

### Post by krismatth3 on 2006-11-09
Not, do NOT set umask to 000. That will make ALL FILES YOU EVER CREATE fully accessible by everyone.

---

### Post by taurus on 2006-11-09
> **krism said:**
> Not, do NOT set umask to 000. That will make ALL FILES YOU EVER CREATE fully accessible by everyone.
Isn't that what he/she wants, others to be able to read and write to those files?  And if you don't want people to mess around in your $HOME, then just set the permissions for your $HOME as 755!!!

---

### Post by krismatth3 on 2006-11-09
I believe he wants that only for /media/Storage. It's not just a matter of files in ~, it's also a matter of files in /tmp, directories you make, etc.

---

### Post by taurus on 2006-11-09
And if I remember it right, /tmp gets empty/cleanup at each boot and since /tmp contains only temp files, I wouldn't worry to much about rwx for everybody!!!  Otherwise, do it the long way, creating a file in /media/Storage and changing the permissions then...

---

### Post by krismatth3 on 2006-11-09
/tmp was an example. Not to start a flamewar, but umask=000 is plain insecure and _will_ get your system hacked.

Keeping in mind that "temp files" include socket connections - to connect to your X server, etc.

---

### Post by krismatth3 on 2006-11-09
Whoops, my original instructions were incorrect. Here's how I handle it on my systems:

sudo addgroup pubusers
sudo mkdir /pub
sudo chgrp pubusers /pub
sudo chmod g=rwx /pub
sudo chmod g+s /pub

Now, all files anyone creates under /pub will be rw to members of the given group (directories will be rwx). Add anyone you want to give access to /pub to the pubusers group.

(To add a user to a group: "usermod -G pubusers username")

---

### Post by taurus on 2006-11-09
I guess it's up to him what he wants to do to his /media/Storage then.  I am done with this subject and move on to some others then...

---

### Post by skathrein on 2006-11-09
Thanks for the input.  Just to clarify, I want to make my /media/Storage rwx for everyone, and rwx for everyone for any newly created file in that directory, and not mess with other directories.  That's why I wondered about an option in fstab.  I understand umask=000 type options (if I could use them) would weaken my security, but I don't really care as long as it works.  But I will try the chmod /pub stuff tonight when I get home.  Just out of curiosity, why did you decide that the sticky bit option would not work.  What would something like chmod 7777 do?

---

### Post by skathrein on 2006-11-11
Just as an update, I found a solution that essentially works like the limited umask option i was looking for.  I installed "acl" and "eiciel" using synaptic.  Then I ran the command to make sure that everything was rwx from the start:
sudo chmod -R 2777 /media/Storage
I'm not sure if the sticky bit is needed or not, but it worked and I don't see any harm.  Next, I fixed my fstab by adding acl as an option:
UUID    /media/Storage    ext3    defaults,acl    0    0
Then I rebooted.  After that I ran:
gksudo eiciel
This opens eiciel which I then used to open /media/Storage.  I made sure rwx was checked for everything, then clicked on "default acl" and made sure everything was checked, and then put a check mark in the default box and closed.  The chmod above also helps here because acl/eiciel does not act recursively but worked as I wanted so that all new files created will be rwx in this directory, but not others which would have been the case if I had run umask on the whole system.
[Thanks.]("http://inconsequentialstuff.blogspot.com/")

---

