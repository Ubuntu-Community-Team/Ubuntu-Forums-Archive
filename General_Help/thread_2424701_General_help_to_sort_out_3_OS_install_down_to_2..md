---
title: "General help to sort out 3 OS install down to 2."
date: 2019-08-13
forum: General Help
---

### Post by adrian-h on 2019-08-13
Thought that before I mess up my computer I would ask for some guidance on here.

I use an elderly computer a Dell Optiplex 780, for my sins it has 3 OS's on it.  Half the disk has Windows 7 which I wish to keep.  1/4 disk is Opensuse 15 and the last 1/4 is Ubuntu 18.04.

I wish to remove the Opensuse completely and expand Ubuntu to fit.

One of he problems is that the grub loader that selects which OS is in Opensuse.  I am not sure how to go about this.  I would like to keep the software I have in Ubuntu without a re-install as my internet speed is not great and it would take me most of the day to download from a fresh install.

So any guidance before I manage to mess it all up?

Cheers

Adrian

---

### Post by guiverc on 2019-08-13
Assuming you want your Ubuntu to own the MBR or *master boot record *(the first stage of grub), you should boot Ubuntu, and enter the command `sudo grub-install /dev/sdX`where sdX is your boot disk (if you have more than one drive, your BIOS config controls which of these disks MBR is the critical one and it's that drive, commanly it's sda; but the MBR is only the first 512 bytes of the disk).

On reboot you should confirm the Ubuntu's grub boots; then you can delete your opensuse partition and expand your Ubuntu partition(s). To do the expansion I would boot a 'live' system (eg. Ubuntu install media) and use `gparted` (or equivalent, eg. if you're a KDE person you could use KDE Partition Manager).

