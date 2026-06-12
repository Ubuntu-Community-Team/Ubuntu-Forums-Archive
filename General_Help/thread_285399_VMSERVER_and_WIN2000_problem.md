---
title: "VMSERVER and WIN2000 problem"
date: 2006-10-26
forum: General Help
---

### Post by matjaz_pirnovar on 2006-10-26
Hi,

When installing WIn2000 on vmserver I get WARNING that if I'm running OS that is incompatible with WIn2000, then current OS might be damaged or deleted if I continue. Something like that. Please see the screenshot.
Should I proceed with installation?

[IMG]http://static.flickr.com/108/280138632_27b2998655.jpg?v=0[/IMG]

---

### Post by matjaz_pirnovar on 2006-10-29
Any clues about that? Has anyone had negative experience with vmserver?

Matjaz

---

### Post by matjaz_pirnovar on 2006-11-04
Hi,

On my WIn2000 on vmserver, windows don't recognize USB key when I plug it in (usb drive appears only in Ubuntu).
And I don't know how to install any programmes like word or Excell.

How do you work with Virtual OS without including Ubuntu? 

Thenks, M

---

### Post by sefs on 2006-11-04
When you add a virtual disk in VM ware I dont think its formatted by default, unless you formatted it with qparted/gparted before installing win 2000 so  that looks like windows is looking at your unformatted virtual disk and just telling you that it can't detect a file sytem on it.  So...it will go thru the process of formatting it for you to NTFS or FAT32 (your choice).  It can in no way see your real OS disk unless you chose the type of virtual disk that give it direct access to your hard disk, which would be bad in your case.

VMware server does not support USB Devices I dont think so you wont get to see your plugged in usb devices.  But to get around that if your USB device is formatted as NTFS or FAT 32 you can give the virtual macine acces to a USB HD by simply adding a new vitual disk and there is an option in there that sets this virtual disk to have direct access to any Hardisk your HOST OS can see.

---

### Post by FrankVdb on 2006-11-04
You can go ahead with your installation.

Windows 2000 is not able to see outside the space you have reserved for your virtual machine. All it sees is an empty (unformatted) hard disk. Use NTFS, it's better than FAT.

---

### Post by matjaz_pirnovar on 2006-11-07
Thanks guys, will try so.

Matjaz

---

