---
title: "Excel 2013 and VBA using Ubuntu - possible?"
date: 2020-09-01
forum: General Help
---

### Post by jfca283 on 2020-09-01
Hi, 
I would like to know if It's possible to run excel's macro under ubuntu.
Can I run VBA using just wine? Or I need a Virtual machine in order to comply that?
Using Libreoffice isn't an option, because I need to teach the use of VBA.
Thanks for your time and interest

---

### Post by mastablasta on 2020-09-02
virtual machine or using windows 10 would be best in this case.

Excel has limited functionalities in wine.

---

### Post by dragonfly41 on 2020-09-02
What you can do is write automation scripts which "autopilot" the Excel GUI (instead of using macros).
If the remote pupil is on Windows there are several automation options.
Or perhaps teaching via Google Sheets.

---

### Post by drpjkurian on 2020-09-02
I remember a software known as crossover which allows excel to run in linux.

---

### Post by ActionParsnip on 2020-09-02
Office 365 in your favourite web browser? Will this not work?

---

### Post by mastablasta on 2020-09-03
> **drpjkurian said:**
> I remember a software known as crossover which allows excel to run in linux.
Crossover is wine (modified).

excel 2013 does install and work relatively well in wine. however it will also unexpectedly crash and some of the things inside do not work well. the OP should install and try out the macros.

> **ActionParsnip said:**
> Office 365 in your favourite web browser? Will this not work?

the web version is limited compared to "desktop app". there are no macros in web browser. a few other things are also missing in web version.

---

### Post by jfca283 on 2020-09-03
The virtual machine option it seems the best way. Can you share the window using zoom or any other videoconference app under Ubuntu? Im really new into this of virtual machines and video apps.

---

### Post by mastablasta on 2020-09-03
if they are web based you can do it and they work in any os. Zoom, Teams, Skype and Google meet and few others have web based versions.

some also have desktop clients for linux. Zoom for example: [https://support.zoom.us/hc/en-us/articles/204206269-Installing-or-updating-Zoom-on-Linux#h_adcc0b66-b2f4-468b-bc7a-12c182f354b7](https://support.zoom.us/hc/en-us/articles/204206269-Installing-or-updating-Zoom-on-Linux#h_adcc0b66-b2f4-468b-bc7a-12c182f354b7)

skype for linux comes as deb or snap: [https://www.skype.com/en/get-skype/download-skype-for-desktop/](https://www.skype.com/en/get-skype/download-skype-for-desktop/)
MS teams for linux: [https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-is-now-available-on-linux/ba-p/1056267](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-is-now-available-on-linux/ba-p/1056267)

there are also various others out there.

---

