---
title: "Recurring problem launching some apps after upgrade"
date: 2014-05-18
forum: General Help
---

### Post by Paul_Jewell on 2014-05-18
I decided to take the plunge last week after learning that the next LTS release was out. I upgraded through with the dist upgrade tool all the way from 12.04 to 14.04. There were a lot of other issues, mainly with compiz and lightdm, but I have those sorted now. An issue which has happened many times, but I can not yet see the pattern which causes it, is an issue where some apps will not launch at all. I have had the issue with nautilus and bresero. Clicking on the launcher for them, they do the slow loading flash for a little while then just stop. From terminal I only get one error output: '[COLOR=#000000]Could not register the application: Timeout was reached'. Restarting or killing X fixes. Launching the apps from terminal with sudo also works, but sometimes this causes other issues. 

Ubuntu 14.04 32bit
Lenovo/IBM thinkpad T60

Let me know if you have any suggestions. [/COLOR]

---

### Post by pfeiffep on 2014-05-18
Symptoms were somewhat similar on my Dell install (specs in signature) I had disabled some startup apps ( one or two TOO many) once 'PolicyKit Authentication Agent, and Certificate and Key Storage were re-enabled to autostart my symptoms were alleviated (read I shot myself in the foot ;-) )

---

### Post by Paul_Jewell on 2014-05-18
I don't remember disabling any of these, but do you know where I should check anyway?

---

### Post by pfeiffep on 2014-05-18
I'm not certain where exactly to tell you to look on Unity - check for startup applications.  I took an [extra step]("https://help.ubuntu.com/community/ShowHiddenStartupApplications") of unhiding all the startup applications - if you didn't do that you probably don't have to worry.

---

### Post by Paul_Jewell on 2014-05-20
The issue happened again today, this time with document viewer. (I was not sure of the process name for this so I did not run it in terminal)

---

