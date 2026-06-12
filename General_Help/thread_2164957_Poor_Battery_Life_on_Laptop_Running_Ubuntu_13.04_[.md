---
title: "Poor Battery Life on Laptop Running Ubuntu 13.04 [PLUS]"
date: 2013-08-02
forum: General Help
---

### Post by shabalabadingdong on 2013-08-02
My Dell Inspiron 1521 has poor battery life running Ubuntu 13.04, with it charged completely, from then on it will only last me about an hour.  I have installed TLP and put it in battery mode (when it's not charging) and ac mode (when it is charging) are these the correct settings?  I don't want to mess anything up.  And also every minute or so when I click the battery icon, it will say 1:24 left, and then another minute passes by and it jumps to a higher time, and then a lower time, what is up?  Do I have to get a new battery?

---

### Post by ajgreeny on 2013-08-02
I can't help in detail apart from letting you know that the changes in the time remaining that show when you click on the power-manager icon occur as a result of the wattage being used at the exact moment you click on the icon, power which varies from second to second.  Use powertop (you'll have to install it first) to see what I mean, and you may also be able to tune your machine to be more power economical.

I am aware of many users believing that batteries drain quicker in Ubuntu than in Windows, but can not help with more details, not having any dual boot machines to do an OS comparrison.

---

### Post by shabalabadingdong on 2013-08-02
> **ajgreeny said:**
> I can't help in detail apart from letting you know that the changes in the time remaining that show when you click on the power-manager icon occur as a result of the wattage being used at the exact moment you click on the icon, power which varies from second to second.  Use powertop (you'll have to install it first) to see what I mean, and you may also be able to tune your machine to be more power economical.

I am aware of many users believing that batteries drain quicker in Ubuntu than in Windows, but can not help with more details, not having any dual boot machines to do an OS comparrison.

Thank you very much. I will install powertop.

---

### Post by richardsdma on 2013-10-21
i also have a inspiron 1521 with ati x1270. the only way to reduce the power consumption very close to windows is to set the frequency of video card to "low". it is a feature of opensource radeon driver that is well hidden. download dhe script and run it as "sudo su"
[https://code.google.com/p/power-play-switcher/downloads/detail?name=PowerPlaySwitcher-0.3.zip&can=2&q=](https://code.google.com/p/power-play-switcher/downloads/detail?name=PowerPlaySwitcher-0.3.zip&can=2&q=)
than, click the "low" option and "applay"......the desktop will flicker one time. this will reduce the power consumption with 2W. 
by default, the power management is disabled.

---

