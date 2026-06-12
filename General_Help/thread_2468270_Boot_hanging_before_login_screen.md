---
title: "Boot hanging before login screen"
date: 2021-10-23
forum: General Help
---

### Post by gjohnz on 2021-10-23
This is on a Dell laptop with Xubuntu 20, and then  21 installed. Xubuntu 20 was installed a week or so ago and initially  worked very well. At some point I rebooted and the system hung before  reaching the login screen. 

I was able to switch to VT's for debugging.

Rather than mess with fixing the actual issue I decided to do a  distribution upgrade via command line. The upgrade was flawless but the  results were the same. The Xubuntu 21 system hung at the same point. In  both cases the last text on the screen was as follows:

[B]Starting Update UTMP about System Runlevel Changes
Finished Update UTMP about System Runlevel Changes[/B]

  The fix, at least in my case, was to install nvidia drivers.
 ```

sudo ubuntu-drivers autoinstall

```
  Upon reboot the Xubuntu 21 system was back to "normal". I was greeted  with the appropriate login screen and was able to login to the desktop.

I'm not asking for help here. I'm more interested in what actually  happened to a system that was working fine without the nvidia drivers  but at some point stopped working until the nvidia drivers were  installed.

[[IMG]https://i.ibb.co/HCW3SHM/Screenshot-2021-10-23-08-14-39.png[/IMG]]("https://ibb.co/HCW3SHM")

---

