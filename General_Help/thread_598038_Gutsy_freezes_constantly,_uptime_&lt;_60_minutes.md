---
title: "Gutsy freezes constantly, uptime &lt; 60 minutes"
date: 2007-10-31
forum: General Help
---

### Post by AncientPC on 2007-10-31
Alright, I've run memtest for a few hours and it's passed just fine.  My laptop (Dell Inspiron 6000) dual boots and runs just fine in WinXP. However when I boot into Ubuntu with just Nautilus, Compiz, and Pidgin running the system will freeze (typically within 30 minutes) and I'm not sure why.

I've checked dmesg and syslog around the time of freezes but nothing out of the ordinary shows up.

---

### Post by argosreality on 2007-10-31
What video card are you using? Are you using third party drivers? Have you tried disabling Compiz and seeing if that fixes the issue?

---

### Post by AncientPC on 2007-10-31
ATI Radeon Mobile x300, open source ATI drivers.

Ubuntu has seg faulted once during bootup, and it has frozen despite on being on console (boot up into gdm, switch to console 1, run top, it'll freeze eventually).

---

### Post by fitzbag on 2007-10-31
i've got the same graphics card and have exactly the same problem : (

---

### Post by argosreality on 2007-11-01
Does it do the same thing running from the live cd?

---

### Post by AncientPC on 2007-11-01
No.

---

### Post by stillingen on 2007-11-01
There is a bug opened at [**launchpad**](https://bugs.launchpad.net/compizsettings/+bug/108527) for that relates to your problem. 
As an alternative look at this [**post**.](http://ubuntuforums.org/showthread.php?t=584561)
It's how to get Compiz working with the restricted driver.

---

