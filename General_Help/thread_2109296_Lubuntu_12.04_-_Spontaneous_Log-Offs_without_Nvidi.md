---
title: "Lubuntu 12.04 - Spontaneous Log-Offs without Nvidia"
date: 2013-01-27
forum: General Help
---

### Post by 2CV67 on 2013-01-27
Hi!
I have been using Ubuntu for 6 years on same PC.
Lubuntu since Feb 2012.
12.04 since Aug 2012.
Kernel 3.2.0-35 since 19 Dec 2012.
Kernel 3.2.0-36 since 18 Jan 2013.

Recently, I have had 3 occurences of "Spontaneous Log-Out":
9 Jan 2013 > Double-click to open .jpg file in File Manager > Opens Image Viewer with black center but no image > Find myself at Login screen.
12 Jan 2013 > Exactly same, trying to open a different .jpg file.
26 Jan 2013 > Click to close one of several Tabs in Firefox > Find myself at Login screen.

I searched this topic & found numerous victims with Nvidia graphics, but I don't have Nvidia (ATI RV280 Radeon 9200 series).

Some questions:
1. Any suggestions?
2. Next time it happens, where should I look for diagnostic clues? (/var/log/syslog...  /.xsession-errors?...   somewhere else?...)
3. Likely risks? (apart from loss of unsaved work, of course)
4. Probability of making it better-worse if/when I upgrade to 12.10?

Thanks!

---

### Post by sudodus on 2013-01-27
I run Lubuntu too, with nvidia in a workstation with the proprietary driver suggested by jockey-gtk, and with an old Thinkpad with ATI Mobility Radeon 7500 with the built-in driver. I have not had such issues. Yesterday I had some strange graphics(?) issues though with the terminal window and the web browser. It was OK again after booting from another drive and repairing the file system with

```
sudo e2fsck -f /dev/sdxy
```

where x is the drive letter of the root file system and y is the partition number, typically /dev/sda5

I am not sure it will help you, but it is worth trying.

Another cause of trouble is the graphics driver. Do you use the built-in driver or a proprietary driver?

A third thing to check is the S.M.A.R.T. status of the drive, if it is supported by the hardware. Usually you can get a summary in a BIOS menu, and you can get more details with smartctl (install smartmontools).

---

