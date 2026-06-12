---
title: "&quot;Eject&quot; USB HDD"
date: 2007-10-17
forum: General Help
---

### Post by sheck on 2007-10-17
I have WD Passport Portable 250Gb harddrive (USB) and I was getting errors when I was trying to eject it: it would unmount and then re-mount after 2 seconds back, also I would get "cannot eject" error on NTFS partiotion.

HOW I FIXED IT:

1. In NTFS Configuration tool (ntfs-3g) uncheck "Enable write support for external devices" (Applications -> System Tools -> NTFS Configuration Tool on my system)
2. add this line to FSTAB:
/dev/sdc2 /media/Storage_P ntfs-3g users,exec,suid,dev,dmask=000,fmask=111,locale=en_CA.UTF-8 0 1
(change device, mount point and locale as needed) (don't forget to create the mount point if it doesn't already exist)
3. Reboot

After a reboot I was able to eject my harddrive with no errors. The only issue I see with this, you have to continue changing or adding FSTAB entries for different devices.

I would like to see if this helps other people.

---

### Post by stefanuswiely on 2007-11-01
I use command line to eject my USB Harddrive, in my condition I have the Harddrive with 3 partion, so to eject it I use this command:
```

$ sudo umount /media/disk /media/disk-1 /media/disk-2

```

---

### Post by inversekinetix on 2007-11-01
I have problems with all usb drives.  It tells me to use the context menu and 'eject' the device but i cant see an 'eject' option anywhere so I just unmount it. if i unmount any external drive as soon as i pull the cable out it gives me an unsafe removal warning, even though it says its unmounted. Then it wont mount any other usb device, is this a normal thing in linux?

---

### Post by sheck on 2007-11-01
Unmounting does just that - unmounts
When you "eject" a USB device, especially a hard drive, System makes sure that device is unmounted and heads are in idle position, also that there is no data being written to the device.

To enable USB ejecting: open terminal and type - **sudo gedit /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi**
then edit all lines where it says **<merge key="storage.requires_eject" type="bool">false</merge>**. Change false to true. Reboot.

> 
Then it wont mount any other usb device, is this a normal thing in linux?


No, it's not normal. Mine doesn't do that. Even if I pull the cord without ejecting it, it gives me a warning, but mounts everything after that anyways. I'm not sure if the above will fix this problem.

---

### Post by Jittoku on 2007-11-01
> **sheck said:**
> 
To enable USB ejecting: open terminal and type - **sudo gedit /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi**
then edit all lines where it says **<merge key="storage.requires_eject" type="bool">false</merge>**. Change false to true. Reboot.

I tried this, and it unfortunately didn't work for me.  I'm using a Seagate 80 G USB HDD, but I've read lots of posts on this same problem with every drive under the sun.  I wonder, is this a problem with all the external USB HDDs?  

I want to try Sheck's thread-opening advice, but I have to learn a little more - don't quite follow that.  I don't have the NTFS config tool yet, and anyway, when I bought this drive, I changed the filesystem to ext3.  

I'm still on Feisty.  Can anyone say if the USB issue has been rectified in Gutsy?

---

### Post by Jittoku on 2007-11-01
Sorry for the double, but I have just succeeded in ejecting/unmounting my USB HDD from Gnome for the first time.  This fix was given by evilc on another thread:

sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak

---

### Post by sheck on 2007-11-02
> **Jittoku said:**
> I tried this, and it unfortunately didn't work for me.  I'm using a Seagate 80 G USB HDD, but I've read lots of posts on this same problem with every drive under the sun.  I wonder, is this a problem with all the external USB HDDs?  

I want to try Sheck's thread-opening advice, but I have to learn a little more - don't quite follow that.  I don't have the NTFS config tool yet, and anyway, when I bought this drive, I changed the filesystem to ext3.  

I'm still on Feisty.  Can anyone say if the USB issue has been rectified in Gutsy?

You don't have to have NTFS. For ext3 FSTAB line would look like this:

**/dev/device /media/mount_point ext3 users,exec,suid,dev,locale=en_ CA.UTF-8 0 1**

Reboot and you should be able to eject your drive, provided that you reverse the change that you made according to your last post.

Edit: you don't need NTFS Configuration tool for EXT3

---

### Post by dryder on 2007-11-20
I'm using five Seagate 80GB HD drives, one for each day of the week for backups. Their names include a space (FreeAgent Drive).

As I understand it each one would have a different UUID - and I agree with a lot of posts in the Ubuntu and other forums that moving to UUID is a backward and very confusing step.

And working out the UUID would be OK if, for example, a command line/configuration gui tool would calculate it for you! IMHO UUID is hardly a forward step in Ubuntu linux.

Surely, if commands like those above only used /dev/hc.. (or whatever - s,d a,b,c and so on) then each day I changed the drive it would be the same designation as the other four USB Seagate drives? If this is true, it would make life more simple.

So, my question is, what do I do if all five drives are NTFS and what do I do if I change them to ext3?

Comments and help (please explain the help :) ) greatly appreciated.

David

---

### Post by sheck on 2007-11-22
> **dryder said:**
> I'm using five Seagate 80GB HD drives, one for each day of the week for backups. Their names include a space (FreeAgent Drive).

As I understand it each one would have a different UUID - and I agree with a lot of posts in the Ubuntu and other forums that moving to UUID is a backward and very confusing step.

And working out the UUID would be OK if, for example, a command line/configuration gui tool would calculate it for you! IMHO UUID is hardly a forward step in Ubuntu linux.

