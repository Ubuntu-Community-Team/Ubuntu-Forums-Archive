---
title: "Flash USB Memory Stick Volume Decreased"
date: 2008-04-20
forum: General Help
---

### Post by OsakaWilson on 2008-04-20
I have a SanDisk Cruzer Mini 1.0GB USB Memory Stick. I can't seem to clear space on it to add new things. When I open the properties, I get this conflicting information:

Contents: 524 items, totaling 39.2 MB
Total capacity: 976.1 MB
Used: 917.2 MB
Free: 58.9 MB

If the contents total 39.2 MB, why is 917.2 MB used? When I review the content, it reflects the 39.2 MB.

Any ideas how I can fix this?

---

### Post by kyphi on 2008-04-21
Insert your USB stick and when the screen opens press Ctrl+h to reveal the hidden files.

My guess is that there is a very full ./trash folder on that device.  Delete it if you do not want the files that it contains.

---

### Post by niteshifter on 2008-04-21
Hi,

Check the trash folder on the device. Assuming a GNOME desktop, when the drive is mounted and the file browser window opens, press Ctrl+H to see all files and folders. The "trash can" in Ubuntu is a folder named .Trash-XXXX, where XXXX is your user name.

Note it's possible to have more than one .Trash-XXXX folder, one for each user of the device. Usage of the device with a LiveCD also counts.

Open each of the .Trash-XXXX folders and delete the contents by using Shift+Del. This actually deletes the files - just Del alone doesn't (moves items to a .Trash folder).

---

### Post by OsakaWilson on 2008-04-21
Yeah. The trash is full and it won't let me delete anything. It says it is a read-only disk. I add stuff to it all the time, so that is weird.

---

### Post by OsakaWilson on 2008-04-21
Now I'm clicking 'skip' for every file in the trash that it won't allow to be deleted. Been going at it now for five minutes.

---

### Post by OsakaWilson on 2008-04-21
Now there are little lock icons on each of the files in the drive.

---

### Post by kyphi on 2008-04-21
Eject and then reinsert the flash drive.

---

### Post by OsakaWilson on 2008-04-21
I did that and the lock icons went away, but it is still read-only.

---

### Post by kyphi on 2008-04-21
Right click on the icon of your usbdisk on your desktop and then go to Properties and then Permissions.

You should have Read, Write and Execute permissions.

---

