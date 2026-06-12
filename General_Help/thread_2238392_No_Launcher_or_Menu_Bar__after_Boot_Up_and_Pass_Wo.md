---
title: "No Launcher or Menu Bar  after Boot Up and Pass Word"
date: 2014-08-07
forum: General Help
---

### Post by SpikeLS6 on 2014-08-07
My last 14.04 Update put 3.11.0-20-generic on the Grub Loader. I noticed that all the other previous -generic's are gone; I did not remove them as I usually do. The Desktop comes up, but no launcher (Unity?) or the top Menu Bar to  be able to Shut Down. The only way I can shut down is to Reset and when it comes up  to the Pass Word Screen, click on the Shut Down Symbol there. At the Desktop, the mouse can be moved around, but I can not get into Terminal with any keyboard short cuts, so the keyboard seems to be ineffective.

I have tried going into Ubuntu Recovery Mode for a normal boo to no avail, then clicked on 1) fsck, Check all File Systems, and 2) failsafex, run in failsafe graphic mode. #2) did not have a mouse and there was no keyboard control. I had to use the reset button to shut down when the Pass Word Screen came  up.

My laptop is updated and is running 3.13.0-32-generic. Did some files not get installed on the on the Desktop's last update? How do I get my launcher and menu bar back?

---

### Post by Jesse_Campton on 2014-08-07
Please look here and see if this will fix your problem.. [http://askubuntu.com/questions/449845/problems-after-upgrading-to-14-04-only-background-and-pointer-after-login](http://askubuntu.com/questions/449845/problems-after-upgrading-to-14-04-only-background-and-pointer-after-login) (try ctrl+alt+F1 for terminal).

This looks like your problem here: ```
sudo [FONT=Ubuntu Mono]apt-get install --reinstall ubuntu-desktop[/FONT]
``` ```
sudo [FONT=Ubuntu Mono]apt-get install unity[/FONT]
```

---

### Post by SpikeLS6 on 2014-08-07
That looks good, but how do I get to Terminal to enter these instructions?

---

### Post by Jesse_Campton on 2014-08-07
Boot into your Desktop and try: Hold Down CTRL+ALT then push F1. That should take you to a terminal which you must then login. Type your username first then it will ask you for your password (password will not display). After doing the commands, simply type ```
sudo reboot
```

---

### Post by SpikeLS6 on 2014-08-07
Got  into Terminal with commands you suggested (also found in Recovery "Root" would work). The reinstall Desktop went through quite a fewlines of code and ended back at the root prompt,  and the install Unity did the same. I reboot normally, but still no launcher  or menu bar.

I tried "sudo apt-get update && sudo apt-get upgrade" and "sudo apt-get update && sudo apt-get dist-upgrade" but get errors such as "Failed to fetch cdrom://Ubuntu 13.10 -Saucy Salamander_ - Release amd64 (2013 1016.1)/dists/saucy/restricted/binary-amd64/Packages  Please use apt-cdrom to makethis CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs", another but with ".../dists/saucy/main/binary-i386/Packages ...", and a third with "... /dists/saucy/restricted/binary-i386/Packages ...". Plus "Some index files failed to download. They have been ignored, or old ones used instead."

I have also seen errors that say "... unable to write to /var/cache/apt, too.

It seems as though some of the repositories are not loading to get all the software.

---

### Post by Jesse_Campton on 2014-08-07
Was this a fresh install of 14.04 or did you dist-upgrade from 13.10?

---

### Post by SpikeLS6 on 2014-08-07
I used the software upgrade "14.04 Available" from  the automatic update screen.

---

### Post by Jesse_Campton on 2014-08-07
It seems there are a lot of people having this issue upgrading from 13.10 to 14.04 through the upgrade feature. Is a fresh install of 14.04 possible? I see quite a few people posting problems although I am not seeing a fix as of yet.. but I will keep looking.

---

### Post by SpikeLS6 on 2014-08-07
I thought about a fresh install if the problem was wide spread. What would be the best way to do a fresh install? Just go to the Ubuntu site  and Download 14.04? I can do that  tomorrow morning.

---

### Post by Jesse_Campton on 2014-08-07
Yes, download Ubuntu and either make a disc or USB installer.

---

### Post by SpikeLS6 on 2014-08-08
I made the USB an installer media, but had problems getting ubuntu 14.04 installed. It kept  balking and offering up error screens that my hard drive could not be written to and i should clean it, or other indicators pointing to the hard drive. It is only six months old. So, rather than being frustrated the entire weekend I ran it down to the repair shop this morning to have them diagnose the problem. Wheather they find a problem with the old one that isfixable or install a new one, they will put a fresh install of Ubuntu 14.04 on the hard drive and I  will spend next week dealing with the backed  up files and re-installing  the software I use every day.

Thank you for your help with the Unity and Desktop problems, but it may be that a faulty hard drive prevented a correction.

I will go back and report  this thread as [SOLVED].

---

