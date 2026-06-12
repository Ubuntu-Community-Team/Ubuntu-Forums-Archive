---
title: "Ubuntu and OSX dual-boot, how to make a shared folder?"
date: 2007-01-03
forum: General Help
---

### Post by Gen2ly on 2007-01-03
OSX creates a Shared .Folder for all users of the computer in /Users/<user name>/Public  it's accessible to anyone on the network.  I want to be able to read-write from this directory in Ubuntu.

Here's what I tried:

sudo mkdir /mnt/MacBook_OSX
sudo mount /dev/sda2 -t hfsplus -o rw /mnt/MacBook_OSX

added the correct values to have this partition recognized at boot in fstab:

 /dev/sda2 /mnt/MacBook_OSX hfsplus rw,exec,auto,users 0 0

Every thing shows and appears ok.  So I cd to /Users/<login name>/ and goto link the Shared (Public) Folder:

ln -s Public /home/<user name>/Desktop/MacBook_Shared_Folder

link shows on Ubuntu desktop, but has a lock on it.  Clicking on link opens the window but when I drop files on it I get

"You do not have permissions to write to this folder."

So I try to copy in terminal a file from Ubuntu to the OSX shared directory:

sudo cp test_test /mnt/MacBook_OSX/Users/<user name>/Public
cp: cannot create regular file `/mnt/MacBook_OSX/Users/<user name>/Public/Helpful Tidbits': Read-only file system

Any Ideas?

---

### Post by shane2peru on 2007-01-03
This is only a hunch, I don't know anything about MAC systems or the filesystem or type.  Anyway, based on all written here, you may need to play with the fstab line.  The other thing that I would try is changing the owner and group of the media.  You can do that by going to /mnt
then typing ```
sudo chown -R username MacBook_OSX  
```  You will need to plug your user name in there.  The next thing you will want to do is change the group ```
sudo chgrp -R username MacBook_OSX 
```  This should give your user privileges to read and write to it.  You may need to change the permissions on it as well ```
chmod -R 777 MacBook_OSX
```  Like I said, I don't know if this will fix it for you or not.  If you want to see what the current settings are before trying this, just type```
ls -l 
``` and it will tell you what user owns it, and what group it is in, and what the rw access is on it.  That is the easiest way that I can think of to fix it up, and should let you write to it.  If not it is probably an fstab problem, but that seemed to look fine to me.

Shane

---

### Post by llanitedave on 2007-01-03
Is "***MacBook_Shared_Folder***" the actual name of the shared folder?  On my iBook and the wife's eMac the name of the shared folder is simply "Shared."

If it was created separately on a MacBook personal account it might have the account-holder's restricted permissions attached to it.  The generic "***Shared***" folder on a Mac is in the ***Users*** directory, but it's not attached to any individual user.  It's like a user of its own.

---

### Post by Gen2ly on 2007-01-05
appreciate the input there shane.

I tried as suggested and for kicks and giggles another:

> sudo chown -R username Public
sudo chmod 755 Public

and got back "Read-only file system"

Somehow my drives being mounted read-only.  

llanitedave, or anyone else, is there a reason why I'm only getting ro(read-only) from this mounted partition?

---

### Post by Gen2ly on 2007-01-07
Moved to [Apple PPC forum]("http://ubuntuforums.org/showthread.php?p=1981765#post1981765") as it seems to be an issue with the HFS+ file system mount.

---

