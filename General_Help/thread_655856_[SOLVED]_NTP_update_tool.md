---
title: "[SOLVED] NTP update tool"
date: 2008-01-01
forum: General Help
---

### Post by zhimsel on 2008-01-01
Hey guys,

Does anyone know of a simple tool (preferably something over SSH, X forwarding is okay) that can update the system time with an ntp server? I have an Ubuntu server I remotely manage with does not a run a GUI. I connect over SSH and would like to keep the time correct.

---

### Post by g2g591 on 2008-01-01
ntpdate ? for easy searching for programs in the repositories, use apt-cache search queryhere

---

### Post by IcemanV9 on 2008-01-02
Here's a very good [[COLOR="DarkOrange"]wiki[/COLOR]]("https://help.ubuntu.com/community/UbuntuTime?action=show#head-336ef694a54320282b887818e67d1b340da792ef") on time synchronization.

---

### Post by g2g591 on 2008-01-02
I agree, that wiki page is an excellent source of info. Now to convert info to KDE commands...  same first steps, in right clicking the clock and selecting adjust date time, but kubuntu users won't get a nice helpful dialog that will install ntp or ntpdate, you/they must manually install with adept or apt-get, other than that, just select a server from the drop down list

---