At worst the /boot/grub/ directory could be moved (the MBR points to it, a move could cause it to point in the wrong place) so you may have to enter a few commands boot your system & re-enter the `grub-install` command to fix. It's my opinion you ignore that until it's a problem (as it's only a possible one).

---

### Post by oldfred on 2019-08-13
+1 on guiverc suggestions.

But you also should have good backups, just in case. Any major change always has a chance that user, system or fate, causes issues. If you have a backup then those issues are not the end of the world.

Also if slow Internet, you should learn about zsync. I have fast Internet, but use zsync to update ISO and have not downloaded an entire Ubuntu ISO for several years. I do copy & rename to the different version or flavor & zync it. New versions like my update of my 19.04 ISO to 19.10 regularly gets large changes, but by time released changes are small. 

[https://www.ostechnix.com/zsync-file-transfer-utility-download-new-parts-file/](https://www.ostechnix.com/zsync-file-transfer-utility-download-new-parts-file/)

For example if you have the 18.04 ISO your can copy it to 18.04.3 and run this, it only updates the changes. You need to copy & paste the full command, but forum only now displays a shorten version. if you run cursor over it, you can see at bottom the full command. It needs to be run from terminal in the folder you have the ISO.
zsync [http://releases.ubuntu.com/18.04/ubuntu-18.04.3-desktop-amd64.iso.zsync](http://releases.ubuntu.com/18.04/ubuntu-18.04.3-desktop-amd64.iso.zsync)

Full command is zsync at beginning & .zsync at end. Then the web site & iso file. The web site for released distributions can be any mirror, but often best to check the mirror for what it offers & its exact path to the ISOs.

You can see which ISO files are available as zsync:
[http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)

---

### Post by adrian-h on 2019-08-13
Ok thank you for your suggestions I will give it a go, sorry for the late response i thought I would have got an email to say someone had responded!.. I must have missed a setting somewhere.

Adrian

---

### Post by adrian-h on 2019-08-13
Well do not know what went wrong but it did, opensuse was /dev/sda6
the swap was /dev/sda5 and ubuntu was /dev/sda7.

When 6 was deleted all the rest went wrong.  It would not resize /dev/sda7, it would not reboot successfully.

In the end i used a live version to copy my needed files into the Windows partition as it would not mount any external USB sticks or anything.

I am now doing a new install on half of the disk keeping the win7 OS as well and i should be able to get my data back later, the programs i will install from the net even if I leave it running for several hours.

Thanks all

Adrian

---

### Post by yancek on 2019-08-13
You haven't indicated if this was an MBR/Legacy install with an msdos parrtition table but that seems to be the case.  If your Opensuse and Ubuntu partitions were logical partitions on an Extended partition, when you deleted sda6, partitions with higher numbers dropped one number so that Ubuntu is not longer sda7 but sda6.  That's just the way partition numbering works on older Legacy systems.

---

### Post by adrian-h on 2019-08-13
I got an email.

Hello and yes yancek it was a MBR/legacy install, the machine was from the days of Win 7, well the OptiplexI believe was from 2010 so it is an old machine.

No problem I have started to get the programs back on it, I have recovered my data from Windows C: that s safe.

I understand what you are saying and that does stack with what I saw in partitioner, it was just that I could not resize things after deleting sda6 and things went down hill from there, perhaps i should have deleated the data from it and then resized sda6 to something small like a few Meg, that way it would still have been there, i might have been able to resize sda7 then?  To late to tell now.
Just reinstalling GNU-radio and all the bits that go woth it.

The PC does what I need, the quad core cpu still does me OK.

Adrian

---

### Post by adrian-h on 2019-08-13
I have spoken to soon, I downloaded 18.04.3 LTS to install and it seems to be giving me issues, I have a flashing splash screen when starting up and it does not start up, I thought it may have been the old ATI radion card but it is happening with the on board graphics, eventually the flashing screen stops and I am am left with the 5 changing dots all the time.

I have noticed an error and if I can get it to reboot I will post. 

How do I get back to the test information on boot up, I could previously just press the esc key but I get blank screen now?

Cheers

Adrian

---

### Post by guiverc on 2019-08-13
> **adrian-h said:**
> .. I downloaded 18.04.3 LTS to install and it seems to be giving me issues, I have a flashing splash screen when starting up and it does not start up, .. Adrian

I would suggest when you boot the 18.04.3 and when you see a keyboard-in-rectangle, plus person-in-circle you quickly press a key to have a menu show. On my box (optiplex 755) i was asked language then given a menu which has "Check disk for defects" which is what I suggest you use.  It'll verify your download, plus write to install-media were flawless. 

The option I'm suggesting is [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck) (though screen image will differ, and CD applies even if your install media is a thumb-drive).

*FYI: the description above came from booting both Xubuntu 18.04.3 & Lubuntu 18.04.3 flavor RCs on my 755; I don't have the patience for gnome on my older boxes, and don't have the Ubuntu 18.04.3 ISO lying around.  My primary box is a optiplex 960 (which has the same motherboard specs as my optiplex 780, even same spec'd video card)*

---

### Post by adrian-h on 2019-08-13
Hi this is when booting from normal I get the grub screen up and I can select which OS to run.

It looks like a:-
Failed to start user manager for uid 121

if I use 

```
getent passwd | grep 121
```

gdm: x :121:125:Gnome Display Manager:/var/lib/gdm3:/bin/false

Withe various keyboard presses basically the "break key" I end up with a login window where i enter my password and it logs me in and from there it is fine.  The machine is normally set to auto-login  I have disabled that and sometimes it works but mainly not and I have to resort to the break key a few times.

I can not get a terminal to run with cntl-alt-F2 until after I hit the break key a few times so I I only see a screen with the errors for a split second before it is hidden.

I am not sure if these are of use?
```
Aug 13 23:07:44 OptiPlex-780 PackageKit: search-file transaction /120_aaeaadaa from uid 1000 finished with success after 807ms
Aug 13 23:07:44 OptiPlex-780 gnome-control-c[2156]: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
Aug 13 23:07:44 OptiPlex-780 gnome-control-c[2156]: message repeated 4 times: [ g_object_unref: assertion 'G_IS_OBJECT (object)' failed]
Aug 13 23:07:45 OptiPlex-780 PackageKit: get-details transaction /121_eebdddba from uid 1000 finished with success after 841ms


Aug 13 23:08:55 OptiPlex-780 dbus-daemon[778]: [system] Successfully activated service 'org.freedesktop.hostname1'
Aug 13 23:08:55 OptiPlex-780 systemd[1]: Started Hostname Service.
Aug 13 23:09:01 OptiPlex-780 CRON[2391]: (root) CMD (  [ -x /usr/lib/php/sessionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Aug 13 23:09:03 OptiPlex-780 gvfsd-metadata[1926]: g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed
Aug 13 23:09:03 OptiPlex-780 gvfsd-metadata[1926]: message repeated 7 times: [ g_udev_device_has_property: assertion 'G_UDEV_IS_DEVICE (device)' failed]
Aug 13 23:09:14 OptiPlex-780 systemd[1]: Starting Clean php session files...
Aug 13 23:09:14 OptiPlex-780 systemd[1]: Started Clean php session files.
Aug 13 23:14:12 OptiPlex-780 gnome-shell[1577]: Some code accessed the property 'WindowPreviewMenu' on the module 'windowPreview'. That property was defined with 'let' or 'const' inside the module. This was previously supported, but is not correct according to the ES6 standard. Any symbols to be exported from a module must be defined with 'var'. The property access will work as previously for the time being, but please fix your code anyway.
Aug 13 23:15:08 OptiPlex-780 dbus-daemon[778]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.84' (uid=1000 pid=2460 comm="gedit /var/log/syslog " label="unconfined")
Aug 13 23:15:08 OptiPlex-780 dbus-daemon[778]: [system] Successfully activated service 'org.freedesktop.hostname1'
```

But I do notice a few errors in syslog

At least I can find a way to get the computer up and running and will have to hope for an update that helps!

Adrian

---

