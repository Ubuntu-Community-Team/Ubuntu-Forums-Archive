---
title: "[SOLVED] Conky"
date: 2008-03-22
forum: General Help
---

### Post by garymc1 on 2008-03-22
I have got conky running all and good but how can get another conky on screen at the same time ??
Thanks
Gary

---

### Post by Oldsoldier2003 on 2008-03-23
> **garymc1 said:**
> I have got conky running all and good but how can get another conky on screen at the same time ??
Thanks
Gary

Why would you want another instance of conky onscreen? or am I misunderstanding your intent...

---

### Post by notwen on 2008-03-23
Here's what I do.  I typically run 3 conkys at all times.  The first for general system info, the second for date/time and the third is for audacious info.  I have made a shell script to run all 3 instances at once.  

```
#!/bin/bash
sleep 20 && conky && conky -c .conkyaud && conky -c .conkytime;
```

sleep 20 makes my system wait 20 seconds before executing my conky commands.  conky will launch ym default .conkyc in my home folder, conky -c .conkyaud will launch my conky for audacious, conky -c .conkytime will launch my conky for time/date.  To make a shell script simply make a empty document, lets name it, conkystart.sh  --- paste the above code into it, renaming/removing any configs you don't want to include, save it, then be sure to give it executable permissions.  Post back if you need any help.  Hope this was useful.  =]


Here is a my current screen and conky setup for reference:
[URL="http://www.notwen.org/img/uf_mar20_08.png"][IMG]http://www.notwen.org/th/th-uf_mar20_08.png[/IMG]
[/URL]

---

### Post by kaivalagi on 2008-03-23
Nice config, I have just installed Conky for the first time and have started playing....how did I miss this app!

By any chance could you share your conky config files to give me a head start into understanding what can be done? 

Alternatively is there a good place to go to read up on conky integration people have done other than the conky sourceforge website? 

Thanks

---

### Post by kaivalagi on 2008-03-23
Forget my request, I've had a good play around with Conky and I have got a good understanding now...

I only wish now that there is more support for other music players, such as rhythmbox and listen...I guess time will tell

---

### Post by garymc1 on 2008-03-24
Thanks notwen got it working now

thanks again
gary

---

