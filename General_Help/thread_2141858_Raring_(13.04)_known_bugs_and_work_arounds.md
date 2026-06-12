---
title: "Raring (13.04) known bugs and work arounds"
date: 2013-05-03
forum: General Help
---

### Post by cariboo on 2013-05-03
Personally, since we started using the 3.8 kernel, Raring has been running remarkably well, but I know there are some members with various combinations of hardware that have run into problems. This is the place to post bugs that you have found (remember to create a bug report too) and ways to work around them.

---

### Post by pqwoerituytrueiwoq on 2013-05-03
These 2 common issues have the same solution
[LIST]
[*]Broken HDMI audio (It worked in 12.10 but not in 13.04 scenario) *the hdmi audio does not appear is the sound configuration options 
[*]Lots of text at boot, that mentions something about "soft lockup" [looks like this]("http://i.imgur.com/EG6zyWQ.jpg") (673.08 KB), it will boot eventually if you keep rebooting, then you can fix it, this also happens in recovery mode, i have had this happen on a clean install before installing anything 
[/LIST]
Both of those issues have the same solution, upgrading the [mainline 3.9 kernel]("https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater#readme") appears to solve them
Another way to get the 3.9 kernel is to pull it from saucy (When saucy starts using the 3.10 kernel you will get a update but it will break virtualbox, may also break your nvidia/amd drivers, so don't use 3.10 unless you know what you are doing *edit: it is on Linux 3.10 now and 3.10 breaks nvidia 313.30*)
```
[COLOR=#ff0000]# EDIT: do not use this saucy is now on 3.10[/COLOR]
echo -e '\nSource for Saucy Kernel\ndeb http://us.archive.ubuntu.com/ubuntu/ saucy main\ndeb-src http://us.archive.ubuntu.com/ubuntu/ saucy main' | sudo tee -a /etc/apt/sources.list
echo -e 'Package: *\nPin: release a=saucy\nPin-Priority: 100\n\nPackage: linux-generic,linux-firmware,linux-headers-generic,linux-image-generic,linux-libc-dev\nPin: release a=saucy\nPin-Priority: 500' | sudo tee -a /etc/apt/preferences
sudo apt-get update;sudo apt-get upgrade -y
```If you use this you will need to undo it before upgrading to saucy, the files to edit are at the end of the 1st two commands

Other broken sound solution:
In some cases reinstall the audio system can fix it ([[credit]]("http://linuxg.net/how-to-fix-the-no-sound-error-after-upgrading-to-ubuntu-13-04/"))
```
sudo apt-get remove --purge alsa-base pulseaudio
sudo apt-get install alsa-base pulseaudio
sudo alsa force-reload
```

In some cases it may be necessary to use [this ppa]("https://launchpad.net/~ubuntu-audio-dev/+archive/ppa"): ([[credit]]("http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/"))
```
sudo add-apt-repository ppa:ubuntu-audio-dev
sudo apt-get update
sudo apt-get dist-upgrade
```

If your laptop's backlight does not act right and it worked fine on 12.10
you may need to use the [FONT=courier new]acpi_osi='!Windows 2012'[/FONT] boot parameter
```
sudo sed -i "s/quiet splash/quiet splash acpi_osi=\'\!Windows 2012\'/" /etc/default/grub;sudo update-grub;echo 'Reboot to apply'
```
here is the command to undo that, if it makes it worse or does not do anything
```
sudo sed -i "s/ acpi_osi=\'\!Windows 2012\'//" /etc/default/grub;sudo update-grub;echo 'Reboot to apply'
```

---

### Post by linuxman72 on 2013-06-27
I have been having a difficulty with the 3.8 kernel, namely, it will not boot. every time it attempts to boot, it tries, and then says it cannot find "/dev/mapper/gnome-root" and drops to a shell. I can then restart the computer with the reset button and manually select the 3.5 kernel which will boot, but I have been utterly unable too find a way to get 3.8 to boot. Info: I am running 13.04 64-bit, originally installed as 12.10 gnome remix, then manually reconfigured to be normal ubuntu (some traces of gnome remain, like the boot screen) and then upgraded through ubuntu's distribution upgrade tool to 13.04.(I know this is a horrible mess) I am hoping to resolve this without reinstalling ubuntu, as I have compiled a bunch of programs from source and spent a lot of time modifying stuff on this computer. I will reinstall as a last resort.

other lesser issues I would like to fix:

"lock screen" does not work and you can switch between users without entering passwords
the boot screen is leftover from gnome-remix, and I would like to make my computer back into pure ubuntu.

---

### Post by terabyte1 on 2013-07-02
Does KompoZer figure in this work-around? It loads in Precise Pangolin but refuses to load in Raring Ringtail - why? I am building a website and it works on 12.04. I have to use either Bluefish or Quick 'n Easy Web-Builder on Raring Ringtail.. I'm trying out CSS and HTML5 (i used to use HTML4 - but 5's better - and CSS is gee-whizz)! Sigh...! Thanks everyone! terabyte1 ;-D

---

### Post by Donut50 on 2013-10-08
I have had difficulties with having the backlight modes to work instead of just having 3, now i have 10 modes.
Its on the acer aspire one 532h-2db, it was easy to solve though, just install the new intel open source drivers and it works like a charm now.
for the peeps with a slow netbook ubuntu 13.04 gives it a pretty big speed boost as i feel like i really got one :)
and the wifi throws itself off the connection sometimes, and then after a couple of seconds it reconnects.
dont know the fix of the wifi problem :/

---

