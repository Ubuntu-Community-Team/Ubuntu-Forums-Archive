---
title: "Unable to mount external USB devices"
date: 2012-11-22
forum: General Help
---

### Post by MdeVicente on 2012-11-22
When trying to mount an external USB device with my recently updated Ubuntu 12.10, an error message appears saying:

 *Adding read ACL for uid 1001 to `/media/user' failed: Operation not supported*

I never had such a problem with previous versions. Please, I would need help.

---

### Post by cjhabs on 2012-11-22
Maybe a permissions issue? My permissions on /media are 755 owner and group are root.
On the sub folders the permissions vary - you could change the "user" folder to 777 to make the permissions wide open. Also make sure that /media/user is a folder and not a file

---

### Post by MdeVicente on 2012-11-22
Looking for permissions I realized that the folder "user" didn't even exist. It seems that Ubuntu 12.10 doesn't mount the devices in the folder media directly, but in a subfolder with the name of the user. I created it and settled the permissions to 777, and my problem is already solved.

Thank you very much.

---

### Post by Ranimator on 2012-11-28
I have this same issue. (Never had it on previous versions of Ubuntu, but with 12.10 all external USB Thumb Drives I insert into the USB slot give the same  message.)

How did you solve this?

---

### Post by MdeVicente on 2012-11-30
To mount external devices you must have a folder with the name of your user in the folder *media*. As an administrator, you type in the console:

[FONT=Courier New]cd /media[/FONT]

to go to the media folder. Then:

[FONT=Courier New]sudo mkdir user[/FONT]

where *user* is the user name, to create the folder. The new folder belongs to the administrator. To make owner to your user:

[FONT=Courier New]sudo chown user user[/FONT]

Another choice is giving permission to everyone to write and read in that folder:

[FONT=Courier New]sudo chmod 777 user[/FONT]

After that I had no problem to mount external devices.

---

