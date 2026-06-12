---
title: "How to make liveCD load other graphics drivers?"
date: 2008-03-10
forum: General Help
---

### Post by Svopp on 2008-03-10
Hi there,

I am having problems with the 64 bit 7.10 ubuntu liveCD. It makes black screen after the run/install button is hit ... failsafe graphic drivers load also make blackscreen.

I tried it on my friends computer aswell, and it also makes blackscreen.
Note that neither of them do blackscreen with the 32-bit version. And yes, both our computers support the EM64 bit thingy.

These are the drivers i want the installation to use.
[http://www.nvidia.com/object/linux_display_amd64_169.12.html](http://www.nvidia.com/object/linux_display_amd64_169.12.html)

Now ... I wanna know how i should burn them down. If they should be saved in a special way on an external CD, or exactly how to do.

Thanks in advance

---

### Post by forrestcupp on 2008-03-10
When you get to the LiveCD menu, you can press F6 to enter extra boot options.  I was going to suggest forcing Vesa drivers and installing your nvidia drivers after it is installed.  But I tried the boot option myself just now, xdriver=vesa, and it still booted to the nv driver.  So I really don't know how to force it to vesa.

So my suggestion to you is to use the Alternate installation CD to install it because it is text based.  Then after you have it installed, you can get your nvidia drivers working.

If you do that and it still won't boot up right, you can choose the 2nd option in GRUB to boot to the CLI.  Then you can type:
```
dpkg-reconfigure xserver-xorg
```
And manually choose the vesa driver.  If for some reason it doesn't boot to root, you'll have to put a sudo in front of that command.

Then when you get it booting correctly, we can work on your nvidia drivers.

---

### Post by Rocket2DMn on 2008-03-10
I think the correct kernel line to add is "xforcevesa", don't quote me on that though.  If you're just going to install, you can use the alternate install CD available at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom for alternate cd.  It is an easy to use text based installer without a live session, so graphics are not a problem during installation.  Once installed you can setup the nvidia proprietary drivers, preferably from System->Administration->Restricted Drivers Manager, but you can download the ones from nvidia if you're up to the task.

---

### Post by crtlbreak on 2008-03-25
The option under the F6 boot is 'xforcevesa' to force the vesa driver to load - I tested it with the live CD of gutsy about 10 minutes ago  - after the live CD has loaded go to a terminal and check with
sudo cat /etc/X11/xorg.conf
will show the vesa driver loaded in the Xserver
There have been many posts with issues relating to nVidia cards and drivers  - seems that nVidia are not "open" at all.

---

