---
title: "udev filtering"
date: 2014-07-20
forum: General Help
---

### Post by juju43 on 2014-07-20
Hello,

I'm trying to use some usb filtering from [http://www.lexsi-leblog.fr/audit/danse-des-canards.html](http://www.lexsi-leblog.fr/audit/danse-des-canards.html) and optimize it for day to day.

basically adding to udev rules
```
ACTION=="add", ENV{DEVTYPE}=="usb_device",SUBSYSTEM=="usb",RUN+="/usr/local/bin/usb-prevent-ducky.py %k '%E{DEVNAME}' '$attr{manufacturer}' '$attr{idProduct}' '$attr{serial}'"
```

and executing prevent-ducky.py script to ask user if he wants to use the device

1- tested on lubuntu 12.04. the script logs as blocking device. It does but you have to disable automounting
* normal ubuntu
```
gsettings set org.gnome.desktop.media-handling automount false
```
as advice on [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
* lubuntu/lxde
pcmanfm > edit > preferences > volume management
not found cli command on either per user or global (and prevent user to change it)

2- In the case we allowed peripherals, I want automount to apply. so how to call udisks for relevant device?
something in python script like
```
popup("udisks --mount %s --mount-options ro,nodev,nosuid,noexec" % devname)
```
but devname is not the right devpath and need to manage multiple partitions/filetype which the script has no view inside.
Or is there a way in udev to say: previous script returned allow so execute other command else stop all processing (not really sure if OPTIONS="last_rule" is working today).

3- How to whitelist past allowed devices to avoid gui questions? and to allow some specific device like your usb keyboard and mouse ;)
for example appending some rules to a whitelist udev rules files.

4- How to force some mounting flags on default or identified devices? default on lubuntu seems
```
vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
```
I would prefer ro,noexec,nosuid (depending if unix partition or not)
And enabling rw or else only on a whitelist

Previously I add rule like
```
ACTION=="add", SUBSYSTEM=="block",ATTR{idVendor}=="1987",ATTR{idProduct}=="01234",ATTR{serial}=="12354646576451467413334",RUN+="/usr/local/bin/usbfilter-mount2.sh %p rw,noexec,nosuid,nodev"
```
(after the prevent ducky) but it's not working anymore

It seems now, there are
* either customize udev rules like [http://askubuntu.com/questions/61448/how-to-configure-to-record-data-to-pendrive-instantly](http://askubuntu.com/questions/61448/how-to-configure-to-record-data-to-pendrive-instantly)
* either udisks-glues
[http://askubuntu.com/questions/289696/set-mount-options-for-removable-devices-on-kubuntu](http://askubuntu.com/questions/289696/set-mount-options-for-removable-devices-on-kubuntu)
[http://manpages.ubuntu.com/manpages/oneiric/man5/udisks-glue.conf.5.html](http://manpages.ubuntu.com/manpages/oneiric/man5/udisks-glue.conf.5.html)

Any help?

Thanks

---

