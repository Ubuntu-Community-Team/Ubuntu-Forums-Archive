---
title: "woeusb and other repository"
date: 2019-03-31
forum: General Help
---

### Post by iamtheeggman2 on 2019-03-31
Hi,

I wanted to install windows 10 onto my new setup however I have downloaded the iso file but ubuntus own usb drive maker doesnt recognise other iso's not even other linux ones, anyway, I found a tutorial for using a program called woeusb but in order to install it i have to add some other repository to my list, I am concerned aout ubuntu updating variety of programs from this repository, should I be concerned? I wonder is there an easier way to get this iso onto a usb stick?



home@home:~$ sudo add-apt-repository ppa:nilarimogard/webupd8
 The main Web Upd8 PPA maintained by: [http://www.webupd8.org/](http://www.webupd8.org/)

To add this PPA, simply paste this in a terminal:
sudo add-apt-repository ppa:nilarimogard/webupd8

Packages in this PPA: audacious, ap-hotspot, awn-applet-radio, awn-applet-wm, calise, cmus, dockbarx, dockbarx-themes-extra, dropbox-share, emerald, exaile, fbmessenger, gnome-subtitles, gnome-window-applets, grsync, grive, gthumb, launchpad-getkeys, mc, mdm (Mint Display Manager), minitunes, minitube, musique, notifyosdconfig, nautilus-columns, powertop, ppa-purge, rosa-media-player, fixed pulseaudio-equalizer, subtitleeditor, syncwall, umplayer, unity-reboot, wimlib, youtube-dl, xfce4-dockbarx-plugin, xournal, yad, yarock and others. Almost all packages are updated to their latest version.

For other (specialized) PPAs we maintain, see: [https://launchpad.net/~webupd8team](https://launchpad.net/~webupd8team)
 More info: [https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8](https://launchpad.net/~nilarimogard/+archive/ubuntu/webupd8)
Press [ENTER] to continue or Ctrl-c to cancel adding it.

---

### Post by yancek on 2019-03-31
Most usb creation tools on Linux will not create a bootable windows iso/usb so that's no surprise.  I've not used woeusb although I have read a number of posts about so don't have any opinion.  If you want easy to create a bootable usb with windows, I expect you would need to use a windows OS to do that.  

Using Linux, the general process would be to loop mount the windows iso, copy the extracted windows files to an ntfs formatted partition on a usb drive, mark it as active and put a proper boot entry in your grub.cfg file in Ubuntu and boot to install.  Extremely detailed instructions at the site below which, if followed correctly, will work so if you want to do it from Ubuntu, this works, if you want easy I expect you willl need to use windows and don't know if that will be easy.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by iamtheeggman2 on 2019-04-01
OK well I eventually found a way to do this via windows command prompt to create bootable partition then copy files from the mounted iso into the USB drive worked a charm

---

