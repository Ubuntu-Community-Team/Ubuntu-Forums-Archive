---
title: "XServer Crashes on Restart"
date: 2007-10-20
forum: General Help
---

### Post by iansen on 2007-10-20
I just got a new laptop computer (Acer Aspire 5520G) ... it came with Vista .
I wanted to keep Vista and not change the file system so I downloaded Wubi.... installed Ubuntu.
The first time I booted to Ubuntu  I got a xserver error.... got back to Vista and searched the forums.
Here is what I found: - the problem was caused by my video card (geforce 8440m) ...updated the drivers using :
[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.09/NVIDIA-Linux-x86-100.14.09-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.09/NVIDIA-Linux-x86-100.14.09-pkg1.run) .
It worked fine  - after the installer finished setting up the kernel modules    I started gdm  (/ect/init.d/gdm start) and it worked fine. It even made a start menu item for Nvidia Control Panel.

After a while I restarted the computer and tried to log back into Ubuntu .... no luck ...got another  xserver error .... this time it said  tthe Kernel module version does not match the driver version .

If I reinstall the driver it works fine .... until I restart .

Any ideas ? :confused: ...the xorg.conf file settings are the ones the driver installer makes .

---

### Post by maikie on 2007-10-23
I had similar issue I followed this and it worked.

Hope it helps

> 
If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

---

### Post by iansen on 2007-10-24
Thanks for the reply .... I'll try to do what you just said :-P ..I'm kind of new to Linux so it might take some time :D  .
I'm trying this on a wubi installation on my laptop ... I managed to install Ubuntu 7.04 ....I hope it has all the things you said  I don't know how to look for them :(.
I would appreciated if could give me some quick pointers  .... or a link to a how to ..

Thanks again for the reply.

---

### Post by maikie on 2007-10-29
Hello,

What are you trying to do?

Do you want to install the nvidia drivers? You will need to download them,

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

fill in the information and put linux. You will need to install the drivers but they will not install while x-server is running.

If you press ctrl+alt+f2

Then type sudo /etc/init.d/gdm stop

That should stop xserver. Installing the drivers. type, sudo sh PATH/TO/NVIDIA/FILE.sh

Then it should install.

---

### Post by siddharth.unnikrishnan on 2007-12-28
hey...

im pretty new to the world of ubuntu and wubi...ive been trying to install ubuntu on ma hp notebook since august 06 but in vain. at first tried 7.04 with the live cd, but it just dint boot up...so i thot its ma sata hard drive (i had a similar problem with xp) then i waited till the 7.10 was launched. with the live cd it booted up properly and then i installed it removing vista from my notebook. after the installation, when i tried to reboot into ubuntu, it just got stuck at the loading menu at 'bluetooth services'. waiting for a long time proved futile as it just wudnt load. then i install vista again and have been trying my hand at ubuntu all the time since then.

now i installed wubi which installed ubuntu 7.04 completely but ive been having the x server problem. i tried sudo dpkg-reconfigure xserver-xorg and it starts the reconfiguring utility. ive been tryn to save different configurations hoping that it will boot up ubuntu in someway. but i keep getting the same error all the time. could someone please help me out with this and tell me the step by step procedure to get it right on ma notebook...dats just cuz im pretty new :)

---

### Post by ago on 2007-12-30
try with vesa driver first
if you have internet working (try pinging google.com) you can install the driver required for your video card with "sudo apt-get install DRIVERNAME"

---

### Post by siddharth.unnikrishnan on 2007-12-30
hey...

thanx a lot for the tip....tried vesa and after a couple of tries got 7.04 up... been playing around with my new os since then...just another problem... 7.04 doesnt recognize my wireless device and i cant connect to the net using wifi... i use an hp pavilion dv6500t... am still tryn to get myself connected using 7.04.... do lemme kno if u know how to get this fixed...

thanx again....

byez! :)

---

### Post by ARGMan on 2007-12-31
Hi Siddharth, I wonder if you can help me please, I have a similar problem to you with the xserver and my laptop and I have been trying numerous attempts to get ubuntu 7.04 to get past the xserver problem from an original wubi install?
I notice in your post that you also tried a few times and then eventually got into ubuntu - what was it about your answers to the numerous questions in the xorg configure script that actually made it work for you? If you can remember then hopefully I can get may laptop to run ubuntu too? I have an ATI Mobility x1600 graphics card in my laptop which is causing the problem. I have tried selecting the ati from the list and also the vesa from the list but I guess I must be answering the other questions wrongly in some way as it always fails to start the X-Server!!

Any help would be enormously appreciated as I am relatively new to Ubuntu although I do have it loaded onto my desktop machine with a NVidia graphics card and it runs without a problem from the wubi install.

Cheers,
Tony.

---

### Post by ARGMan on 2007-12-31
Its okay, I have managed to figure it out by using a combination of information from various posts on this forum. It took a little while but I got it running on the laptop perfectly in the end!

---

### Post by siddharth.unnikrishnan on 2007-12-31
:) welcome to wubi 7.04.... by the way...could u get ur wireless device started? i just cant manage to get myself online wirelessly... lemme kno if u find a way out.... 

wishin a happy new yr to all...

regards,
siddharth.

---

