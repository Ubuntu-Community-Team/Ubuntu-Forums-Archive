---
title: "X will not start"
date: 2007-11-03
forum: General Help
---

### Post by emid on 2007-11-03
I know there are other similar threads out there, but they haven't solved my problem.  Whenever I reboot, X fails to start.  If I reinstall the Nvidia driver I can then restart gdm and everything works fine.  The next time I reboot the same thing happens all over again.  I recently upgraded to Gutsy, but I've been having this problem for a while using Feisty.

I'm running the AMD64 version with a Nvidia 7600GT.  Any help would be appreciated.

Also, I feel that this problem may have started a while ago after a kernel update.  I could be wrong though.

---

### Post by Pumalite on 2007-11-03
What's the output of:
uname -a

---

### Post by erginemr on 2007-11-03
I had a similar issue under Feisty. I have GeForce MX400, and had installed the NVIDIA driver installer from thier site. The first time it started the session, everything seemed OK, but my X was gone after a reboot with such a complaint from the system: 
"Your NVIDIA kernel is 1.78 blah blah, but it should have been 1.98 blah blah. Check that you are using the same versions for both the kernel and the driver."

And if my memory serves me correctly, the problem arose after a kernel update through synaptic.

So, my question is, how did you install the NVIDIA driver?

---

### Post by Pumalite on 2007-11-03
I'm sure it was from Nvidia through a virtual terminal.

---

### Post by emid on 2007-11-03
my output for uname -a is:
```

Linux d-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

```

I installed the Nvidia driver through their website, from the terminal indeed.

---

### Post by Pumalite on 2007-11-03
Which driver did you install?

---

### Post by emid on 2007-11-03
I had installed 

NVIDIA-Linux-x86_64-100.14.11

and more recently:

NVIDIA-Linux-x86_64-100.14.19

---

### Post by Pumalite on 2007-11-03
The process requires:
1.-Accept the license
2.-Allow driver to remove old drivers and compile the module
3.-Let the driver reconfigure your xorg.conf
4.-sudo /etc/init.d/gdm start

Did you follow all that?

---

### Post by erginemr on 2007-11-03
> **emid said:**
> I had installed 

NVIDIA-Linux-x86_64-100.14.11

and more recently:

NVIDIA-Linux-x86_64-100.14.19

I am sure pumalite will more experienced than me and will propose a more professional solution, but IMHO, you should uninstall the latest NVIDIA driver by running the same installer file but using an "-uninstall" switch / argument at the end of install script.

This way, you will get rid of the existing package and kernel part. Then, you will need to re-install the same, causing the installer to re-create the NVIDIA kernel module, but this time, according to your new kernel.

For this to work, you also should have installed xorg-dev package before. But I recommend waiting for pumalite's suggestion first.

---

### Post by emid on 2007-11-03
> **Pumalite said:**
> The process requires:
1.-Accept the license
2.-Allow driver to remove old drivers and compile the module
3.-Let the driver reconfigure your xorg.conf
4.-sudo /etc/init.d/gdm start

Did you follow all that?

Yeah, I did that.  My issue is that every time I reboot I have to do that exact process over again.  Once I finish it starts the gui session with compiz working perfectly.

---

### Post by Pumalite on 2007-11-03
The driver removes old drivers automatically if one follows the procedure correctly in all it's steps.

---

### Post by emid on 2007-11-03
I suppose so.  Every reboot gets me kicked to the terminal unable to start gdm until I reinstall the driver.  I almost forgot about this problem since I hadn't rebooted in a while.  But after I upgraded from Feisty I realized it still existed.

---

### Post by emid on 2007-11-03
> **erginemr said:**
> I am sure pumalite will more experienced than me and will propose a more professional solution, but IMHO, you should uninstall the latest NVIDIA driver by running the same installer file but using an "-uninstall" switch / argument at the end of install script.

This way, you will get rid of the existing package and kernel part. Then, you will need to re-install the same, causing the installer to re-create the NVIDIA kernel module, but this time, according to your new kernel.

For this to work, you also should have installed xorg-dev package before. But I recommend waiting for pumalite's suggestion first.

I uninstalled and then reinstalled the driver and still have the same problem.

---

### Post by erginemr on 2007-11-04
> **emid said:**
> I uninstalled and then reinstalled the driver and still have the same problem.

I am sorry to hear that. I couldn't solve that problem either at that time, I ended up uninstalling Feisty and returning to Edgy until the release of Gutsy.

One temporary solution to your problem (that will bring back the desktop but without Compiz and other 3D effects of the binary NVidia driver), is to manually edit the "/etc/X11/xorg.conf" file and replace the line:
Driver "nvidia"
with
Driver "nv"

This way, you can at least have a consistent access to your Gnome desktop.

I would also try as a final resort to first disble Compiz (desktop effects), stop the gdm from a virtual terminal (say Ctrl+Alt+F1) with the command:
"sudo /etc/init.d/gdm stop"

uninstall the NVidia driver from the command line again with the -uninstall switch, but not reinstall it this time, change the xorg.conf file as above, then reboot the computer,

It should normally show up the graphical screen (gnome desktop, I mean). Then, everything should return back to the initial stage, as if you had never installed NVidia binary driver.

At this stage, you may try installing "nvidia-glx-new" from Synaptic. The package from synaptic will conform to your current kernel. Hopefully, this will rectify the kernel incompatibilities. 

