---
title: "Trying to setup eSata or internet hard drives for auto mounting when System turned on"
date: 2014-10-09
forum: General Help
---

### Post by Christopher_Miller on 2014-10-09
I have been trying to attempt auto mounting hard drives on 2 different systems.  First on one PC I have an eSata drive setup and every time I restart I have to access the drive to mount it, I am looking to have it already mounted when I start up.  the 2nd PC has 2 internal hard drives and I have the same problem when I start up I need to access them to mount them.  I have searched the web and can not find anything that will help.  In Ubuntu disks app I tell it auto mount on either PC.  After which I will get a message when I try to access the drive and when I reboot there is an error during the start up were it stops and ask to skip the mount to continue.  

I am a new convert from the windows world were windows does a lot of the job when it comes to hard drives meaning once you format the drive it is mounted and will continue to mount on each reboot.  

Please Help!

---

### Post by nerdtron on 2014-10-09
Is this eSata drive an NTFS drive? Is it permanently connected?
You can try adding an fstab entry for it.
First, determine the UUID of the drive. Connect it and run:
```
sudo blkid
```

Create a folder for the mount point:
```
sudo mkdir /media/eSata/
```

Once you know the UUID of the drive, add an fsab entry (assuming ntfs drive):
```
gksudo gedit /etc/fstab
```
You'll be asked for your password and open gedit as root.
Add the following line to the file. Replace the UUID by the UUID your drive.
```
UUID=df156fca-2e39-431c-8c3f-1f02090c83d2 /media/eSata                  ntfs    defaults        0 0


```

Try to reboot and see if it is auto-mounted.

---

### Post by Christopher_Miller on 2014-10-11
Sorry for the delay in replying but I have been way to busy the last few days . . . . .

So I performed the steps you stated and _***[COLOR=#ff0000]it did not work[/COLOR]***_.  

When I do a sudo mount -a  I get  "mount: special device uuid=c61bdc81-c58e-4f3b-be48-85b3c07b81d0 does not exist"

When I restart the PC I get this "Error occurred while mounting /media/esata, Press S to skip mounting or M for manual recovery"

Here is the results of the sudo blkid
/dev/sda1: UUID="87e07cf3-2bc0-47ff-977e-b724c76694fc" TYPE="ext4" PARTUUID="22e76082-01" 
/dev/sda5: UUID="de22769e-9779-400e-a2f2-d065cd4287f1" TYPE="swap" PARTUUID="22e76082-05" 
/dev/sdb1: LABEL="Data" UUID="c61bdc81-c58e-4f3b-be48-85b3c07b81d0" TYPE="ext4" PARTUUID="f4e8e053-01"

This is the FSTAB command I added
uuid=c61bdc81-c58e-4f3b-be48-85b3c07b81d0 /media/esata  ext4  defaults  0 0

---

### Post by oldfred on 2014-10-11
Did you create a mount point for /media/esata?
Your default mount with Nautilus would be /media/$USER/Data since you have labled it.
Where this should be you.
echo $USER

And if ext4, you need to give yourself ownership & permissions:

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)

   [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)


Note that -R is recursion & everything is changed, never run on a system partition or accidentally leave a space after a / in mount point as that changing entire system. Only way to fix it then is a re install. But ok on just your data partition(s).

 sudo chmod -R a+rwX /media/esata       
        
 sudo chown -R $USER:$USER /media/esata

---

### Post by Christopher_Miller on 2014-10-11
I was able to resolve my issue on the one PC.  I was trying things and I changed the format to NTFS and after** oldfred** gave me a few links that I had not seen one clicked for me and alteredn my fstab to add this:

LABEL=Data /home/eyarea51/Data ntfs defauts 0 0

and know I need to apply this to my other PC witht he internal hard drives.

---

### Post by oldfred on 2014-10-11
Glad you figured it out.

Few use the label as a mount, and I think we should suggest that more. While UUIDs rarely get changed using labels is also a good way as long as the user does not label two partitions the same.

---

