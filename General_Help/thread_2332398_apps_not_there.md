---
title: "apps not there"
date: 2016-07-31
forum: General Help
---

### Post by Timothy_Cota on 2016-07-31
I just upgraded to 16.04.  when I click on the apps button I get a message that an update is needed to show some apps, but when I start the update the little spinning circle goes on forever.  In reality, There are no apps at all.  There are only the headings *Featured application, Editors picks, Recommended games and Categories.*They are all empty.  Clicking on the boxes does nothing.

---

### Post by grahammechanical on 2016-07-31
I think that you are talking about the new app store. It is Gnome Software rebranded as Ubuntu Software and it should be considered as still under development.

If you did an online upgrade from an older version of Ubuntu you should still have the old Ubuntu Software Centre installed. And the Dash should be working and there should also be the launcher with icons for File Manager, Libreoffice, Firefox, etc.

If you search for "software" in the Dash search panel you should get an icon for Ubuntu Software Centre as well as Ubuntu Software and also Software Updater. I use Software Updater to update when I am not inclined to update through the terminal.

You may see some improvement to Ubuntu Software after a few updates. I do know that there have been regular updates to the Ubuntu Software catalog. On my 16.04 Ubuntu Software is much more useful than it was 3 months ago. I used it a couple of days ago to install Ubuntu Restricted Extras. It worked ok but it is definitely quirky software.

Regards

---

### Post by CantankRus on 2016-07-31
In the terminal run ...
```
sudo apt update
sudo apt upgrade
```

---

### Post by Timothy_Cota on 2016-07-31
I did upgrade from 14.04 but still no apps.

---

### Post by Timothy_Cota on 2016-07-31
Thanks,  1 bundle was upgraded.  now how do I get it into the app store?

---

### Post by CantankRus on 2016-07-31
Try ...
```
sudo apt install --reinstall ubuntu-software
```

Then reboot.

---

### Post by Timothy_Cota on 2016-07-31
Thanks for the input GRAHAMMECHANICAL.  I expect a lot of bugs for the first 3-6 months but so far I really like 16.04.  I would have waited for awhile but I was having trouble with 14.04.  I had been off linux for a couple of years I tried debian 8 for 24 hours.  It is too soon to talk about it.  I just installed 14.04 a couple of days ago.  It installed without a glitch but when the updating was done and I rebooted I got a message something like "got tired of waiting for (bootloader?)" After a couple of retries I reinstalled 14.04 and then immediately upgraded to 16.04.  Thanks again,  unktim

---

### Post by Timothy_Cota on 2016-07-31
Hooray CantankRus. you **are** the man!  I now have a honey wagon full of software.  unktim

---

