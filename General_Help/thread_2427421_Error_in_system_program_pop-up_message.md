---
title: "Error in system program pop-up message"
date: 2019-09-22
forum: General Help
---

### Post by plutobuntu on 2019-09-22
My OS is Xubuntu and I've been having an issue, every time I log into the pc it displays a pop-up message that says something like "there's an error in a system program" (I'm translating from my language). It also pops-up very rarely on seemingly random moments.

The pop-up gives the option to cancel or to send a report. If I click report, it always goes away and doesn't show anything at all.

How do I go about fixing it? Should I reinstall Xubuntu?

---

### Post by Skaperen on 2019-09-23
show us the output of this command entered on a terminal shell: [COLOR=#0000cd][FONT=courier new]** ls -l /var/crash**[/FONT][/COLOR]

---

### Post by plutobuntu on 2019-09-23
> **Skaperen said:**
> show us the output of this command entered on a terminal shell: [COLOR=#0000cd][FONT=courier new]** ls -l /var/crash**[/FONT][/COLOR]

Here:

> ls -l /var/crash
total 82136
-rw-r----- 1 username whoopsie 84106617 sep 23 06:49 _usr_lib_x86_64-linux-gnu_tumbler-1_tumblerd.1000.crash
-rw-rw-r-- 1 username whoopsie        0 sep 23 06:50 _usr_lib_x86_64-linux-gnu_tumbler-1_tumblerd.1000.upload

---

