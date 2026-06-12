---
title: "USB Driver Automount System"
date: 2005-10-23
forum: General Help
---

### Post by nfvindaloo on 2005-10-23
Hi

Can anyone help me by telling me the name of the subsystem which handles automatic mounting/unmounting of usb disk drives? I need to find out how to change the default permissions.

Thanks
Nic

---

### Post by irv on 2005-10-23
Right click on the USB Drive icon, go to properties and select the Permissions tab. If you are trying to change the right for a NTFS Drive forget it. It will only be read only because Linux doesn't like NTFS.

---

### Post by nfvindaloo on 2005-10-23
Yeah ive tried that, but the device is mounted read-only so i cant. My main problem is that i want to change the configuration so that whenever i plug in a device, it is mounted with rwx permissions, as it stands i only have r-x permissions. Also i just want to know more about this system, I think it michet be UDEV or HAL, but im just after some clarification.

Thanks
Nic

---

### Post by irv on 2005-10-23
Try going to a termial window and using the chmod (change access permissions) command. To get information on the the command type: chmod --help.

---

### Post by sutter2k on 2005-10-28
I would like to know the solution to this as well. My rio carbon keeps getting mounted as readonly.  Even root cannot do anything to the filesystem because it says the device is readonly.

??
I don't think chmod is the answer.  e.g -->
chmod +w CARBON
chmod: changing permissions of `CARBON': Read-only file system


It the way udev is automounting it.

---

### Post by terrax on 2006-03-24
I got the same problem. Found any solution?

---

