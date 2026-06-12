---
title: "Problem with automounting W95 VFAT32 removable media in Ubuntu 12.04 LTS"
date: 2013-03-02
forum: General Help
---

### Post by website.reader3 on 2013-03-02
Recently the automount for my USB stick has stopped working.  The kern.log and the syslog show that the kernel detects the USB stick just fine and correctly identifies it.  Even the gnome desktop under the Places --> Computer window shows the device icon correctly.  But the df command refuses to show the mounted device and I have to manually mount it by clicking on the icon.

Some study shows that perhaps the handling of the org gnome desktop media-handling automount schema is the problem here.

Can someone suggest how I can examine the scripting for this, to see if they handle VFAT32 files???

I tried the traditional pmount, autofs, usbmount, kludge the /etc/fstab file fixes, but they all are unsatifactory.  All I want is automounting of the USB drive, whenever I plug it into a USB port.

Thanks.

---

### Post by fdrake on 2013-03-02
is you USB labelled  ? I do have to mount by clicking too to the icon. I cannot remember if it was always like that but if it wasn't it is probably dude to some kind of kernel update. Can you post your "uname -a" ? If you want a specific filesystem from usb be mounted directly add a setting int grub.

Personally I think this is a good feature, sometimes is not wise to mount automatically a device , like a usb . But if you want to use the command udisks and assing an automount like with cd-roms (i think you can also costumize it by the type too) 
[http://igurublog.wordpress.com/2011/01/26/a-custom-udisks-automounter/](http://igurublog.wordpress.com/2011/01/26/a-custom-udisks-automounter/)

```

man udisks

```
> 

       --mount device_file [--mount-fstype fstype] [--mount-options options]
           Mounts the device represented by device_file using the file system fstype and a comma-separated list of options.

       --unmount device_file [--unmount-options options]
           Unmounts the device represented by device_file using a comma-separated list of options.



---

### Post by website.reader3 on 2013-03-02
Some further research shows that some new rules possibly need to be manually added to the udev rules section, most likely in the /etc/udev/rules.d folder, perhaps as an 80-xxx rule.  I do have the vendor ID and the PID for this USB removable media, but a quick check through the udev rules did not turn up any match on the VID.  The kernel is detecting and mounting the device as a scsi generic sg3 tpe 0, so that appears to be okay.  Does anyone know how to write new udev rules for USB devices?

---

### Post by website.reader3 on 2013-03-03
This is the final answer to my question, please consider the question and topic closed.

A comment on fixing automounting for a Sandisk Cruzer usb thumb drive -

I had to add a new udev rule into /etc/udev/rules.d/ folder called 99-Sandisk.rules

This rules file reads:

ACTION=="add" ATTRS{idVendor}=="0781", ATTRS{idProduct}=="5530", SYMLINK+="sandisk" RUN+="/home/owner/usb_add"
ACTION=="remove" ATTRS{idVendor}=="0781", ATTRS{idProduct}=="5530", RUN+="/home/owner/usb_remove"

end quote

The Vendor ID's and Product ID's are available at [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids). You might be able to retrieve this information using the "lsusb" command also (if your drive is already mounted onto the system)

The first rule runs the /home/owner/usb_add script which creates a directory in the /media/ folder area
Then the usb device is mounted using the current user id and group id numbers, to allow read/write access.

The second rule simply unmounts the usb thumb drive and then erases the directory folder in the /media area

I still cannot get gnome-volume-manager to leave things alone, it keeps insisting upon putting up a USB removable media icon.

Any idea how to fix the gnome-volume-manager or nautilus for automounting?

I do have something which works now, but this was a minor pain.

Can anyone update the udev rules tutorial for Ubuntu 12.04 LTS ??? (following some of the previous postings revealed out of date information)

Btw: The "udevadm info" and "udevadm test" commands along with the /var/log/kern.log had to be used to troubleshoot the udev rule. The "udevtest" command seemed unavailable under Ubuntu 12.04 LTS as is "dev-discover" (which seems to be a very nice tool)

---

### Post by dcstar on 2013-03-04
> **website.reader3 said:**
> This is the final answer to my question, **please consider the question and topic closed**.
.......

Then MARK the thread.

---

