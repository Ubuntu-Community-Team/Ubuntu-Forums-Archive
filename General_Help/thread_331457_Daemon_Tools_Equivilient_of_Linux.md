---
title: "Daemon Tools Equivilient of Linux?"
date: 2007-01-04
forum: General Help
---

### Post by AMCDeathKnight on 2007-01-04
What is the Daemon Tools of Linux?

I want to be able to mount ISOs easily as CDROM Drives in Ubuntu.

---

### Post by taurus on 2007-01-04
Applications -> Accessories -> Terminal
```
sudo mount -t iso9660 -o loop **filename.iso** /media/cdrom
```

---

### Post by AMCDeathKnight on 2007-01-04
Thanks, I didnt realize it was built in. I will test it when I get home.

---

### Post by challahc on 2007-01-04
Although it has nothing to do with what you are trying to accomplish, this is daemontools for linux: [http://cr.yp.to/daemontools.html]("http://cr.yp.to/daemontools.html").  It is service management, a way to monitor and automatically restart daemons.  I was confused when I ran across the windows Daemon Tools, and still am not sure why it's called that.

---

### Post by AMCDeathKnight on 2007-01-04
Because Daemon Tools( [http://www.daemon-tools.cc](http://www.daemon-tools.cc)) Does the Virtual CD mounting in Windows.

---

### Post by challahc on 2007-01-04
Right, I just don't see how that name fits for that application.

---

### Post by AMCDeathKnight on 2007-01-04
To be honest, neither do I

Thanks for your help guys

---

### Post by kEinstein on 2007-01-04
There are lots of programs & scripts that allow you to mount ISO as well as NRG, UDF, CUE/BIN and other formats without having to touch a terminal command.
e.g. you might want to go for [mount-iso-image]("http://freshmeat.net/projects/mount-iso-image/")
alternatively, use gISOMount via apt-get or synaptic.
Probably one of the most powerful tools is 'dares' which enables you to read the content of damaged ISO images...

---

### Post by cmost on 2007-01-04
I agree with KEinstein, there's no need to memorize archaic commands to mount an ISO.  I have two simple Nautilus scripts that will mount and unmount ISO images respectively.  Here they are.  Copy them into separate files, make the files executable, and then copy them to ~.gnome2/nautilus-scripts.  Note:  When mounting or un-mounting, you'll need to enter your root password, unless you change the syntax of the files.  Enjoy!

To Mount an ISO image:
Filename "Mount-ISO-image"
Contents:
#!/bin/bash 
#
# Mount an ISO file 
for I in "$*" 
do 
foo=`gksudo -u root -k -m "enter your password for root terminal 
access" /bin/echo "got r00t?"` 
sudo mkdir /media/"$I" 
sudo mount -o loop -t iso9660 "$I" /media/"$I" && nautilus /media/"$I" --no-desktop 
done 
done 
exit0

To Unmount an ISO image:
Filename "Un-mount-ISO-image"
Contents:
#!/bin/bash 
#
# Unmount ISO image 
for I in "$*" 
do 
foo=`gksudo -u root -k -m "enter your password for root terminal 
access" /bin/echo "got r00t?"` 
sudo umount "$I" && zenity --info --text "Successfully unmounted /media/$I/" && sudo rmdir "/media/$I/" 
done 
done 
exit0

---

