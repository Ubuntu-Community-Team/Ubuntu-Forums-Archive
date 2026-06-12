---
title: "Create a link between two home folders."
date: 2018-05-15
forum: General Help
---

### Post by wallacegalloway on 2018-05-15
Just installed 18.04 to a 64GB SSD drive. Since I will only be using it as a boot drive I would like to directly download files to my home folder on my second hard drive. In other words, a soft link between my home folder on the SSD and the home folder on my mechanical drive. This way if I decide to reformat and install the OS again I won't lose my files since they are actually stored on my hard drive. I'm a little confused as how to go about this since last time I just used nautilus as root and created a link. But I'm sure there must be a more simple way. Any help is appreciated..thanks.

---

### Post by again? on 2018-05-15
1st step would be to create an entry in /etc/fstab to automount your drive where you want your folder linked to.
```
gedit admin:///etc/fstab
```

eg I autommount a [COLOR="#000080"]Data drive[/COLOR].
My fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=a5fd3901-9409-4ab8-9e37-374c3bca427a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=dac1b216-5ba6-4d5e-a6b9-f8917aa60845 none            swap    sw              0       0

[B][COLOR="#000080"]# Data Drive /dev/sdb1
UUID=7817a27f-9b0e-4677-b55b-25865a5411d6 /media/Data ext4 defaults 0 0[/COLOR][/B]
```

To get your UUID use...
```
sudo blkid
```

Reboot 

Create your sym link.
If both accounts use the same login name permissions should be ok.
Open a terminal and make sure you are in the directory where you want the link created.
```
cd ~
ln -s /path/of/directory/to/link
```

As an example these are the link commands I run after adding my data drive to fstab and rebooting.
```
ln -s /media/Data/glen/bin
ln -s /media/Data/glen/conky
ln -s /media/Data/glen/Music
ln -s /media/Data/glen/scripts
ln -s /media/Data/glen/Sounds
ln -s /media/Data/glen/Pictures/wallpaper ~/Pictures/
ln -s /media/Data/glen/.icons
ln -s /media/Data/glen/.fonts
ln -s /media/Data/gPodder
```

---

### Post by wallacegalloway on 2018-05-15
Thanks..but still confused. I mounted the second drive on installation. So I have my ssd drive "/home/user/Downloads" and I have my second hard drive /bigdrive/Downloads.  So would I go into the directory (via terminal) /home/user/Downloads and create:

ln  -s  /home/user/Downloads    /bigdrive/Downloads

---

### Post by vanadium on 2018-05-15
If the drive is automatically mounted during startup, it is sufficient to create the link: ln -s <target> <link name> (if you omit <link name>, the link will be created in the current folder and have the file name of the target.). Probably what you are after is to access your bigdrive from within your home, so the command should be
```

ln -s /bigdrive/Downloads /home/user/Downloads 

```
You first will need to remove (or rename or move) the existing Downloads folder in your home folder, because the link is supposed to replace that folder.

---

### Post by wallacegalloway on 2018-05-15
Got it figured...thank you!

---

### Post by again? on 2018-05-15
If I got this right, you want your downloads from your 64GB SSD drive to link to your other drive so that your downloads
reside on the mechanical drive.

You would need to boot into the SSD with the mechanical drive automounted.
From there create your symlinks as indicated earlier.

---

### Post by Impavidus on 2018-05-15
Or, if you want to store your entire home directory on the big drive, simply mount the big drive as your /home partition and don't create any links.

---

