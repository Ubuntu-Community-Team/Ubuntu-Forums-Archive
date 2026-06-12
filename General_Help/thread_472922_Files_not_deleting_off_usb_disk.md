---
title: "Files not deleting off usb disk"
date: 2007-06-13
forum: General Help
---

### Post by dje on 2007-06-13
When i delete a file off my usb pen drive in ubuntu it appears to have been deleted but when i put the disk in windoze a folder appears called 'DJ .trash' . Does anyone know why this is and how to stop it happening?

Cheers

---

### Post by merlinus on 2007-06-13
Two choices:

Show Hidden Files (Ctrl-H) will show the trash folder created in ubuntu on your drive.  You can delete it, and everything will be gone.

Alternatively, pressing Shift-Del will send the selected file(s) into the ozone, never to be heard from again.

-merlin

---

### Post by stchman on 2007-06-13
> **dje said:**
> When i delete a file off my usb pen drive in ubuntu it appears to have been deleted but when i put the disk in windoze a folder appears called 'DJ .trash' . Does anyone know why this is and how to stop it happening?

Cheers

Yes, when you delete a file through Nautilus it sends the file to a hidden folder called .Trash

I find the best way to delete stuff off of a USB drive is to open a terminal in the USB drive and type:

rm -f ./<file to be deleted>

---

### Post by dje on 2007-06-13
Thanks merlinus and stchman, ill try all three ways and see which works best for me :D

---

### Post by ajgreeny on 2007-06-13
You should also make sure you unmount your usb drive before removing it from the usb socket.  If not the delete action may not have been performed, as I think ubuntu waits until unmounting these drives before it undertakes certain actions.

---

