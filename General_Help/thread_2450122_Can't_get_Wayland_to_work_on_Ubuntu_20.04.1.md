---
title: "Can't get Wayland to work on Ubuntu 20.04.1"
date: 2020-09-07
forum: General Help
---

### Post by Hewjr100 on 2020-09-07
I have tried uncomenting Wayland =false and when I reboot the option to switch from Ubuntu or Ubuntu on Wayland is not there.  Tried changing it to Wayland=true, no luck.  I have done this while using open source Nvidia 450, from Nvidia ppa site.

Going back to Xorg and see if that works.  The problem is that the default install from mini iso does not install Nvidia drivers, and when finished I cannot get to the login screen unless when booting I hit esc the "E" to edit grub boot process.  Then I add nouveau.modeset=0 to the Linux line.  I can't keep doing this every time I turn on or reboot my laptop, and I see no way to save this option.  Also add nomodeset to /etc/default.grub causes the system to boot to a black screen, in whick case I cannot get to login screen.

As for installing with full image and selecting extras for wifi and graphics work, fine.  Only issue is rippling and tearing when scrolling on some web pages.  This occurs with Firefox and Google Chrome.  Any suggestions would be helpful.

Henry

---

### Post by Hewjr100 on 2020-09-07
Using Xorg graphics llvmpipe ( 10.0.0, 128 bits ) and Wayland=false uncommented, reboot I get a black scree with the following:

[ 7.609465 usci_acpi usbc 000: 00: PPM init failed ( -110 )

Don't know if this helps

Henry

---

### Post by rbmorse on 2020-09-07
The following works for me on my desktop PC running 20.04, but no idea how it behaves on a laptop.  I have an Nvidia 2080RTX GPU running the proprietary 440.xx driver. 

1. Make sure the proprietary Nvidia driver installed is at least version 440.xx 


2. add the kernel boot option: 

    nvidia-drm.modeset=1

I was able to make this permanent by editing the GRUB options and then running update-grub.  

    
3. Open /etc/gdm/custom.conf and comment out the the statement: 

     # WaylandEnable=false 
     
in the [daemon] section.  May already be done. 
 

4. Open /usr/lib/udev/rules.d/61-gdm.rules and comment out (make inactive) the statement:  


    # DRIVER=="nvidia", RUN+="/usr/libexec/gdm-disable-wayland"   
    

5. Full reboot.  GDM restart will not be sufficient. 


When the machine restarts, you should have the gear symbol on the password screen with session options, one should be Gnome on Wayland.  If you see, instead:

gnome
gnome classic
gnome on x.org

The "gnome" option will load Wayland.


As far as I can tell, all this is unsupported.  I can say that Xwayland apps do not work properly, and my experience was that the entire desktop stack would crash without particular reason at infrequent intervals.  I'm back on X.org full time.

---

