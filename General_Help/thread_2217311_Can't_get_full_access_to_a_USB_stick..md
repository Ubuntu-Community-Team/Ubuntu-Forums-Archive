---
title: "Can't get full access to a USB stick."
date: 2014-04-16
forum: General Help
---

### Post by Extreedoc on 2014-04-16
I use a USB stick on my Precise 64 bit system but I don't have a "Format" command, so I deleted the files I didn't want. Thing is, I have no "Trash" file showing but in a Windows machine the trash file is there. What do I have to do to access the stick fully?

---

### Post by Kris_Spencer on 2014-04-17
Hello. I believe the behavior is to just delete the files and not use the trash. At least, that is what my computer has done just now. It's not unusual to have a hidden trash folder that Windows will show. If you are concerned that the deleted files didn't clear the space, you can delete this folder. If you want to format the device, you can use terminal, Gparted or disks (formally disk utility). Or you can format it in Windows too.

Hope this helps some

---

### Post by Extreedoc on 2014-04-17
Ok, thanks Kris, I must say it seems a bit of a faf, that trash file that shows in windows is filled with the files I deleted.

John.

---

### Post by mcduck on 2014-04-17
If you empty the trash bin on your desktop before removing the USB drive, the files will be properly deleted and won't stay on a trash folder on the device.

You can also use Shift+Del to delete a file immediately without putting it in the trash bin.

And finally, the trash bin on the device is just a normal hidden folder, so if you want to see it in the file manager just press Ctrl+H (or make the hidden files and folders visible by default in the file,manager's preferences)

---

### Post by Extreedoc on 2014-04-17
Thank you mcduck, I'll make a note of that.

Late edit: I have just discovered the "Format" command: Right click the stick's icon in the launcher and there is the format command.

---

