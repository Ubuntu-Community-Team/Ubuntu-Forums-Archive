---
title: "No Nvidia-settings"
date: 2007-10-22
forum: General Help
---

### Post by geovino on 2007-10-22
Since I upgraded to 7.10 I have not been able to install my Nvidia drivers. I'm sure I'm not the only one.

I go to Applications > Sysytem Tools > Nvidia Settings I get this message:

Failed to execute child process "/usr/bin/nvidia-settings" (No such file or directory)

When I try to install the Restricted Drivers I get this message:

E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb: subprocess pre-installation script returned error exit status 2

How can I solve this problem?

---

### Post by UK-Wobbie on 2007-10-22
> **geovino said:**
> Since I upgraded to 7.10 I have not been able to install my Nvidia drivers. I'm sure I'm not the only one.

I go to Applications > Sysytem Tools > Nvidia Settings I get this message:

Failed to execute child process "/usr/bin/nvidia-settings" (No such file or directory)

When I try to install the Restricted Drivers I get this message:

E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb: subprocess pre-installation script returned error exit status 2

How can I solve this problem?

Have a go going to "Synaptic Package Manager" And see if you got any broken packages..
If you have not! You can put in "nvidia-glx-new" In the search box.. That will look up your nvidia-glx-new plugging.. Then right click on it and go to make for "reinstallation".. That will restill it!
If that do not work go to make for "Complete removal" That will Unstill the plugins.. Then reinstill it! Then when that is all done restart your computer and hit
 "CTRL-ALT- And your delete back key on your keybored!" That will reboot the X sever.. Then login and test your "Restricted Drivers Manager" To see if your drive shows up!
Click on your drive and instill it...The only thing is! It will instill the old nvidia plugins so you have to go to "Synaptic Package Manager" And instill the "nvidia-glx-new" plugins and then restart the pc and at the login screen hit  "CTRL-ALT- And your delete back key on your keybored!" to restart the X server..Then login and your done!

I hope that will help you. :)

---

### Post by geovino on 2007-10-22
I tried your first option and the drivers weren't installed at all. So I tried to install and I got the same message as before:

E: /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb: subprocess pre-installation script returned error exit status 2

Why? Since I can't install the drivers at all I doubt if I can do the second option you mentioned because there's nothing to uninstall.

What to do?

---

### Post by geovino on 2007-10-22
After running Synaptic I get a message that Software package is broken and to run this command;

davek@davek-desktop:~$ sudo apt-get install -f
[sudo] password for davek:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  nvidia-glx-new
Suggested packages:
  nvidia-settings nvidia-new-kernel-source
The following NEW packages will be installed:
  nvidia-glx-new
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/5014kB of archives.
After unpacking 15.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 171912 files and directories currently installed.)
Unpacking nvidia-glx-new (from .../nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb) ...
dpkg-divert: `diversion of /usr/X11R6/lib/libGL.so.1 to /usr/X11R6/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new' clashes with `diversion of /usr/X11R6/lib/libGL.so.1 to /usr/X11R6/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_100.14.19+2.6.22.4-14.9_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
davek@davek-desktop:~$ 




Well I completely uninstalled the nvidia-glx-new and now I get this error:


E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9639+2.6.22.4-14.9_i386.deb: subprocess pre-installation script returned error exit status 2

Do I have to do a clean install of 7.10 to get this to work?

---

### Post by airjaw on 2007-11-01
I have the same problem, and have been searching the forums for a fix.
Doesn't seem to be one yet...

---

### Post by dcstar on 2007-11-02
> **airjaw said:**
> I have the same problem, and have been searching the forums for a fix.
Doesn't seem to be one yet...

If you have Broken Packages, then you go into Synaptic and use the built in function to fix them.

If you install anything but the old nvidia-legacy drivers, then the nvidia-settings function is built into the newer drivers and can be accessed by running that command manually (or create a launcher with it).

---

### Post by Anthrax9 on 2007-11-02
Try Using [Envy]("http://albertomilone.com/nvidia_scripts1.html")
it searches your machine for a video card and installs the necessary drivers and packages
first clean out anything left from old installs using the sudo nvidia-installer --uninstall
this would be the best bet

---

### Post by geovino on 2007-11-02
I decided to so a clean install of Gutsy. Specials effects are working, and Gutsy runs faster than Feisty. 

[Problem Solved]

---

