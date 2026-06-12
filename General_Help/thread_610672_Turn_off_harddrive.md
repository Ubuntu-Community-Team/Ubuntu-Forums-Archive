---
title: "Turn off harddrive"
date: 2007-11-12
forum: General Help
---

### Post by plop166 on 2007-11-12
Hello all,

I am booting Ubuntu off a 4gb usb key and it works great. So good in fact that i would like to power off the local hard drive on my laptop while im using Ubuntu (to cut down on noise). Any suggestions on how to go about doing this?

Also now that i have ubuntu up and running on a usb key, is there any way to transfer the instalation from the key to a partition on the harddrive?

Thanks for any help you can provide,

Plop

---

### Post by wieman01 on 2007-11-12
> **plop166 said:**
> Also now that i have ubuntu up and running on a usb key, is there any way to transfer the instalation from the key to a partition on the harddrive?
You could pretty much copy & paste it, that's all. You need to do so while you are logged on as root.

As for turning off the HD, all I can suggest is the BIOS. But that's probably not what you want.

---

### Post by justin_guerin on 2007-11-12
In my experience, if you don't mount the hard drive, it won't spin up.  Make sure you're not using the hard drive for swap space, either.

You can transfer the installation from USB key to the hard drive by copying all files and then editing some.  You'll have to edit /etc/fstab and point the file system mounts to the hard drive, and you'll have to install the boot loader on the master boot record of the hard drive.  You'll also have to make a new initial ram disk / kernel image with the modules required to read your hard drive.

It may be easier to install to the hard drive and transfer your settings and personal files.  From the USB key, you can save the list of installed packages with 'dpkg --get-selections > myselections.txt'.  This will write the list of packages you've installed to myselections.txt.  Once you've installed to the hard drive, boot from it and run 'dpkg --clear-selections', and then run 'dpkg --set-selections < myselections.txt'.  This will set the package selections to match your USB key.  To actually install them, use a front end like dselect.  For dselect, use 'dselect install' and that should install all the packages you've selected.  You can also use aptitude, wajig, or another front end to install the packages, but I'm not familiar with their syntax enough to tell you which command to use.

Once you've installed all the packages, you can selectively copy over files from /etc if you've done any customization, but make sure you don't copy over /etc/fstab, as it's supposed to be different.  

Also, you can copy over all your personal files by copying the /home directory, but make sure that your user IDs are the same on both installs.  If they're not, boot from the hard drive, mount the USB key, and copy as your user so as to become the new owner of the files.

Incidentally, how did you install to the USB key?  I'd like to do that myself.

Thanks,
Justin

---