Please try this and let's hope that it will work. After all, you have nothing to lose.

---

### Post by erginemr on 2007-11-04
In the meantime, you may also scan the following page, to see if it says anything about your (and my former) problem and its solution:
[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

(I'll read it, too.)

---

### Post by emid on 2007-11-04
I will give those suggestions a try and post back with my results.  Thanks for the help.

---

### Post by emid on 2007-11-05
> **erginemr said:**
> I am sorry to hear that. I couldn't solve that problem either at that time, I ended up uninstalling Feisty and returning to Edgy until the release of Gutsy.

One temporary solution to your problem (that will bring back the desktop but without Compiz and other 3D effects of the binary NVidia driver), is to manually edit the "/etc/X11/xorg.conf" file and replace the line:
Driver "nvidia"
with
Driver "nv"

This way, you can at least have a consistent access to your Gnome desktop.

I would also try as a final resort to first disble Compiz (desktop effects), stop the gdm from a virtual terminal (say Ctrl+Alt+F1) with the command:
"sudo /etc/init.d/gdm stop"

uninstall the NVidia driver from the command line again with the -uninstall switch, but not reinstall it this time, change the xorg.conf file as above, then reboot the computer,

It should normally show up the graphical screen (gnome desktop, I mean). Then, everything should return back to the initial stage, as if you had never installed NVidia binary driver.

At this stage, you may try installing "nvidia-glx-new" from Synaptic. The package from synaptic will conform to your current kernel. Hopefully, this will rectify the kernel incompatibilities. 

Please try this and let's hope that it will work. After all, you have nothing to lose.

I just tried it and unfortunately it didn't work.  After I installed the nvidia-glx-new and rebooted it was back to the same thing.  I guess it isn't the worst bug because I don't reboot that often.  It still is pretty annoying though.

---

### Post by erginemr on 2007-11-05
After surfing the net for an answer to our mutual problem, I think I have found a solution.

I have collected the avaliable threads and solution candidates from several sites and attached the result. Please read the attached file (in txt and pdf), they basically describe the kernel version incompatibility and a resulting failure to boot the graphical desktop.

I will try to make something out of these because there are many common suggestions in different posts for a solution. 

More later...

---

### Post by erginemr on 2007-11-05
Sorry, I cannot upload the pdf version due to its size. I hope the text version is legible...

---

### Post by erginemr on 2007-11-05
OK. Here is the deal:

[My comment --> First of all backup your xorg.conf file to be re-used in case things go bad: sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak

--> Start and stop Gnome desktop with sudo /etc/init.d/gdm start (or stop) from another terminal Ctrl + Alt + F1-6

--> Uninstall the binary driver with &#8220;sudo NVIDIA*.sh -- uninstall&#8221;. Note that there is a double dash before the uninstall argument. In general, the convention is to put -- before long commands, - before short ones, such as to get help on any command: - h or -- help

--> Then follow either POST-1 or POST-2, yet they basically they describe the same thing.]

POST-1:

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that  ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx (or nvidia-glx-new) package has been uninstalled with the --purge option and the files 
      /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

[My comment --> Either remove them as advised above with &#8220;sudo rm /etc/init.d/nvidia*&#8221; or better, move them under a new directory for backup with: &#8220;sudo mkdir /etc/init.d/nv-old; sudo mv /etc/init.d/nvidia* nv-old&#8221;]

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. 

Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via: DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists: /lib/linux-restricted-modules/.nvidia_new_installed

Re-install NVIDIA package with the NVIDIA installer (NVIDIA*.sh).

[My comment --> You may need to run: "sudo nvidia-xconfig" to properly configure xorg.conf file.]

POST-2:

For the the compiled version of the newest NVIDIA official drivers to work:

1) make sure you have build-essential installed: 
     sudo aptitude install build-essential

2) make sure you have the linux-headers package matching the installed Linux kernel is installed:
     sudo aptitude install linux-headers-$(uname -r)

3) make sure that the pkg-config and xserver-xorg-dev packages are installed
     sudo aptitude install pkg-config xserver-xorg-dev

4) if the nvidia-glx/nvidia-glx-new package has been installed, uninstall it with the --purge option
and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist (delete them manually)

sudo aptitude remove --purge nvidia-glx or 
sudo aptitude remove --purge nvidia-glx-new
sudo rm -fvr /etc/init.d/nvidia*

5) make sure that the linux-restricted-modules or linux-restricted-modules-common packages
have been uninstalled.
sudo aptitude remove linux-restricted-modules*

[My comment --> I believe this is not necessary, because we can disable it with: Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via: DISABLED_MODULES="nv nvidia_new"]

6) run the NVIDIA installer you downloaded from NVIDIA and follow the wizard until its done.

NOTE: doing sudo rm -fvr /etc/init.d/nvidia* just might do the trick. I compiled the driver w/o
removing those files and i got conflicts. If someone could confirm this it would be great.

Cheers!!!

[My comment --> Cross your fingers and pray. Good Luck!]

---

### Post by erginemr on 2007-11-06
Any progress?

---

### Post by emid on 2007-11-06
Unfortunately no.  This really seems like it would be the answer, but when I tried it I ended up with the same problem.

In the /etc/init.d/ directory I only had the "nvidia-kernel" script to erase, the other one didn't exist on my system.  I'm really not sure if that means my issue is different or not.

I am looking over the instructions again to make sure I didn't mess anything up, even though I'm 99% sure I did it properly.

---

