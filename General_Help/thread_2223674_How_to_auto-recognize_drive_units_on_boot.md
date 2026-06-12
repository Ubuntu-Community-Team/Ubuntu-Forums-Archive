---
title: "How to auto-recognize drive units on boot?"
date: 2014-05-12
forum: General Help
---

### Post by tassadar2 on 2014-05-12
Hi all, I have a problem with my HTPC based on Kubuntu. 

I have an SSD for the OS and a 2tb drive for files. Everytimes I boot  the computer I have to go to Dolphin file manager and enter on the  secondary drive that appears as a device; this is because it appears  with a red croos icon, and when I enter on it it changes to a green ok  icon.

If I enter XBMC without having done this, I can't access to the content  of this drive, so I always have to enter dolphin and open drive before  opening XBMC.

It's very annoying, so... how can I make kubuntu enable this drive  automatically on every startup? It also happend if a use a USB hard  drive, by default I cant access to it until I open in dolphin.

I want Linux to automount? (not sure if it's the appropiate word) all  units on start and show them with green ok icon instead red cross.

Many thanks in advance

---

### Post by SeijiSensei on 2014-05-12
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by oldfred on 2014-05-12
If automounting now, is it mounting by a label you have assigned to partition? If you create a new mount point will it create issues in your HTPC settings? I have labeled a partition data and mounted it as Data, which are totally different. But for me it was just realizing which was correct.

 Specific example here by Morbius1 for either NTFS or Linux.[URL="http://ubuntuforums.org/showthread.php?t=1983336"]
http://ubuntuforums.org/showthread.php?t=1983336[/URL]
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

### Post by tassadar2 on 2014-05-12
Many Thanks,

I solved this problem in this way:

see systemsettings -> removable devices -> attached drives

for all removable drives:
1) -> enable automatic mounting .........., click preferences
or for only that 1 drive:
2) -> select the usb driv -> click automount on login & automount on attach 

Honestly, I really really can't figure out why this option is not enabled by default.

Regards

---

