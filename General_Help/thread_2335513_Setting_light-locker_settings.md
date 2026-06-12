---
title: "Setting light-locker settings"
date: 2016-08-29
forum: General Help
---

### Post by jjanderson5 on 2016-08-29
I'm running Ubuntu 16.04 and my desktop gets locked out too quickly for me. I would like to increase the timeout time, but I didn't find anything yet that allows me to change the timeout. I ran 'ps' to find running process and I found that 'light-locker' is running. I believe this is the application that is locking out my desktop. Can someone tell me how to modify the light-locker settings?

Jim Anderson

---

### Post by ajgreeny on 2016-08-29
From memory it is in **System Settings** (in the drop down from the cog top right) **->Brightness and Lock**, but I'm not using unity here so not absolutely sure.  I have Ubuntu 16.04 as a VM in VBox so will quickly boot it to make sure I'm right.

Yes, that's where it is and you can set the time from 1 hour down to 1 minute, or if you prefer, Never.

---

### Post by yetimon_64 on 2016-08-29
_*If you have light locker installed*_ (I had to install it manually here in Unity 16.04) press "alt + F2". In the run command box type in "light-locker-settings", without the quotes and press enter (you can also use the command directly in a terminal, but is easier/quicker to use the run command box without a terminal). You should get a window pop up from where you can adjust the settings for light locker. You can adjust the timeout up to 1 hour with the slider or turn off screen locking completely.

Otherwise you can, as ajgreeny notes, just use the system settings and "brightness and lock" to adjust the timeout.

---

### Post by jjanderson5 on 2016-08-29
I had to install light-locker-settings, but once that was done, following your instructions was easy. Thank you.

Jim A.

---

### Post by ajgreeny on 2016-08-30
Great! Please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

### Post by phillip-griffith on 2017-07-27
My light locker (screen saver) settings are controlled by Xfce Power Manager.

---

### Post by wildmanne39 on 2017-07-27
Old thread back to sleep.

---

