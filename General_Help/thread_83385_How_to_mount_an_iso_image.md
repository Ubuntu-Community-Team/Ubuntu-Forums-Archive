---
title: "How to mount an iso image"
date: 2005-10-28
forum: General Help
---

### Post by PriceChild on 2005-10-28
he, how do i mount an iso image?

Simple question :)

Thanks for any help,
                         Pricey

---

### Post by kashms on 2005-10-28
mount -t iso9660 -o loop file.iso /mnt/point

---

### Post by heimo on 2005-10-28
```
sudo mount -o loop image.iso mountpoint
```
where mountpoint is existing directory

---

### Post by aysiu on 2005-10-28
What are you mounting it for--to browse the files? Or is this a live CD you want to emulate a boot from without burning an actual CD?

---

### Post by satbunny on 2007-12-07
I would like to mount an ISO image every time I boot the PC.
What is the correct line to add to fstab or is that not the right way to do it?

---

### Post by geirha on 2007-12-07
> **satbunny said:**
> I would like to mount an ISO image every time I boot the PC.
What is the correct line to add to fstab or is that not the right way to do it?

It's one way of doing it, and it's not wrong :)

Adding something like this line to /etc/fstab should do the trick: 
```
/path/to/image.iso /media/image iso9660 defaults,loop 0 0
```

Of course change /path/to/image.iso to the actual absolute path of the iso, and change /media/image to whatever directory you want to mount it to, and make sure that directory exist.

---

### Post by edm1 on 2007-12-07
Two nautilus scripts i found somewhere on this forum ages ago serve me well. They go in ~/.gnome2/nautilus-scripts

Mount
```
#!/bin/bash
#
# nautilus-mount-iso

gksudo -u root -k /bin/echo "got r00t?"

sudo mkdir /media/"$*"

if sudo mount -o loop -t iso9660 "$*" /media/"$*"
then
        if zenity --question --title "ISO Mounter" --text "$* Successfully Mounted.
        
        Open Volume?"
        then
                nautilus /media/"$*" --no-desktop
        fi
        exit 0
else
        sudo rmdir /media/"$*"
        zenity --error --title "ISO Mounter" --text "Cannot mount $*!"
        exit 1
fi
```

Unmount
```
#!/bin/bash
#
for I in "$*"
do
foo=`gksudo -u root -k -m "enter your password for root terminal
access" /bin/echo "got r00t?"`

sudo umount "$I" && zenity --info --text "Successfully unmounted /media/$I/" && sudo rmdir "/media/$I/"
done
done
exit0
```

---

