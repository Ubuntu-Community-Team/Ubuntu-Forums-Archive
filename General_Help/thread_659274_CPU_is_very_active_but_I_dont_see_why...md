---
title: "CPU is very active but I dont see why.."
date: 2008-01-05
forum: General Help
---

### Post by mohamad on 2008-01-05
I'm using ubuntu for a while now and I am getting the feeling that it is becoming slower and slower every day, from boot up till shut down.
One of my big problems is that now and then my CPU-History gets crazy from what I can see in System Monitor and from what I can hear from my CPU-fan going at a higher RPM. 
But then when I look into all processes, I don't really see any process eating up CPU speed so I can kill it. The highest would be gnome-system-monitor at about 6% CPU, which is normal I think. 

So how can I find out whats eating my CPU speed so bad. It just happens without any reason at all, just surfing the net and then at once it begins, sometimes stops after 15 minutes and sometimes I have to shutdown (just loging off and on won't help)

thnx

---

### Post by Craigus on 2008-01-05
Open a terminal and type [COLOR="RoyalBlue"]top[/COLOR]

You will see what processes are using CPU resources.

---

### Post by mohamad on 2008-01-05
Great thnx it worked! I saw a command pdftotext that was taking about 90% that I didnt see on System Monitor. I couldnt do "killall pdftotext" because it showed up again so I killed trackerd and that worked. Thnx alot

---

### Post by Alekcander on 2008-01-05
for me it's the same, but even if I kill trackerd, it keeps eating my cpu for over 93%
its very strange, I must say I did a reinstall today and instead of doing update , I did dist-upgrade, ....???
the only thing that is possible is to renice trackerd and give it a very low level, so that other applications can push it away for a bit.
:(

---

### Post by fjgaude on 2008-01-05
Once Tracker has indexed the files it defaults to indexing it quiets down and really has little activity after that. That's hours to do it after first installing. That's been my experience with Tracker. I find it very useful.

---

