---
title: "Xubuntu won't boot whenever I boot into windows 10"
date: 2016-02-07
forum: General Help
---

### Post by ash22 on 2016-02-07
I have Xubuntu installed on a drive and windows 10 installed on the other one.  Every time I boot into windows 10, Ubuntu won't boot up. I can only  boot it up after I use the live USB, use boot-repair and restart the  computer, and boot Xubuntu but the problem starts again when I boot into Windows 10. Boot repair doesn't fix the problem permanently and the recovery menu  doesn't help at all. Also, grub shows 2 windows 10 loaders when before there was only one; It shows Windows 10 on sda1 and sda2.

This is the link I got after using boot-repair [URL="http://paste.ubuntu.com/14957058"]http://paste.ubuntu.com/14957058.


[/URL]

---

### Post by thatsallurspaceships on 2016-02-07
Did you try to install alongside w$n partition? If so the grub menu should show both options. Maybe youve just installed another over xubuntu partition. Thats why it is recommended to install ubuntu afterwards. Some Os tend to use whole drive :)

---

### Post by ash22 on 2016-02-07
> **thatsallurspaceships said:**
> Did you try to install alongside w$n partition? If so the grub menu should show both options. Maybe youve just installed another over xubuntu partition. Thats why it is recommended to install ubuntu afterwards. Some Os tend to use whole drive :)

I installed Xbuntu after I installed windows. What's w$n?

---

### Post by ash22 on 2016-02-07
And in the advanced options, there's a long list of "ubuntu generic","Ubuntu recovery", "ubuntu upstart" and only the bottom older ones work and the top ones freeze the computer. Why do I need all of those options and why do some freeze? When trying to boot ubuntu after booting into windows it goes into grub emergency mode and I can't boot it unless I go on upstart but on the bottom of the list of advanced options.

---

### Post by yancek on 2016-02-07
> Reinstall the GRUB of sdc7 into the MBR of sdc

The above from the boot repair output followed by:  Please do not forget to make your BIOS boot on sdc (250GB) disk!

Have you changed the boot priority to sdc where your Xubuntu is?
You also have your windows hibernated which may be part of the problem?

> The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

---

### Post by ash22 on 2016-02-07
> **yancek said:**
> 
You also have your windows hibernated which may be part of the problem?

I've already changed the settings in windows 10 power options and turned off fast boot which should have stopped the drive from being hibernated so I shouldn't get that error. 
Is the boot priority the setting when you switch around the partitions in gparted or is it something done in BIOS? Because I've already made the Xbuntu drive go first in the boot order in BIOS.

---

### Post by yancek on 2016-02-07
> I've already changed the settings in windows 10 power options and turned  off fast boot which should have stopped the drive from being hibernated  so I shouldn't get that error. 

Windows 10 has multiple options to deal with fastboot, fast startup which you can enable/disable.  I don't use it so all I can suggest is you take a look at the various options at the link below for dealing with hibernation.

 [http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

