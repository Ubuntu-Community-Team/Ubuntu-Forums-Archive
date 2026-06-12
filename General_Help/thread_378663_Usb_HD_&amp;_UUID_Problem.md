---
title: "Usb HD &amp; UUID Problem"
date: 2007-03-07
forum: General Help
---

### Post by MasterHead on 2007-03-07
Hi, I've just bought a new External Hard Drive but i cant get it work as i want, or more accurate where i want, when i turn it on it mounts fine, but it does in /media/LACIE, and i want it to be mounted in /datos/External.

as far as i know its an fstab issue( or its an automount thing? ), since being usb means it ca get a different dev each time depending on the usb drives im using, i guess i have to use UUID, so i get it,connect the drive see the dev it gets and run :

master@Amd64X2:~$ ls -l /dev/disk/by-uuid | grep sde1
lrwxrwxrwx 1 root root 10 2007-03-07 20:57 6853-5BA9 -> ../../sde1

master@Amd64X2:~$ sudo vol_id -u /dev/sde1
6853-5BA9

both ways tell me the UUID : 6853-5BA9, so lets go to fstab, and add the following line : 

# Disco LACIE de 500Gb
UUID=6853-5BA9 /datos/Ext500Gb auto nouser,noauto,atime,rw,nodev,noexec,nosuid 0 0

But, when i connect the drive again it just mounts in /media/LACIE, so i can only guess what ive done works only if i start up the computer with the drive attach and runnig( ill try now) but not when hot-plugging it.. ¿? 

how can i make it mount wherever i want? does it has to do with automount? and i so, how can i configure it?

Thanks a lot.. :)

---

### Post by MasterHead on 2007-03-07
i forgot to say that im using Kubuntu.. :)

---

### Post by dcstar on 2007-03-08
> **MasterHead said:**
> Hi, I've just bought a new External Hard Drive but i cant get it work as i want, or more accurate where i want, when i turn it on it mounts fine, but it does in /media/LACIE, and i want it to be mounted in /datos/External.
.......
how can i make it mount wherever i want? does it has to do with automount? and i so, how can i configure it?

Thanks a lot.. :)

Give the volume a label and it will mount with the label.

If you want another "Mount Point", then make a link to the real mount point.

---

### Post by MasterHead on 2007-03-08
Thanks for the reply.. :)

i had thought about that one but :

Option 1 : if i change label it would change the name of the folder but not the path, i mean changing it to, lets say, External, the drive will mount in /media/External instead of /media/LACIE, is this ok? so, it would be, still, in /media and i want this drive( not all external drives) in /datos. so it wouldn't what im looking for. At least as far as i know

Option 2 : Linking from /datos/External to /media/LACIE, this could do the trick, and if i cant find another way is what ill do, but i would like to do it directly and not using a workaround. 

I guess this has to be possible but i cant find the way to do it, as ive already seen it has nothing to do with fstab so it probably has to do with automount daemon, but no idea how to configure it.. ¿? where are the config files? how can i change the way autoconfig works? i have also hear that aoutoconf works different in ubuntu and kubuntu, that they use different daemons, is that true?  as said before im using kubuntu.

Thanks Again.. :)

---

### Post by MasterHead on 2007-03-08
a friend has told me to look for HAL + udev as it is what kubuntu uses instead of automount, so ill start digging that direction, lets see if i find something.. :)

---

### Post by MasterHead on 2007-03-12
Hi, i have find this little help about udev so ill try at home.. :) 
Where i found it : [http://informatics.ntu.edu.au/staff/kgilbert/miniHOWTOs/persistent_device_naming.html](http://informatics.ntu.edu.au/staff/kgilbert/miniHOWTOs/persistent_device_naming.html)

another interesting links : 

Gentoo wiki : [http://gentoo-wiki.com/HOWTO_Customizing_UDEV](http://gentoo-wiki.com/HOWTO_Customizing_UDEV)
and rules : [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

as said before ill try all this at home.. :) hope it helps out somebody else.. 
-----------------------------------------------------

   1.  Mount the device as normal
   2. Check the device name that has been assigned:

      tail /var/log/messages
   3. Obtain all the detailed information about the device from the sys file system:

      udevinfo -a -p `udevinfo -q path -n /dev/<device-name>`

      where, obviously, <device-name> is the name of the device discovered in the previous step.
   4. Create a file under /etc/udev/rules.d/ with a name that is before 50-udev.rules wrt the lexicographic order. If that file doesn't exist, look for one that has a similar name. In my case, I created the file 10-usb.rules.
   5. Using your favourite editor, add a line / lines that is / are similar to:

      BUS=="scsi", SYSFS{vendor}=="PENTAX", SYSFS{model}=="DIGITAL_CAMERA", KERNEL=="sd?1", SYMLINK+="camera"

      BUS=="scsi", SYSFS{vendor}=="SanDisk", SYSFS{model}=="Cruzer Mini", KERNEL=="sd?1", SYMLINK+="dosflash"

      BUS=="scsi", SYSFS{vendor}=="SanDisk", SYSFS{model}=="Cruzer Mini", KERNEL=="sd?2", SYMLINK+="linuxflash"

      BUS=="scsi", SYSFS{vendor}=="Maxtor", SYSFS{model}=="OneTouch", KERNEL=="sd?1", SYMLINK+="maxtor"

      The BUS, vendor and model information comes from the output of the above udevinfo command and the KERNEL information is the wildcarded device name. The SYMLINK parameter directs udev to create a soft link, with the specified name, to the device file.

      The upshot of all this is that when, say, I insert my USB flash drive, I get the files /dev/dosflash and /dev/linuxflash created. This means that I can code my /etc/fstab file knowing precisely what device will be mounted where.

---

### Post by MasterHead on 2007-03-12
i havent tried it yet but i have also look out how to make the trick with mount, mounting it as a bind :

mount --bind /media/LACIE /datos/Ext500Gb

this way its like having it mounted in /datos/Ext500Gb which its what i really want.

i can also do that in fstab :

 /media/LACIE /datos/Ext500Gb none bind

if later on i want to change the mount name :

mount --move  /datos/Ext500Gb  /datos/Ext500Gb-2

anyway, i still think there should be an easy way to config the mount point in udev.

---

