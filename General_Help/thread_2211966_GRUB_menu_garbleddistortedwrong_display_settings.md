---
title: "GRUB menu garbled/distorted/wrong display settings?"
date: 2014-03-18
forum: General Help
---

### Post by Nopposan on 2014-03-18
I successfully installed Lubuntu 12.04 on an old Dell Inspiron 8100 with 256mb of RAM and it's working quite well except for one issue.

The Grub menu can't be read because the screen is overwritten with "@@@" and such and it seems it's not displaying in the right resolution or maybe the refresh rate is wrong. 'Not sure. Once the Nvidia driver kicks in, all is well, however, and the lxdm and lubuntu desktop come up fine.

What can I do to make the GRUB menu readable to my end users?

Thanks.

---

### Post by oldfred on 2014-03-18
I think grub tries to use the video mode from Ubuntu, but does not always work.

You can try setting display to a lower level default.
If you know what grub will support (usually from BIOS) you can use that instead of 640x480

       Use command line editor grub's on set gfxmode=640x480
and just remove the # as that makes that line a comment.
sudo nano /etc/default/grub
or
gksu gedit /etc/default/grub
# then 
sudo update-grub


 Details on settings in /etc/default/grub
 info -f grub -n 'Simple configuration'
> `GRUB_GFXMODE'
     Set the resolution used on the `gfxterm' graphical terminal.  Note
     that you can only use modes which your graphics card supports via
     VESA BIOS Extensions (VBE), so for example native LCD panel
     resolutions may not be available.  The default is `auto', which
     tries to select a preferred resolution.  *Note gfxmode::.


   From a grub command line to see available settings pressing <c> & escape to get back to menu
vbeinfo

---

### Post by Nopposan on 2014-03-18
Supposing that works, is there a way to set it right after the system installation finishes and before first boot?

I'm thinking about the other volunteers whom I've got to pass a protocol down to once I get this settled.

Thanks.

---

### Post by oldfred on 2014-03-19
If you know from vbeinfo a correct setting, you just set that in etc/default/grub instead of 640x480.

---

### Post by Nopposan on 2014-03-20
Thanks, Oldfred. O.k., so I have got the problem fixed. There is a way to fix it after Lubuntu Alternate CD install too. You fix it just like Oldfred said, but to do it before booting the installed system (Booting up without fixing caused my screen to look like it was briefly imitating the northern lights and then it slowly faded to black -- rather spooky.) you select "execute root shell" or something like that, and then you get a message informing you that the installed system is mounted on /Target whereas your working directory is in RAM. So you cd /Target and modify etc/default/grub using nano.

cd /Traget
nano etc/default/grub

CAUTION: if you instead do this
nano /etc/default/grub

You'll open an empty nano text file which will be erased as soon as the system reboots! 'Sorry to say I made that mistake once; I didn't get so far as rebooting, but I was perplexed as to why there was nothing in the grub configuration file! :-)

Thanks for the help.

---

