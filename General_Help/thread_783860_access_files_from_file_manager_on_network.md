---
title: "access files from file manager on network"
date: 2008-05-06
forum: General Help
---

### Post by dbrine on 2008-05-06
Sorry for the weird description. I am trying to open files from inside programs (music for example) that are located on the network drive. However there isn't a network tab to browse. I can see all physically attached drives (ie usb drive, local drive) bit not the network. How do I open network locations?:confused:

---

### Post by danwood76 on 2008-05-06
You need to mount the network drive.

If you are using hardy I think it does this automatically when you open a network location.

---

### Post by dbrine on 2008-05-06
I mounted the drive but I don't see it in file manager (mplayer for example)

---

### Post by dbrine on 2008-05-06
when i mount it, where it it mounted to? /mnt? /media?

---

### Post by chrisccoulson on 2008-05-06
For applications which have been ported to GVFS, you should be able to access network shares in the same way as you would in Nautilus.

However, you're referring to an application which isn't ported to GVFS. In order to access network shares in this case, navigate to ~/.gvfs. This folder should contain the network shares which you are connected to.

---

### Post by danwood76 on 2008-05-06
They might be mounted in the ~/.gvfs folder.
The mounting is done by gvfs now you see.

I cant mount any network shares at the moment so I cant test this myself.

Have a look in nautilus, go to your home folder and view hidden files and look in the .gvfs folder.

---

### Post by dbrine on 2008-05-06
how would you normally access files from all programs, like windows, where you can browse the network?

---

### Post by dbrine on 2008-05-08
????

---

### Post by danwood76 on 2008-05-08
I tend to browse to the folder I want, mount it and access what I need from there, normally copying stuff I want to edit and copying it back after.

Before hardy I used to mount network folders through the cli but the new gvfs seems to like doing it over the GUI.

---

