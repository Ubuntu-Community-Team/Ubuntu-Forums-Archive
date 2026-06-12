---
title: "Mounting queries"
date: 2008-06-17
forum: General Help
---

### Post by hey_ram on 2008-06-17
Hi!

I am facing some problems with mounting my windows partitions. I went through the earlier thread regarding mounting troubles. Though initially I too was facing the same problem, I sorted it out with a lot of help from that thread. My trouble is as follows:

I am running a dual boot system (win XP with ubuntu 8.04). i tried to mount the drives using the command:

 sudo mount /dev/sda5 /media/sda1

I get the following message:


$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /media/sda1 ntfs-3g force 0 0

i may have shut my computer down with the hibernate option instead of shutdown and restart before i booted into linux. could that be a problem? also, if I do force the mount, will it cause any significant problems?

---

### Post by iaculallad on 2008-06-17
> **hey_ram said:**
> Hi!

I am facing some problems with mounting my windows partitions. I went through the earlier thread regarding mounting troubles. Though initially I too was facing the same problem, I sorted it out with a lot of help from that thread. My trouble is as follows:

I am running a dual boot system (win XP with ubuntu 8.04). i tried to mount the drives using the command:

 sudo mount /dev/sda5 /media/sda1

I get the following message:


$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda5': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda5 /media/sda1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda5 /media/sda1 ntfs-3g force 0 0

i may have shut my computer down with the hibernate option instead of shutdown and restart before i booted into linux. could that be a problem? also, if I do force the mount, will it cause any significant problems?

Are you sure that your /dev/sda5's mountpoint is your /media/sda1? Well if that's the correct mountpoint, you can force mount by issuing the command below in your terminal (choice 2):

sudo mount -t ntfs-3g /dev/sda5 /media/sda1 -o force

---

### Post by hey_ram on 2008-06-17
hey iaculallad,

thanx for the reply..

this what my file /etc/fstab shows:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=1c9c07c8-0845-4c5e-969e-3af842cfc403 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=f7e526bf-1bcb-49b4-9695-9e45855a07cd /boot           ext3    defaults        0       2
# /dev/sda1
UUID=7814C80E14C7CD76 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=127EA67971283829 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=6fe17aed-348d-4746-9745-4b6cdc819ef0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


according to this, the mount point for /dev/sda5 should be /media/sda1 and /dev/sda7 should be /media/sda5 right??

---

### Post by iaculallad on 2008-06-17
No, try referring on the commented part of your fstab file (#): Force mount it using this command instead:

If you're force mounting your sda1:

```
sudo mount -t ntfs-3g /dev/sda1 /media/sda1 -o force
```

If you're force mounting your sda5:

```
sudo mount -t ntfs-3g /dev/sda5 /media/sda5 -o force
```

---

### Post by hey_ram on 2008-06-17
oh yes...

i get it now...a stupid mistake..
thanx for the help....

also, would force mounting the drive (say /dev/sda1) result in some serious effects on the drive?

---

### Post by iaculallad on 2008-06-17
> **hey_ram said:**
> oh yes...

i get it now...a stupid mistake..
thanx for the help....

also, would force mounting the drive (say /dev/sda1) result in some serious effects on the drive?

In most of my experiences with force mounting, I would say no.

---

### Post by hey_ram on 2008-06-17
is there any way i could make those changes permanent?
i mean..if i edit /etc/fstab and replace (or comment out with a '#') the commands for mounting sda1 and sda5 and instead replace them with the force mount equivalents....

a. would it be a good idea??
b. or should I just write another script and execute it every time i boot ubuntu?

---

