---
title: "Monitor won't stay asleep after upgrading to 13.04"
date: 2013-07-14
forum: General Help
---

### Post by itsr0y on 2013-07-14
After upgrading to 13.04 from Xubuntu 12.10, my monitor no longer goes to sleep automatically, and if I manually put it in sleep mode via [COLOR=#008000][FONT=courier new]xset dpms force off[/FONT][/COLOR], it clicks back on after 10-15 seconds, though the screensaver remains active the whole time.  I did not have this problem in 12.10.  In Power Manager, On AC, Monitor, I have it set to put the display to sleep after 10 minutes / off after 15.  Any ideas?

---

### Post by maestrobwh1 on 2013-07-15
deactivate your screensaver and see if that resolves the issue.  I have had so many issues with screensavers and power managers conflicting with each other over the years in Ubuntu. I never use the screensaver.  I just let the power manager shut the screen off.  I've actually force removed xsreensaver as a package from all mu ubuntu machines.

---

### Post by itsr0y on 2013-07-15
Wow, worked like a charm.  Thanks so much!  It must have gotten installed when I upgraded to 13.04.

I [asked the question on AskUbuntu]("http://askubuntu.com/questions/313628/monitor-wont-go-into-sleep-mode-automatically-after-upgrading-to-13-04").  Do you want to answer it there so I can give you credit?  If not, I'll just post your solution.

---

