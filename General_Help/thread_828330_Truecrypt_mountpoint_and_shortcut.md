---
title: "Truecrypt mountpoint and shortcut"
date: 2008-06-13
forum: General Help
---

### Post by sparrowkc on 2008-06-13
I have a 250 GB usb HD that I just turned into a truecrypt drive.  There is also a small fat16 partition at the end of the drive.

I used visudo to make it so I don't have to type my password to do sudo truecrypt.  

When you use the truecrypt gui to mount, it mounts to /media/truecrypt(#).  Is there a way to make it create and delete those mountpoints from the command line?  If I try to mount from the command line the mountpoint has to already exist.

Also, I want to have a bash script that pops up the truecrypt password dialouge and asks for the password.  I have keyfiles in the small fat16 partition just so that I can secure delete them and destroy the drive if I need to.  <strike>How can I make truecrypt find this partition based on uuid or partition name (sdb2) instead of something like /media/disk?</strike>

EDIT: If I name the drive something is windows I can make it mount in /media/DriveName so that isn't a problem.

---

