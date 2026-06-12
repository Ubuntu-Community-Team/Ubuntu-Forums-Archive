---
title: "Ubuntu 12.04.01 not starting becouse of full memory."
date: 2013-07-15
forum: General Help
---

### Post by bambara on 2013-07-15
I filled my computer's Memory completely and after shutting it down I can't start it again. When I try to start the Computer I get this:                The system is running in  low-graphics  mode. Your screen, graphics card, and imput device Settings could not be detected correctly. You will Need to configure it your self. 

 I am unable to use the 4 options following the prompt given above:


 1. Run in low-graphics mode for just one session.
 2. Reconfigure graphics.
 3. Troubleshoot the error.
 4. Exit to console Login.

---

### Post by maestrobwh1 on 2013-07-15
Is this a live CD / USB, or is this your actual install?  If live CD / USB, choose boot options and check "nomodeset"  That should get you into X.  if not, reboot, check that off again, then you can also just move up (tab?) to the boot line and also add "xforcevesa" without the quotes of course.

If it is a HDD install, then I don't know why this would happen on later versions of X UNLESS you have proprietary graphics drivers installed and they upgraded right before this botched boot.  If you do, then you probably have an xorg.conf file in /etc/X11/ which we might have to look at later.  Boot into recovery mode but hit "e" and edit the kernel line and add "nomodeset xforcevesa" without the quotes, let it boot to the blue options screen, drop to a root shell, then 

for good measure (I am thinking when your machine crashed, it left the filesystem in an unclean state and your drive is being mounted as read only.  If there is an option to fsck your root drive (it has been a while since I have had to do this), try that but it might refuse because it is mounted.  

```

mount -a
mount -o remount,rw /
touch /forcefsck
```

This just makes sure you can write to your disk now and will force fsck on next boot
type:

```
exit
```

this brings you back to your options, and choose the one that allows you to continue the boot process.  See if this takes you to the login.  It might be the wrong resolution.  At any rate, choose to reboot here.  Let fsck do its thing and see if you get into a login screen.  If so, great.

If not, and you have an ati or nvidia card with proprietary graphics, repeat the above minus the "touch /forcefsck"

then:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nano /etc/X11/xorg.conf
```

you can use arrows to move the cursor around
ctrl+k and delete all lines except where you see

```
Section "Device"
    Identifier             "something"
    Driver                 "something" 
EndSection
```

arrow over and backspace over whatever is in the Identifier field and replace it with "default"
do the same for driver and change it to "vesa" "radeon" or "nvidia" to load the open source drivers.  Vesa is the safest BUT your resolution will be limited.

so it looks like this

```
Section "Device"
    Identifier             "default"
    Driver                 "vesa" 
EndSection
```

Ctrl+x will exit (answer yes to save).

Reboot and hope for the best as far as at getting into your desktop. If you used "vesa," the resolution will be at 1024x768.

---

