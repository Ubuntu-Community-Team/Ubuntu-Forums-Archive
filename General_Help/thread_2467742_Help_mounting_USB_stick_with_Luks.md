---
title: "Help mounting USB stick with Luks?"
date: 2021-10-06
forum: General Help
---

### Post by grandkodiak2 on 2021-10-06
My distro will no longer boot unless it goes to command line safe mode. Not a problem, my fault forgetting not to ever upgrade cause it never ever boots after doing so (experimental tablet toy for tinkering)

I have files on a USB stick that I can't seem to mount via cli that I'd like to salvage before reflashing.

it shows up as sda 

i created a directory media/usb

when i do 

mount -t /dev/sda /media/usb

I get

mount: /media/usb: can't find  in etc/fstab

also tried changing sda to sda1

lsblk shows sda with a disk type, and sda1 as part type

i hate command lines. 

help?

when i googled the error, all the solutions say that people are forgetting to make the mount directory and mount command... but i GET the error doing just that.

only thing i can think of is that the usb stick was encrypted with luks months back. i know the password. unfortunately, if i plug it into my ubuntu pc, it will mount automatically with the luks password, but then gives me an access denied when trying to view files once mounted. im guessing the key file i need is still on the tablet? i cant mount a usb drive so i cant pull the key file if one exists off anywhere even if i knew where it was lol. i only played around with it, never got further into how luks works. otherwise i would just pull the files onto the pc and flash the tablet fresh and start over. when the gui was working, i just opened the file explorer, plugged it in, it asked the password and then i could see/edit the files on the usb drive.

---

### Post by TheFu on 2021-10-06
With LUKS, you have to use "cryptsetup open" command.  The manpage has details.
This will create a device, hopefully with a file system that can be mounted.

If cryptsetup is already loaded and the file system stuff is available - some setups will need LVM too - then a file manager like Caja will prompt for each step along the way.  If you search for "the bald nerd luks", he has some setup and access video guides and text steps that could be helpful.  

I've posted steps in these forums too - probably 2-3 yrs ago. Look for *cryptsetup open* and my userid.

Sorry that you had the CLI. 

BTW, if you leave off the leading / character like you've done above, it won't work.

etc/fstab is NOT the same as /etc/fstab.
Details matter.

---

