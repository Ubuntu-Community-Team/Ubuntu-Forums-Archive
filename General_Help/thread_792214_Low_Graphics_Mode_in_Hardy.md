---
title: "Low Graphics Mode in Hardy"
date: 2008-05-12
forum: General Help
---

### Post by JonathanSchroeder on 2008-05-12
Ok, so i recently upgraded to 8.04 from 7.10, and when i rebooted after upgrading, i was forced into low graphics mode.  While upgrading to hardy, i noticed that one of the things it did after the restart failed.  It said something like "vn.mmap_min_addr" is an unknown key. Low graphics mode means no visual effects whatsoever, and a small screen. I have a Nvidia GeForce 7600GT graphics card, with the latest restricted driver in use.  I accessed a thread i thought could help me, but it didn't, and they didn't respond to my comment, cus the original problem was already solved.  It can be found here:
[http://ubuntuforums.org/showthread.php?t=784615](http://ubuntuforums.org/showthread.php?t=784615)
When I tried to access nvidia-settings, it tells me to run nvidia-xconfig as root. This leaves me with this message:
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

I also tried "sudo apt-get install xserver-xgl" and restarting xserver.  i also tried reinstalling compiz.  Nothing worked. Any ideas?

---

### Post by Zer0Nin3r on 2008-05-12
Been having the same/similar problem that you have been experiencing after I upgraded.

[See my post]("http://ubuntuforums.org/showthread.php?p=4945361#post4945361").

---

### Post by Xgen on 2008-05-13
Try installing envyng-core and envyng-gtk through Synaptic and running the program. I usually upgrade to the latest beta from nvidia after that.

---

### Post by cros13 on 2008-05-13
definately envy is the solution. Your nvidia drivers / libraries have got fscked up. reinstalling the nvidia proprietary driver should work to as this now includes the ability to search for conflicting libraries.
In future you can help avoid this situation with future upgrades by removing the proprietary driver before the upgrade and then reinstalling after.

---

### Post by JonathanSchroeder on 2008-05-13
I installed the envy packages you said and restarted my computer but to no avail.  Still in low graphics mode.  What did you mean by "upgrade to the latest beta from nvidia" and "reinstalling the nvidia proprietary driver"?  And how do you do these things?

---

### Post by Xgen on 2008-05-13
Well, reinstalling the propriety drivers might be a solution, but if you wish to install the drivers from NVidia:

Google 'nvidia'--->Download Drivers section.
Advanced Driver Search--->Product Series: Geforce 7x Series. Download latest driver (169.12) or Beta (173.08 - below Advanced Driver Search).
Optionally rename file to a simpler name (e. g. nvidia169) and optionally relocate. 

* Ctrl + Alt + F6--->login and password.
* sudo /etc/init.d/gdm stop
* sudo sh (path +name of nvidia file)
* On menu choice--->ACCEPT and press ENTER 3 or 4 times to get by menu boxes (or read).
* When it is through compiling, on the last choice accept (or not) whether to write to the xorg.conf file. Perhaps you should for the first time.
* sudo /etc/init.d/gdm start

---

### Post by briandu on 2008-05-13
Just follow exactly as the post states and should work:

[I][http://ubuntuforums.org/showthread.p...=1#post4908847]("http://ubuntuforums.org/showthread.php?p=4908847&posted=1#post4908847")

Cheers
[/I]

---

### Post by JonathanSchroeder on 2008-05-13
Ug.  Well, i went through the process numerous times, trying both of the suggested ways and so here is what happened.  When i got to the command prompt, here is what it said after I clicked accept
no precompiled kernel interface found to match your kernel
i clicked ok
No matching precompiled kernel interface was found on the NVIDIA ftp site;
o clicked ok
the CC version check failed:  compilers didn't match. kernel compiler gcc4.1 doesn't match current compiler gcc4.2
it asked me if i wanted to stop. Saying yes got me back to command prompt, and saying no got me to
unable to find kernel source tree for currently running kernel.
It also said that i should install 'kernel-source' and 'kernel-devel' RPM.  I found kernel-devel, but i didn't find anything that was exactly kernel-source, and i don't wanna risk install conflicting packages, so i didn't install anything.  It said that the nvidia-installer.log file may be useful, but it won't let me attach it, so...



nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue May 13 16:56:45 2008

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> The CC version check failed:
   
   The compiler used to compile the kernel (gcc 4.1) does not exactly match the
   current compiler (gcc 4.2).  The Linux 2.6 kernel module loader rejects kern
   el modules built with a version of gcc that does not exactly match that of t
   he compiler used to build the running kernel.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: No)
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).



But ya know, i am not sure that nvidia is the problem, cus i tried switching over to my motherboard's graphics card (not nvidia), and i was still stuck in low graphics mode.

---

### Post by Xgen on 2008-05-13
[https://answers.launchpad.net/ubuntu/+question/30999](https://answers.launchpad.net/ubuntu/+question/30999)

---

### Post by thedevnull on 2008-05-13
I have had the same problem.  :(  Its a known bug...

[https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/173418]("https://bugs.edge.launchpad.net/ubuntu/+source/xorg/+bug/173418")

---

### Post by Zer0Nin3r on 2008-05-14
> **Xgen said:**
> [https://answers.launchpad.net/ubuntu/+question/30999](https://answers.launchpad.net/ubuntu/+question/30999)

I pulled the following from the link above.

>  georgaeie  said on 2008-04-30: 

Hello everyone,

I had the exact same problem when upgrading from gutsy 7.10 to hardy 8.04.

I have a nvidia geforce 6100 card.

The solution on my system was simple; the old /boot/grub/menu.lst was still in place, causing the old kernel to be loaded in stead of the new one. I spent 4 hours figuring this out. Clever me... The 'kernel is compiled using gcc-4.1 should have set off the alarm'..

Anyway, I did the following:

sudo -i
vi /boot/grub/menu.lst (changed everything from 2.6.22-14-generic to 2.6.24-16-generic - make sure you refer to the correct kernel in /boot !!)
reboot
apt-get install nvidia-glx-new linux-restricted-modules nvidia-settings
rm /etc/X11/xorg.conf
nvidia-xconfig
/etc/init.d/gdm restart (may need to stop gdm, kill all remaining X processes and start gdm again)

..and now everything works!

Can anyone verify this?  Also as I stated in [my post]("http://ubuntuforums.org/showthread.php?t=792276"), I am able to run 8.04 with the previous kernel with nVidia graphics support utilizing version [100.14.19]("http://www.nvidia.com/object/linux_display_ia32_100.14.19.html") of the driver.

Everything seems to run fine including Google Earth.  Food for thought.

nVidia also keeps an [archive]("http://www.nvidia.com/object/linux_display_archive.html") of Linux drivers.

---

### Post by Zer0Nin3r on 2008-05-17
> **JonathanSchroeder said:**
> The CC version check failed:  compilers didn't match. kernel compiler gcc4.1 doesn't match current compiler gcc4.2

unable to find kernel source tree for currently running kernel.

Was doing some tinkering with the drivers and newer kernel and broke the system.  Now I'm back to square one.  I ran into the same problem as in the quote before and I used to be able to revert back to the old driver and old kernel before, but now I'm stuck.  I cannot remember if I'm forgetting something in order to work around the gcc problem.

---

### Post by thedevnull on 2008-05-21
Anyone know if this is officially listed as a bug?  I found references to it but not an exact one...

Thanks!

---

