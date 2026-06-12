---
title: "Slow startup"
date: 2006-09-28
forum: General Help
---

### Post by marianom on 2006-09-28
Hi, I installed a lot of stuff lately (the new kernel, updates for firefox and tb, firestarter, nessus, vmware...).
Now, when I start up my PC it takes at least 20 minutes to let me work, everything is very slow, trying to switch between tb and firefox takes minutes, the mouse pointer moves slow through the screen, I cannot switch between workareas.
All of the sudden, after 15 or 20 minutes everything goes back to normal and I can use the pc as it never happened.

I would like if you guys can advice me where to look (logs, for example) and find out what's slowing me down here.

Thanks a lot and kindly regards.

---

### Post by FuzZy2006 on 2006-09-28
hmmm, i don't know if my advice is good, but, as nobody has answered yet, i'd like to try to help you. There might be some explanations:
         - there are to many programs that start at startup (check system-preferences-sessions-startupPrograms and uncheck the ones you don't need, you may also disable the ones you don't need from system-administration-services)
         - as you may know, the ext3 partition uses a journaling system. this one keeps track of the exchange of files in your computer. it usually runs when you don't use the computer for a while or while you are logged off. if none of these happens - this task runs at the computer startup, which slows down a lot your computer. At least this is the pb I had at the beggining, when I didn't what was all about. My advice is not to shutdown all the time but to log off only and let the pc do it's job. 
          - if you use programs like superkaramba or xgl-compiz, this might slow down your machine if you don't have one that meets the requirements. 

Well, this is all I can help you. Hope you'd solve your pb. Tell us which are your system requirements.

---

### Post by marianom on 2006-09-28
Thanks a lot for you input.

I checked the startup services and they're really minimum. 
I'm controlling the files @ the /var/log and it looks like its the vmware. I just installed it (no windows installed yet) so I'm not using it right now.

Didn't know it would start a service.

---

### Post by markster23 on 2006-09-28
sounds like a hardware problem... did your ubuntu recognize all of ur hardware??

---

### Post by marianom on 2006-09-28
Installed since july: ubuntu never complained about any piece of hardware.

Why do you say so?

---

