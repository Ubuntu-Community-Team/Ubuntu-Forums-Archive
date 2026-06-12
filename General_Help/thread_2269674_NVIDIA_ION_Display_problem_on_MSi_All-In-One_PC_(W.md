---
title: "NVIDIA ION Display problem on MSi All-In-One PC (Wintop)"
date: 2015-03-17
forum: General Help
---

### Post by matey3 on 2015-03-17
Hello everyone:
Wow I cant believe I got in! Heh been out of job for 3 years now so been away from Ubuntu for a long time and I have forgotten many of the commands :( anyway; I have 2 questions (I didnt want to open another thread so I post both here):

1- I am dual booting with win7 and  Ubuntu 12.4 on this MSi touch screen wintop pc. Everything was working before but:

Recently when I booted into Ubuntu my display driver was set to _Basic VGA_ and so the screen is so big that I cannot use it easily.(so I am using my win 7 right now)
I wondered if there is a solution to put the working Display Driver(s) back on it cuz I miss Ubuntu.
There is a Nvidia Display Driver icon there under Administration/Display but the only res. is at 640 at the drop-down menu & cant be changed!
Anyway I dont care about the touch-screen and hardly ever use it. I just want my Hi Res. back. Thanks!

2- I wonder if I can install an older version of Ubuntu on my machine? 

To tell you the truth I dont like the newer version because the OS has too much control and locks everything down and has taken our freedoms away... like the display settings the desktop setting etc, (I am used to the older version where I could move the bar on bottom of the desktop and it is stuck on top and I hate it).
plus lot of other little things which made me go back to windows. (I really liked Ubuntu 7.x and got so used to it but after 12.x feh... they fixed things which were not broke)... My new Asus laptop wont even boot anymore with Ubuntu 14.x and no boot menu? (but thats another story)...

Thanks in advance!

---

### Post by nerdtron on 2015-03-17
1. You probably have updated your Ubuntu (and kernel) so you need to reinstall the NVIDIA drivers. Try to reinstall the the drivers from the Additional Drivers Utility, reboot and you should have your HD resolution back

2. As for the user interface, don't install a lower version since they are no longer supported, and newer versions with newer kernels probably will bring better hardware (touchscreen) support. If you like the old interface, you can install other flavors of Ubuntu like Kubuntu 14.04 which still have the usual bottom bar, or have a try on Xubuntu.

As for the new Asus Laptop, you can open a new thread on that, it probably is UEFI or display drivers issues. (lots of post here on the forums for these new laptop problems).

---

### Post by SeijiSensei on 2015-03-17
I have an older ASUS netbook with an ION processor.  Kubuntu 14.04 with the proprietary NVIDIA driver works fine on that platform.

---

### Post by matey3 on 2015-03-17
Thanks for the reply. I checked the /etc/X11/xorg.conf-backup file and copied it as xorg.conf then ran the nVidia configurations as root (it said so) so it copied the backup file as new and I got high resolution! :) I am using 1440X900 right now, but still I got a lot more res. left to try! ;) yeah... and I am glad I am using my Ubuntu once again! :)

Thanks for the info. I'll check for updates and even an Upgrade (to 14.4) as you said but I have to get my courage up first lol been away so long...it's terrible how you forget things.
Thanks a lot! and give yourself a big Thanks for me!
Regards;


> **nerdtron said:**
> 1. You probably have updated your Ubuntu (and kernel) so you need to reinstall the NVIDIA drivers. Try to reinstall the the drivers from the Additional Drivers Utility, reboot and you should have your HD resolution back

2. As for the user interface, don't install a lower version since they are no longer supported, and newer versions with newer kernels probably will bring better hardware (touchscreen) support. If you like the old interface, you can install other flavors of Ubuntu like Kubuntu 14.04 which still have the usual bottom bar, or have a try on Xubuntu.

As for the new Asus Laptop, you can open a new thread on that, it probably is UEFI or display drivers issues. (lots of post here on the forums for these new laptop problems).

---

