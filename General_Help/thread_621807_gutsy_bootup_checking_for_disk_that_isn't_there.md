---
title: "gutsy bootup checking for disk that isn't there"
date: 2007-11-24
forum: General Help
---

### Post by OoooMatron on 2007-11-24
Every time I boot up gutsy tries to check for a disk that doesn't exist sending me to a command line that i have to exit from.

It appears to be the usb drive that it is trying to check but it's not registered in fstab so I don't understand why it's trying to mount something that isn't in the config file.

Where else is it picking it up from and how do i stop it trying to mount this drive?

---

### Post by banewman on 2007-11-24
The boot process will check all hardware as part of the process.
So why not remove the usb drive?

---

### Post by OoooMatron on 2007-11-25
> **banewman said:**
> The boot process will check all hardware as part of the process.
So why not remove the usb drive?

Sorry, I wasn't articulate enough in what I wrote. It checks for a non existent drive because the drive is not there (it's a USB thumb drive). I have plugged the USB in to test if it would find the "missing" device and it didn't work. So whether or not the drive is in or out, I still get this start up error on which i have to type "exit" at to continue the boot process.

I can't understand where it is finding the details on this drive to mount it, since there is no fstab entry.

---

