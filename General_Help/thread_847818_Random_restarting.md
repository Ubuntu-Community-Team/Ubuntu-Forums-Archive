---
title: "Random restarting"
date: 2008-07-02
forum: General Help
---

### Post by FRed_is_dead_7x on 2008-07-02
Every so often my computer will lock up for a short time and then restart.

I have tried to look up whats wrong but run into problems because I have no idea what the problem is related to, hardware/OS/drivers/specific programs/anything.

So the best I can do is provided as much information as I can and hope someone randomly has some inspiration, so here you are:

-It seems to do this mostly when playing games, or when the processor is under at least medium load.  I haven't seen it do this just sitting at the desktop without any programs running.  But it has done it with every program I use with any frequency.

-This happens with all the programs I run but some more than others. A few it just seems not to like and crashes in seconds every time,others it happily plays for hours, but sometimes crashes on these too. The ones it does well are more processor intensive than most of the ones it doesn't do.

-I just got the computer, and I can't rule out the possibility of hardware/driver problems. Here are some specs: 
       -Asus M50 Series M50Sa-X1 NoteBook
       -Intel Core 2 Duo T9300 2.5G 
       -ATI Mobility Radeon HD 3650

-I have checked the logs but can't find anything that looks bad.  From what I've seen there is nothing logged for several minutes before each crash, but I stopped checking after about four crashes.

I will provide any further information anybody thinks would be relevant.

---

### Post by pytheas22 on 2008-07-02
When the system shuts down, it goes through the normal shut-down process, right?  In other words, it doesn't just shut itself off as if the power had been cut?

Since you say that it occurs when the system is under load, my first guess would be an overheating problem.  Check your BIOS; most have an option where you can tell the system to shutdown after the CPU or motherboard reaches a certain temperature.  Try raising that threshold to see what effect it has on shutting down.

You can also check out [this page]("http://blog.mypapit.net/2008/06/monitor-temperature-from-ubuntu-linux-gnome-applet.html") to install some stuff for monitoring the temperature of various components on the system.  Do you see anything reaching a dangerous temperature?

Also obviously make sure all system fans are working.

---

### Post by FRed_is_dead_7x on 2008-07-02
The power just cuts off and the system restarts.

I have already downloaded that program, my max temp seems to be about 50 C which is not too bad as far as I understand.

I have checked my bios and if it does have a utility for adjusting shutdown temps I can't find it.

I don't really think it is an overheating problem though, because the system runs fine for hours at high loads sometimes. It seems to me that an overheating problem would be more predictable. But then again I might not know anything about that sort of thing.

---

### Post by pytheas22 on 2008-07-03
> The power just cuts off and the system restarts.

In that case, it may not be overheating.  If BIOS were shutting the system down, it should do it gracefully, not with a cold restart.

Maybe it's a power-supply problem.  Does your PSU provide a decent amount of watts to the system?  Even if it does, it could just be a faulty PSU; if possible you may want to swap in a different one to see if it makes a difference.

---

### Post by FRed_is_dead_7x on 2008-07-03
Its a laptop. The battery is at 97% of its manufactured capacity.  And watching the power history as the computer crashes shows no sudden/significant drop in power output. 

It does hang up for a few seconds before it crashes, where it freezes keyboard and mouse input as well as the screen and the sound stutters.  It seems fully powered during this pause.

Thanks for your help so far though.

---

### Post by pytheas22 on 2008-07-03
I don't know what else to look at then.  If you've ever had Windows installed on this laptop (I realize you just got it), did you have problems there?  If not, that would rule out hardware failure.

The only other thing I can think of is to look at the logs.  I know you say you already did, but maybe someone else will see something that you missed, if you post them here.

---

### Post by FRed_is_dead_7x on 2008-07-03
Well here is the syslog.

---

### Post by pytheas22 on 2008-07-05
The last line of your system log, "Machine check events logged," apparently means that something pretty bad happened at a low level of the system, so I suspect that this is related to the crash.  To get more information about the actual events, I guess that you have to install a program called mcelog:

```
sudo apt-get install mcelog
```

This should create a log at /var/log/mcelog containing more information about the crash, which you can open after the crash for more information.  Does it say anything useful?

For more information, google for "Machine check events logged," or check out this [page]("http://support.advancedclustering.com/index.php?_m=knowledgebase&_a=viewarticle&kbarticleid=4").

---

### Post by FRed_is_dead_7x on 2008-07-06
I don't know what this means other than "It's bad."

---

### Post by pytheas22 on 2008-07-06
I don't know exactly what it means either, but I'm guessing that it's hardware defects with the CPU.  It could be your RAM too--you could swap in a different stick to check--but because mcelog only mentions the CPU, I'm guessing that that's the problem.

So I think you should contact your hardware vendor and request a replacement.  If your machine is only a few weeks old and it's had the lockups since day one, obviously it came defective.

I'm sorry this has happened, but good luck.

---

### Post by FRed_is_dead_7x on 2008-07-06
Thanks for your help.

---

### Post by vasiauvi on 2008-08-10
Hi.
I have also an ASUS X51R laptop and I use on this WinXP (but on my PC I have Ubuntu 7.10:))and I have to say that I have the same problem like you.I think that the CPU is the problem.I want to install Ubuntu to see if restarting is happening also with Ubuntu. Now I have the answer.

---

