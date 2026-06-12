---
title: "HELP - Laptop upgrading from 7.10 to 8.04"
date: 2008-05-20
forum: General Help
---

### Post by Bandarra on 2008-05-20
Hello, I'm realy gutted I messed up my pc and can't use it or get a 7.10 cd fast enough. As you may have noticed I upgraded my laptop (compaq presario x1010) from 7.10 to 8.04 but don't know if the upgrade was completed sucessfully or what I did wrong. Im going to make a list of important point te explain the problem better:
- just read now that I was supposed to do all the updates before upgrading (I didn't)
- the problem itself is that when the pc boots all is normal until the point where it is supposed to show the desktop but it doesn't (just shows the default color, and the mouse pointer)
- I think the problem must not be too hard to solve because it seems to be runing ok but it doesn't display anything other than the color and mouse
- I say this because I have a shortcut for the task manager and if I press it it comes up and shows as usual everything that is going on and everything seems fine, except that I cant see or click anything
- good news is, I think, from the task manager I can get access to a terminal and so if there is anything simple that I have to do to correct the problem (or get back to 7.10) I supposes you guys can tell me an I can type it in.

I think thats it but plz feel free to ask any relevant questions, I realy need my laptop working since its exams and assignments time and I realy have a lot of work to do :(

Thanks everyone

---

### Post by Bandarra on 2008-05-20
some one must know :(:confused:

---

### Post by tamoneya on 2008-05-20
first of all in terminal you can type:```
lsb_release -a
```This should tell you that you are in hardy and that you are fully upgraded.  Then the next thing you can do is type:```
sudo nano /etc/X11/xorg.conf
```We can take a look to make sure everything is configured correctly here.  Post the result here if possible  

The other thing that you could try doing is instead of booting normally you could hit "escape" when GRUB is loading and select the recovery option.  Here you will have just command line with root access.  You could uninstall and then reinstall the ubuntu-desktop package.  This should clear out any problems that have manifested themselves during the upgrade:```
apt-get remove --purge ubunt-desktop
apt-get install ubuntu-desktop
```

Also the forum rules say that you should wait 24 hours before bumping up a post.  We will get to it when we can.  Please be patient.

---

### Post by Bandarra on 2008-05-20
CODE]lsb_release -a[/CODE]
Replied
No LSB modules are available.
Distributor ID: Ubuntu
Descripiton:    Ubuntu 8.04
Release:        8.04
Codename:       hardy

```
sudo nano /etc/X11/xorg.conf
```
Here I dont know what to do so I did
sudo dpkg-reconfigure -phigh xserver-xorg
Replied:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080520213717

```
apt-get remove --purge ubunt-desktop
apt-get install ubuntu-desktop
```
Replied
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

I did this and after a lot of processing it gave an error. and exited. problem still the same

---

### Post by tamoneya on 2008-05-21
make sure you put sudo before dpkg --configure -a

---

### Post by Bandarra on 2008-05-21
```
sudo dpkg --configure -a
```

Replied after many operations:
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Errors were encountered while processing:
 ntfs-3g

---

### Post by Bandarra on 2008-05-21
I was wondering, is there a way through the console of reverting the system back to 7.10? (I think I would be happier with that rather than "fixing" the 8.04) or even if I get a 7.10 cd is there an option of reinstaling 7.10 without losing the documents that I have currently in the hard drive? something like a downgrade...
I was happy enough with the 7.10, didn't think the update to 8.04 would be this major...

---

### Post by tamoneya on 2008-05-21
there is no way to just downgrade.  Depending on how you have your partitions set up you can do a reinstall without losing your documents.  You need to have a separate /home partition if you want to do this and that isnt done by default so I am guessing that you havent done this.  You could however pop in the 7.10 liveCD.  Then copy your files off of the harddrive to some external drive/server.  Then install and replace your files from backups.

---

### Post by Bandarra on 2008-05-21
Thanks, I think that's what I'll do when/if I get a live cd. Meanwhile can you think of any other way to fix the 8.04? I even have internet now. From the system monitor i can get konkeror, from there I can get a firefox page and a terminal... firefox didn't get any internet because I use wireless but now I pluged the cable in and even have that.

---

### Post by tamoneya on 2008-05-21
well we need to resolve the ntfs-3g problem.  Are you using any ntfs (windows) partitions for anything. Post the output of ```
sudo fdisk -l
```That is a lowercase "L"

---

### Post by Bandarra on 2008-05-21
```
sudo fdisk -l
```

Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4683    37616166   83  Linux
/dev/sda2            4684        4870     1502077+   5  Extended
/dev/sda5            4684        4870     1502046   82  Linux swap / Solaris

No, I don't have any ntfs partition in my hard disk, only on my external usb connected disk that I use for documents storage, so I think it has nothing to do with it

---

### Post by Bandarra on 2008-05-21
Something completely beyond my understanding just happened.

A friend came to give me a 7.10 live cd.

Rebooted the pc with the cd in the drive. Optical drive is the primary boot device. Started to open the cd, orange bar moving back and forward, then went  on to the hard drive boot instantly, (filling bar) and everything loaded perfectly and my pc is back to its original state.

Really don't have a clue of how this happened. on the notification area it says 400+ updates to do so I'm doing them before risking a reboot and coming back to the original state.

Any thoughts? :confused:

---

### Post by Bandarra on 2008-05-22
I'm going to tag this post now as SOLVED because everything is back to normal even tough I have absolutely no idea of how that happened.

---

