---
title: "CPU 100%, whats the problem?"
date: 2006-11-08
forum: General Help
---

### Post by Green_Star on 2006-11-08
Till yesterday my ubuntu edgy was working fine, but today when i started i found my cpu was running at 100%, I am not running any xgl or beryl. i tried to find out which program is taking that much  of processing power, but i could not find please check the screen shot of 'top'. Can any one tell me what is the problem and how i can solve this.


.
Thanks in advance.

---

### Post by OffHand on 2006-11-08
I'm pretty sure beagle is doing this. It's a known bug.

---

### Post by Green_Star on 2006-11-08
what is beagle, how can i resolve this?

---

### Post by Linux O)o_O7 on 2006-11-08
I won't be trying to install a new theme in a hurry - is trashed my Linux completely. probably something I did wrong. Still - I believe they need to come in packages one click install.

My CPU is at 97% caused by Nicotine right now was not the case but it is now with the clean Ubuntu install.

---

### Post by OffHand on 2006-11-08
> **Green_Star said:**
> what is beagle, how can i resolve this?

Beagle is ubuntu's search engine. if you go to System > Preferences > Sessions and pick the tab Startup Items do you see beagle or beagled in the list?

---

### Post by Green_Star on 2006-11-08
Thanks for your help. I checked my start up session, but I didnt find any think like that, please check my screen shot.

..
[IMG]http://img490.imageshack.us/img490/7082/screenshotsessionsmx7.png[/IMG]

---

### Post by fragos on 2006-11-09
Your top display only shows about 6% CPU.  The numbers will change as tasks execute.  The only heavy CPU I've seen is when runing tvtime but the culprit is xorg.

---

### Post by handy on 2006-11-09
Have you tried looking at:

***Menu:* System / Administration / System Monitor - *Tab = Processes***

Then check the **% CPU** column to see what exactly is using the cpu?

---

### Post by Rui Pais on 2006-11-09
I have a problem of 100% cpu too.
In my case it was hald-addonn-storage, a deamon that auto mount storage devices or something like that. 
It froze at 100% every time there is no CD on cdrom drive (most of the time). 
My only solution was disconnect that drive :( - i hardly use it, except for installing system.

You should keep top running until the culpit, the 100% one, appears.

---

### Post by Green_Star on 2006-11-09
Please check the System monitor screenshots. I didnt find any process which is taking that lot of CPU. 

But any way if some process taking that lot of CPU why it is not showed up in my top or system monitor list?

I hardly can use my Ubuntu now because of this problem, i can not open any program, because it is taking hell lot of time because of this CPU issue.

Any idea to resolve this?


[IMG]http://img353.imageshack.us/img353/7179/systemmonitor1gt4.png[/IMG]..


..
[IMG]http://img353.imageshack.us/img353/5816/systemmonitor2ew9.png[/IMG]

---

### Post by Green_Star on 2006-11-09
Finally it is resolved, I donno how it was fixed but i can explain what i have changed. 

In my sources.list there are some repositories pointing to Dapper, but now I moved to Edgy, so I commented out those lines, rebooted, now every thing is fine. Even with those lines uncommented after I moved to Edgy it is working fine, but it started all of sudden day before yesterday.

My question is why Ubuntu is not able to give the process name which is taking lot of CPU?

---

### Post by fragos on 2006-11-09
That disparity is really wierd.  I would question the Resources display.

---

### Post by papparainen on 2006-11-16
Here seems to be the problem:
[https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/54684](https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/54684)

---

