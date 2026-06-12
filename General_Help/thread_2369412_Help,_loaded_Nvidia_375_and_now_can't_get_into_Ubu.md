---
title: "Help, loaded Nvidia 375 and now can't get into Ubuntu!"
date: 2017-08-22
forum: General Help
---

### Post by Panawe on 2017-08-22
A little knowledge is a dangerous thing!
 
 
 A little while ago I loaded Ubuntu 16.04 onto a friend&#8217;s computer and despite a few teething problems it works okay (dual booting with Windows XP). However, there has always been a niggling problem with the graphics driver which I have this evening attempted to fix and now we can no longer boot into Ubuntu as when the password is entered it loops back to the password screen.
 
 
 Back when the machine was running okay I looked at the Nvidia driver and noticed it was version 304. As my own machine was running 375.66 I thought this driver a little outdated and deduced that the problem lay there. I went into terminal and:
 
 
     $ lshw -numeric -C display
 
 
 Which told me his graphics model is GeForce 7025.
 
 
 Went onto the Nvidia driver page looking for an appropriate driver but the series 700 series (for Linux 64-bit) only went down to GeForce 705.
 
 
 Here&#8217;s what I think I did next (got onto a web page I can no longer find and went into Terminal).
 
 
 Run sudo apt-get purge nvidia-*
 Run sudo add-apt-repository ppa:graphics-drivers/ppa and then sudo apt-get update.
 Run sudo apt-get install nvidia-375.
 
 
 Since when I can no longer get into the machine because it keeps looping back to the password login.
 
 
 I do recall looking at Additional Drivers page and seeing that the only Nvidia driver offered was 304.
 
 
 Any help welcome.

(The information below refers to my own computer, my friend's is an older model)

---

### Post by BenginM on 2017-08-22
if additional drivers is offering 304 for that card , then use it .. purge the -375 and install the nvidia-current from additional drivers which should be 304. when you get locked at the login display, switch to a VT "Virtual Console" by pressing Ctrl+Alt+F3 , then login with your friends user & passwd , then pruge the current nvidia driver ..

$ sudo apt purge nvidia-*
$ sudo ubuntu-drivers devices  .. this is the equivalent to Additional drivers .. then install 304
$ sudo apt-get install nvidia-304

I suppose you may need to stop the display manager (lightdm) or whichever is in use before you got about doin' the above , i think it's 
$ sudo service lightdm stop 

[URL="https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"]https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia


[/URL]

And yes , that PPA is official but it's for testin'..
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by again? on 2017-08-22
> **Panawe said:**
> 
Went onto the Nvidia driver page looking for an appropriate driver but the series 700 series (for Linux 64-bit) only went down to GeForce 705.
The card is a GeForce 7 Series not 700 series which is only supported up to the 304 driver.

---

### Post by cleaf on 2017-08-22
I copy the standard method from Nvidia:

1. Create a file at /etc/modprobe.d/blacklist-nouveau.conf with the following
contents:
blacklist nouveau
options nouveau modeset=0

2. Regenerate the kernel initramfs:
$ sudo update-initramfs -u

3. Turn off the lightdm
$ sudo /etc/init.d/lightdm stop

4. Install
$ sudo ./NVIDIA-Linux-x86_64-xxxx.run --no-opengl-files

If you have two gpu cards, and only one of them is product of Nvidia, the --no-opengl-files is necessary, or you can not login. 

5. Turn on the lightdm 
$ sudo /etc/init.d lightdm start

---

### Post by again? on 2017-08-23
> **cleaf said:**
> I copy the standard method from Nvidia:

1. Create a file at /etc/modprobe.d/blacklist-nouveau.conf with the following
contents:
blacklist nouveau
options nouveau modeset=0

2. Regenerate the kernel initramfs:
$ sudo update-initramfs -u

3. Turn off the lightdm
$ sudo /etc/init.d/lightdm stop

4. Install
$ sudo ./NVIDIA-Linux-x86_64-xxxx.run --no-opengl-files

If you have two gpu cards, and only one of them is product of Nvidia, the --no-opengl-files is necessary, or you can not login. 

5. Turn on the lightdm 
$ sudo /etc/init.d lightdm start
For someone who just stated "A little knowledge is a dangerous thing!" they're better off 
following BenginM's advice rather than trying to install a downloaded driver from nvidia.
The only problem here is he installed a driver that doesn't work with the gfx card.

---

### Post by Panawe on 2017-08-23
Thanks for replies, as always.

Once I can get back into Ubuntu I now realise I have to replace the Nvidia driver (as describied) but my immediate problem is getting back into my friend's account. We know the password but I'm not sure about the computer "name" as I think I may have been trying to log in as Guest using the password.

---

### Post by again? on 2017-08-23
The login name is the same as your home folder.
If you can't remember, boot to a live usb, mount your Ubuntu partition in the left pane of the file manager and look in the /home folder.
The username should also be listed in the /etc/passwd file in that same partition.
If you have forgotten password see [**HERE**]("http://psychocats.net/ubuntu/resetpassword").

Just to confirm the computer was running ok using the 304 nvidia drivers before you decided to try install a later driver?

---

### Post by Panawe on 2017-08-23
> Just to confirm the computer was running ok using the 304 nvidia drivers before you decided to try install a later driver?

Yes, except that the screen had hung when using a secure banking page on Firefox. It was this that prompted me to mess with the graphics driver or I would have left well alone.

---

### Post by mastablasta on 2017-08-24
1. boot into text mode - it is a bit more complicatedf with 16.04 since it has sytsemd (hurray): [http://ask.xmodulo.com/boot-into-command-line-ubuntu-debian.html](http://ask.xmodulo.com/boot-into-command-line-ubuntu-debian.html)
2. remove driver with commands posted by BenginM 

if you just remove them and reboot, you will boot into desktop with nouveau, if you reinstall it should boot into desktop.

screens can hung for various reasons. if they do it only on certian browsers then change the browser. firefox doens' trun well at all on some sites in one of my Kubutnu install. i moved to chromium there which works with no issues.
[[COLOR=#000000]BenginM[/COLOR]]("https://ubuntuforums.org/member.php?u=1100835")[COLOR=#000000] 

[/COLOR]

---

### Post by Panawe on 2017-08-25
Okay, done that. Kept getting into a loop at the login stage until I tried Ctrl+Alt+F3 when, after a bit of strangeness, I found myself at a command line same as Terminal and did as BenginM suggested. Sorted. Only...

Now get annoying requests to input password to unlock keyring (or something similar). I should add that I have set the computer to automatic login. There's stuff on the web about this but after the last experience I thought I'd come here first.

Should I start another thread as the video driver problem is solved?

Oh, and I changed the browser to Chromium but the problem with the secure banking page persists, other web pages seem unaffected.

I'll mark this as solved.

TIA

---

### Post by again? on 2017-08-25
Should be no issues to turn off autologin if your password works at a tty console(ctrl+alt+F3).
system settings > user accounts
unlock at top right then turn off automatic login.

If you changed your login password you may still get the 
password prompt after logging in but that can be fixed.

---

