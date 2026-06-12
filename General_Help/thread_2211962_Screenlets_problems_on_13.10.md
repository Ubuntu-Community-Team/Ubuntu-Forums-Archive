---
title: "Screenlets problems on 13.10"
date: 2014-03-18
forum: General Help
---

### Post by ivaylo.tanev on 2014-03-18
Hello. I recently upgraded to Ubuntu 13.10. I installed screenlets but I have noticed several problems. I am using the Sysmonitor screenlet and it is not showing me any of the networking information. Is there a known fix or a workaround for this? Also the screenlets do not autostart on login. On the 12.4 it used to keep the screenlets icon in the top panel but not anymore. Thank you for your time and help. 
PS: I looked for fixes around the net and nothing worked. If there is no fix for the networking problem I am open for using a different IP indicator. Unfortunately again I could not find anything on the web that works.

---

### Post by gifford on 2014-03-18
I am not sure what network information you are seeking. It is my understanding that the sysmonitor screenlet only shows upload/download. Nothing more about network. What do you mean by IP indicator?
There are several different system information monitors available. Gkrellm is the one I use but there is also Conky.
Also, when opening the screenlets manager and activating the screenlet you choose, there is a checkbox to auto start on login.

---

### Post by grumblebum2 on 2014-03-18
I can install and run screenlets on a clean install of 13.10.
Sceenlets shows an indicator in top panel and autostarts.
The sysmonitor screenlet shows local ip but download rate isn't right.
 
Sysmonitor screenlet is based on conky.
You could run this conky config instead of the sysmonitor screenlet and use much less system resources in the process.
Interested? ....let me know and I'll help to get you up and running.

---

### Post by ivaylo.tanev on 2014-03-20
I am interested. Its exactly what I need. Thank you for the help.

---

### Post by deadflowr on 2014-03-20
> **ivaylo.tanev said:**
> I am interested. Its exactly what I need. Thank you for the help.

You want conky?
If so, then install this
```
sudo apt-get install conky-all
```
this will install all the beginner conky tools you'll need to start with.
As you go along, you can install addtional tools, such as vnstat/curl for network monitoring.
As well as other other stuff, like fonts.

Here's a fun thread, with a really good how-to
[http://ubuntuforums.org/showthread.php?t=1771033](http://ubuntuforums.org/showthread.php?t=1771033)

It might be a little over the top, but you can glean a lot of useful tips, at least for what you want to do.

---

