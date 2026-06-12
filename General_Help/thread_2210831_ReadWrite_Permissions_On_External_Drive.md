---
title: "Read/Write Permissions On External Drive"
date: 2014-03-12
forum: General Help
---

### Post by Wbie on 2014-03-12
I have a Seagate external drive.  When connected to my Ubuntu (13.10; Cinnamon Desktop) install everything works good ***except*** for changing the permissions.  When I go to try to change the permissions I get "permissions cannot be determined."  Any idea how I can change the permissions?

---

### Post by tfrue on 2014-03-13
Will you post the commands you used and their error outputs?

Thanks
Chris

---

### Post by Wbie on 2014-03-13
I was using the GUI.

---

### Post by Impavidus on 2014-03-13
What file system is used on the external drive? After connecting and mounting through the GUI, use the **mount** command to determine the mount options and FS type from the command line. Indicate which lines in the output of mount refer to your external drive.

---

### Post by mcduck on 2014-03-13
> **Impavidus said:**
> What file system is used on the external drive? After connecting and mounting through the GUI, use the **mount** command to determine the mount options and FS type from the command line. Indicate which lines in the output of mount refer to your external drive.

+1 to this.

Only Linux file systems support permissions and ownerships, so if your drive is formatted as FAT or NTFS it's not bale to handle the permissions or ownerships and therefore you can't use commands like chmod and chown (or their graphical equivalents) on individual files or directories. Instead the ownership and permissions are set for the whole file system at the time it's mounted.

---

