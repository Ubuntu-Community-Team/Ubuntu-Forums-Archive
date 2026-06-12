---
title: "File Browser network mounts not available to some apps"
date: 2006-11-13
forum: General Help
---

### Post by danfluidmind on 2006-11-13
When I mount a Windows shared volume to my desktop with "Places->Connect to Server...", it works fine in the File Browser, but some applications simply don't see that mount at all--the Komodo IDE for one. Is there some way to make the File Browser mount Windows volumes to some particular location in the file system so that apps that aren't File-Browser-Savy can get to them?

Thanks
--Dan

---

### Post by earobinson on 2006-11-13
they should be in /media/<mount name>

---

### Post by danfluidmind on 2006-11-13
Nope, don't see them in /media. The only things in there are floppy and cdrom. I have an icon for the SMB volume on my desktop, and I can open it and work with the files. But I can't see that volume in Komodo, can't drag files from it into Komodo, and can't see it in /media.

--Dan

---

### Post by earobinson on 2006-11-13
maybe /mnt im not sure whats the path when you open the icon from the desktop?

---

### Post by danfluidmind on 2006-11-13
Not in /mnt either. That's the first place I looked.

In the File Browser windows the "path" shown at the top shows "Windows Network: servername" first, the "foldername on servername" after that. Then if you add a folder, it simply adds that folder's name after that.

That's why this is so odd to me. The File Browser doesn't show an actual filesystem path. Yet the volume doesn't show up in either /media or /mnt (where it should show up). It doesn't even show up as a mount at all when I do "df" at the command line!

The File Browser doesn't seem to actually mount into the file system but just seems to access the network drive with its own code, which is why other applications (like Komodo) which don't know how the File Browser is accessing those drives can't see them at all.

--Dan

---

### Post by lukemack on 2007-06-11
I am having the same problem in Komodo. Did you resolve this?

---

