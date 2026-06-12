---
title: "System down, Royally messed up!"
date: 2007-10-11
forum: General Help
---

### Post by soumo on 2007-10-11
Hi folks,
I could really use some help about now.

I have a Vista/Ubuntu dual boot in which the Vista has somehow got converted into a logical partition instead of bootable one.  THAT however is NOT the main problem.

I managed to erase my 6GB Lenovo service partition and install Ubuntu into a 5GB partition with a 1GB swap partition.  For a week I've been customizing and tweaking getting everything up and running.  I was able to access the Vista partition and copy mostly what I needed.  

The problem:
Trying to install my scanner, I started installing SANE or XSANE -not sure which.  While going through the myriad dependencies, I noticed a bunch of them would not 'update' by installing the debian packages, notably libgtk and libgimp (the message was something to the effect that the ones on the system were not up to date).

So failing to upgrade them via those packages, I thought to use Synaptic Manager to uninstall libgimp (*I think*, it may also have been libgtk).  After marking it and confirming, I didn't realize it would uninstall a whole lot of dependencies such as gnome and about 2GBs of other system files and programs!  

Immediately I noticed I was not able to access the Beryl settings manager (though Beryl worked fine), and that many at the top taskbar menu items were gone!

After rebooting, I was unable to access the GUI and was asked to log in by text.  This was fine, my password intact, and sent me to an old dos like system or terminal...?  I have been able to use recovery from the boot menu, but it brings me to the same login.

I am currently using the live CD and can access the files in both Vista and Ubuntu, but I really need to get both up and and running.

Where to start?  Any leads are greatly appreciated and the following thread looks like it may be of some use?
[http://ubuntuforums.org/showthread.php?t=573139](http://ubuntuforums.org/showthread.php?t=573139)

Thanks.

---

### Post by nzadLithium on 2007-10-11
try running

sudo apt-get install ubuntu-desktop

might get everything back but not sure.

Or if you can get into synaptic jsut install it using that

---

### Post by om1 on 2007-10-11
ok first try this....
boot back up and login and run this command
```
sudo apt-get install ubuntu-desktop
```
reboot if it doesnt give you a gui....
if that dont work post back with your error if you get one
ps write down the command bc you have to type it completely right or it will not work

---

### Post by Shazaam on 2007-10-11
See if this gets you to the desktop. Try to boot into recovery mode, go ahead and log in.
At the prompt type in 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Enter your password.
Type in reboot.
Try to log in normally.

---

### Post by nzadLithium on 2007-10-12
i think vista is meant to be a logical partition

unless you installed grub on your vista partition?

you probably installed grub on your linux patition so the linux partition should be bootable and the vista partition not. (i think) it could be the other way around though.

does vista not show up in the grub o/s list?

---

### Post by soumo on 2007-10-12
Thanks a lot for your quick responses!

When I tried this:
>sudo apt-get install ubuntu-desktop

I got:
The following packages have unmet dependencies : Depends: xsane 
but it is not going to be installed E: broken packages

When I tried this:
>sudo dpkg-reconfigure -phigh xserver-xorg

On the blue screen that followed, it asked me to choose my video driver,
I chose 'nv' for NVIDIA and left the resolutions as is (low)

I got:
xserver-xorg postinst warning: overwriting possibly customised configuration file; backup in /etc/x11/xorg.conf.20071011233452

On reboot I get the same command line prompt login again.

Any clues?

---

### Post by Shazaam on 2007-10-12
Ok, lets try a manual setup, at the prompt input
```
sudo dpkg-reconfigure xserver-xorg
```
and answer the questions (most are ok as default if you don't know).

Also, every thing went well (except for xsane) with installing ubuntu-desktop?

---

### Post by soumo on 2007-10-12
Thanks again!

I followed the manual setup instructions with no modification, except changing the keyboard to 104 from 105, and unsure which setting was the usb mouse I left it as default.  The rest of the defaults seemed okay.

However on reboot, same thing :(

I did notice a few messages:
Just before it asks for my command line login, I see,

Kinit : no resume image.  Doing normal boot
warning: something created compreg.dat!
Your system was affected by this bug: [https://launchpad.net/bugs/30791](https://launchpad.net/bugs/30791)
compreg.dat has now been removed again, which should fix the symptoms.

I decided to try to install Firefox to try and restore some of the libraries I'd deleted, On reboot same thing...I'm actually no longer certain if the bug mentioned was before or after Firefox, but the kinit bug was there before.

Another thing that was there before was a red 'Fail' flag beside a non-existing mount point in my fstab file.  (This was a manual edit I did to mount my NTFS system automatically.)  

Finally there was a problem with my bcm43xx-fwcutter (but this has been there a while):
Basically I had to install my wireless card manually using the ndiswrapper method, but before that I tried using some method requiring apsta.o which was unavailable.  I did get the wireless working, but the error persisted though it didn't really affect my installs.  It just gave an annoying reminder after each install (via apt-get or synaptic). 

Thanks again, I really appreciate all your help.  I am calling it a night for now, but look forward to your response in the morning :D

---

### Post by nzadLithium on 2007-10-12
Perhaps it would be easier to just install ubuntu again?

---

### Post by soumo on 2007-10-12
I'm afraid it's beginning to look that way!

I wonder if I can just drag 'n drop from the live cd file system into the folders on my hard disk to sort of replace any necessary files?  Any thoughts?

---

### Post by nzadLithium on 2007-10-12
I dont think that is possible. It shouldn't take too long to run the installer anyway. On my other pc running a celeron 2.5ghz it took about 20 minutes to get feisty on it i think.

---

### Post by soumo on 2007-10-14
Thanks again.

yeah it's fast, I guess I just didn't want to have to go save all my data and set it all up again...oh well.

I didn't see the post about Vista before....

It is actually a primary partition and bootable, but I tried to resize it using gparted and qtparted and accidentally erased the mbr or mft -not sure which.  Then I used testdisk to recover it, but it only shows up as a logical partition!  I cannot boot from the GRUB.

---

### Post by nzadLithium on 2007-10-14
unless you have two hard disks then the mbr should be fine if it is booting ubuntu. And i think (but im not sure) that you have to have a boot loader to boot linux. goto computer then file system then boot. chances are that if you have a grub folder there then it is booting using grub. I think you just need to find out what lines to add to the grub config to get it to show vista. There is probably a tutorial somewhere on how to do (i dont know what u need to add for vista as i dont have it) although i dont know why grub didnt auto detect. Maybe its coz u need to update grub or something?

---

### Post by soumo on 2007-10-14
I'm sure I've seen that folder somewhere.

I'll go do some reading now...

Thanks again!

---

