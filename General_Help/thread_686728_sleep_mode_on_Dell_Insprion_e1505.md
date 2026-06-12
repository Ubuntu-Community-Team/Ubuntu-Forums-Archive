---
title: "sleep mode on Dell Insprion e1505"
date: 2008-02-03
forum: General Help
---

### Post by JohnnyBoy022 on 2008-02-03
I'm trying to get suspend to work on my dell inspiron e1505 laptop with Ubuntu 7.10 running off of an **external** hard drive.

Right now when I try to suspend the screen goes black, and the hard drive never turns off (is it supposed to in suspend?)

When I press the power button to try to come out of suspend, absolutely nothing happens. Anyone know where to start, commands, things to try?

---

### Post by JohnnyBoy022 on 2008-02-03
anyone?

---

### Post by pointone on 2008-02-04
I was able to solve the problem by [upgrading to the latest version of the ATI driver]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide") and editing /etc/default/acpi-support, changing POST_VIDEO=true to false and SAVE_VBE_STATE=true to false.

---

