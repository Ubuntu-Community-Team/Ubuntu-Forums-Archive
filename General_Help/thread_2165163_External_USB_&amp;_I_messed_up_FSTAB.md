---
title: "External USB &amp; I messed up FSTAB"
date: 2013-08-03
forum: General Help
---

### Post by Mark_in_Hollywood on 2013-08-03
Using GParted to format a hdd with partitions to use with MythBuntu, I found after partitioning that user is not owner of device. Netsearching for help gave: [http://askubuntu.com/questions/74806/how-can-i-change-permissions-on-external-drives](http://askubuntu.com/questions/74806/how-can-i-change-permissions-on-external-drives)

and following the lines (cut & paste, did I) ran:

Here's the procedure:

Open "Disk Utility", and look for your device, and click on it. This will let you be sure you know the correct filesystem type and device name for it. In my case, it was 'ext4' and '/dev/sdb1' respectively. Next: Decide what you want to call your thumb drive. I called mine 'USB16-C', but you choose your own name. Before closing Disk Utility, click unmount. And USER should be your login name.

    Then run steps 2 to 4 in a terminal window.

    sudo mkdir -p /media/USB16-C

    sudo mount -t ext4 -o rw /dev/sdb1 /media/USB16-C

    sudo chown -R USER:USER /media/USB16-C

then I ran:

sudo mkdir /mnt/sdd1

Edit /etc/fstab and add to the end:

/dev/sdd1 /mnt/sdd1 fuseblk defaults,umask=022 0 0

Then at the command line (to process the /etc/fstab file again):

mount -a

and then decided to add another partition, went back to GParted and created it.

Next I tried to above sudo mkdir and such and edited a line in /etc/fstab.

On next power up Grub defaults to choice of Boot or Recover Mode. On my selecting Boot, splash screen offers to skip mounting, edit mounting or cancel. 

Using sudo nano /etc/fstab, what had been sde1 is now sdd.

I tried sudo rmdir /mnt/wd160 and sudo rmdir /media/wd160 and (2nd part name) wd160cine

Lastly, a 256 meg usb stick, which I think used to be /sdd is now not in GParted. I tried changing it to another usb port, but no success.

So, while I know I've messed this up, I have to idea what question to ask except:

HHHHEEEEELLLLLLPPPPPPPPP?

Current terminal:

mark@Lexington:/media$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Thanks for reading.

---

### Post by sudodus on 2013-08-03
You should use ***UUID*** or possibly a ***label*** to identify the devices in ***fstab***, because the **[FONT=courier new]/dev/sdx[/FONT]** id will change in a way that is hard to predict.

See also the manual pages

```
man fstab
```
and
```
man mount
```

Example 1, my root partition (on an SSD which is why I have the options discard and noatime)

```
UUID=cdc8e357-36af-43bd-91fc-030c21ef9887 /               ext4    defaults,discard,noatime,errors=remount-ro 0       1
```

Example 2, an external drive that is not mounted automatically

```
UUID=d264ff5d-4269-4636-be41-1f153c01ee9d /media/akasa1    ext3    defaults,noauto 0       0
```

And reboot once more, it might help if the system is confused about the devices.

---

### Post by Mark_in_Hollywood on 2013-08-03
This line:

UUID=1da090d4-e5fe-4866-8ca5-5a89abb17045  /media/wd160 ext4    defaults        0  0

added to /etc/fstab. The UUID number found by GParted, highlighting the /dev/sXXX and right clicking, then copying UUID number in "Information".

device now on my desktop, I am "owner" (permissions are correct). Device is: /dev/sde1

thanks to you, Sudodus.

---

