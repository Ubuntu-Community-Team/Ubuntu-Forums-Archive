---
title: "Ubuntu 22.04, “battery plugged in” icon suddenly disappeared."
date: 2023-05-01
forum: General Help
---

### Post by Advait on 2023-05-01
Newbie here.

I&#8217;m running up to date Ubuntu 22.04 ext4 Gnome Wayland on a MSI Bravo 15 AMD Ryzen 7 4800H laptop. Earlier today the little &#8220;battery plugged in&#8221; icon suddenly disappeared from my little battery icon. So I checked my charging cable and it&#8217;s providing a stable solid 19VDC. 

For fun I opened my Virtual Box and then opened a Windows 10 VM. The battery icon in the Windows VM shows plugged in as normal. But the Ubuntu host battery icon shows not plugged in. It&#8217;s been about 2 hours and the battery shows no drain. It&#8217;s staying solid at 93% charge with no drain. So something caused the little &#8220;battery plugged in&#8221; icon to disappear from my Ubuntu 22.04 host.

My Ubuntu 22.04 VM also shows no &#8220;battery plugged in&#8221; icon. But the Windows VM does show the &#8220;battery plugged in&#8221; icon.

The problem persists after multiple reboots. I also ran Software Updater. No effect.

Any ideas why my &#8220;battery plugged in&#8221; icon has disappeared?

Is there a terminal command that shows whether or not the power is plugged in?

---

### Post by Advait on 2023-05-02
bump

---

### Post by aljames2 on 2023-05-02
Have you tried connecting & disconnecting (or vice versa) the power cord, to see if the power indicator refreshes?
Some  of the info here may also give some clues:  [https://askubuntu.com/questions/1317600/top-menu-battery-indicator-not-showing-correctly](https://askubuntu.com/questions/1317600/top-menu-battery-indicator-not-showing-correctly)

---

### Post by Advait on 2023-05-06
> **aljames2 said:**
> Have you tried connecting & disconnecting (or vice versa) the power cord, to see if the power indicator refreshes?
Some  of the info here may also give some clues:  [https://askubuntu.com/questions/1317600/top-menu-battery-indicator-not-showing-correctly](https://askubuntu.com/questions/1317600/top-menu-battery-indicator-not-showing-correctly)

Yep, tried disconnecting and reconnecting the power cord. Doesn't fix the issue.

I followed the link but the issue there is different from my issue. Any ideas how to get the plugged in icon to come back?

---

### Post by Advait on 2023-05-24
The "battery plugged in" and "battery charging" icons are back. Don't know why. Maybe some update fixed it.

---