Surely, if commands like those above only used /dev/hc.. (or whatever - s,d a,b,c and so on) then each day I changed the drive it would be the same designation as the other four USB Seagate drives? If this is true, it would make life more simple.

So, my question is, what do I do if all five drives are NTFS and what do I do if I change them to ext3?

Comments and help (please explain the help :) ) greatly appreciated.

David

Well, what is it that you are having a problem with ? NTFS and EXT3 will auto mount in Ubuntu when you plugin your drive(s). For read/write access on NTFS drives you need NTFS-3G package. That's all. 

Hal will calculate UUIDs for you automatically when you plugin the drive. I'm pretty sure you can see them in mtab.

---

### Post by dryder on 2007-11-22
Hmm, sorry mu post was not clear.
Yes, the drives are NTFS and I have the ntfs-3g packages installed on Feisty and it works fine on fixed disks.
.
I can mount each of the 5 Seagate 80GB HD drives but I can not eject them.> it would unmount and then re-mount after 2 seconds back, is what happens.> 1. In NTFS Configuration tool (ntfs-3g) uncheck "Enable write support for external devices" (Applications -> System Tools -> NTFS Configuration Tool on my system) and > 2. add this line to FSTAB:
/dev/sdc2 /media/Storage_P ntfs-3g users,exec,suid,dev,dmask=000,fmask=111,locale=en_ CA.UTF-8 0 1
(change device, mount point and locale as needed) (don't forget to create the mount point if it doesn't already exist) have no effect.

Also, as each drive has a different drive UUID (clicking on the drive icon>Properties>Volume) then as you say, > After a reboot I was able to eject my harddrive with no errors. The only issue I see with this, you have to continue changing or adding FSTAB entries for different devicesI would need 5 different entries in fstab. I might point out that only one of these drives is used per day.
But as it is always "/dev/sdj1"in fstab because only one is used per day  wouldn't fstab get confused by the same /dev/sdj1 five times with different "UUID=..." lines.

isn't using > sudo eject /media/*your-drivename*
in my case *sudo eject /media/"FreeAgent Drive"* easier?

Although my drive does not power down this way, it is simple to see that it is unmounted and doesn't change fstab.

Or am I completely misunderstanding your first post? (I am trying to learn, not be a nuisance)

---

### Post by sheck on 2007-11-28
> **dryder said:**
> Hmm, sorry mu post was not clear.
Yes, the drives are NTFS and I have the ntfs-3g packages installed on Feisty and it works fine on fixed disks.
.
I can mount each of the 5 Seagate 80GB HD drives but I can not eject them. is what happens. and  have no effect.

Also, as each drive has a different drive UUID (clicking on the drive icon>Properties>Volume) then as you say, I would need 5 different entries in fstab. I might point out that only one of these drives is used per day.
But as it is always "/dev/sdj1"in fstab because only one is used per day  wouldn't fstab get confused by the same /dev/sdj1 five times with different "UUID=..." lines.

isn't using 
in my case *sudo eject /media/"FreeAgent Drive"* easier?

Although my drive does not power down this way, it is simple to see that it is unmounted and doesn't change fstab.

Or am I completely misunderstanding your first post? (I am trying to learn, not be a nuisance)

As long as you have constant number of drives connected at the same time, you do not need to adjust fstab. No need to use UUIDs either.

Make sure that you have all the updates installed.

create a folder in /media then open fstab and add anywhere, on a new line:

**/dev/sdxx /media/x ext3 user,noatime,exec,dev 0 1** or use your own options

or

**/dev/sdx /media/x ntfs-3g user,noexec,nosuid,nodev,dmask=000,fmask=111,locale=en_CA.UTF-8 0 1**

*(don't forget to change device and mount point to what you have)*

after that unmount and remove the drive and then re-attach it. Let me know what happened.

Also if you want to spin down your drive, before unplugging it - install **sg3-utils**
then in terminal type:

```
**sudo sg-start --stop /dev/sdx**
``` that will spin the drive down

Sure, you can also use **sudo eject /media/x ** as well. Whatever works for you best. I use fstab, since I don't like typing too much every time.

---

### Post by mikewhatever on 2007-11-28
> **sheck said:**
> Unmounting does just that - unmounts
When you "eject" a USB device, especially a hard drive, System makes sure that device is unmounted and heads are in idle position, also that there is no data being written to the device.

To enable USB ejecting: open terminal and type - **sudo gedit /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi**
then edit all lines where it says **<merge key="storage.requires_eject" type="bool">false</merge>**. Change false to true. Reboot.


I don't seem to have the file to edit

> ls /usr/share/hal/fdi/policy/10osvendor
10-cpufreq.fdi
10-keyboard-policy.fdi
10-laptop-panel-mgmt-policy.fdi
10-macbook-backlight.fdi
10-macbookpro-utils.fdi
10-power-mgmt-policy.fdi
10-rfkill-switch.fdi
10-usbcsr-mice.fdi
15-storage-luks.fdi
20-storage-methods.fdi


---

### Post by Tang on 2007-12-23
> **Jittoku said:**
> Sorry for the double, but I have just succeeded in ejecting/unmounting my USB HDD from Gnome for the first time.  This fix was given by evilc on another thread:

sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak
Thank you for passing that command on. It enabled me to click the desktop icon and "eject" my USB Elements hard disk. formatted fat32, on amd64 running feisty i386. 

However,  amongst a lot of things I'm unsure of, I'm not sure if the drive has been unmounted, but not correctly parked. Can anyone help?

---

