---
title: "Problem with CPu temperature"
date: 2006-08-13
forum: General Help
---

### Post by unrue on 2006-08-13
Hi, i have Asus M67432NEUh laptop, and i have a problem with temperature of CPU Centrino. Under Xp, temperature reached 90-105° under gaming. I suppose that this temperatures are normal, because i hadn't any problem in two years who i use this laptop. Under Linux instead (Ubuntu 6.06 Live), when CPU temp reach 105 °,  the system shut down and i can't install Ubuntu. In trip_points file , the critical shutdown temperature is 105° in fact . I tried to change this, whit command line 

echo -n "120:0:90:70:0" > trip_points 

but after few minutes, the critical shut down temp  return to default value. How can i change values into trip_points forever? Another question: which temp shut down system under XP as neither 105° are sufficient for system this?( Sorry for my english, i'm Italian :) )Thanks.

---

### Post by em3raldxiii on 2006-08-13
Hi unrue,
 
This would definitely be a pain-in-the-neck, that is for sure. Here are my thoughts on the matter.
 
If your laptop computer really is running over 100C, this is too hot and will likely cause damage to your computer eventually. There are a number of reasons why it may be getting this hot. 
 
A) The heatsink or chassis fan may have failed so it can no longer clear out the heat (your monitoring program would show a high case temperature in this situation), 
 
B) The thermal paste between your CPU and your heatsink may have failed - either through melting and leaking out, drying out, or some other internal chemical failure.
 
C. The thermal diode that senses the temperature of the CPU may be faulty. If you suspect this is the case, you may be able to disable it in the BIOS. I don't know how to change the settings in Ubuntu, though. On the other hand, this might be a good time to take the computer to a reliable servicing department for a thorough servicing and upgrade.
 
D. Your chassis may be heavily soiled with dust and other debris inside that is preventing the airflow from adequately cooling the cpu and other components. Opening it up and using an approved compressed air canister to blow out dust may solve this problem.
 
There may be other issues that other folks here can clarify.
 
It should be noted that temperatures this high can be damaging to some parts of your computer, not just your CPU. Memory, for example, is sensitive to very high temperatures and you can have data loss while the computer is running (often manifesting as lock-ups & hangs). Your graphics processor can overheat (often manifesting in strange "artifacts" or other unusual graphical effects, particularly when gaming). Your hard-drive can have serious problems, but most often it just speeds up the regular wear & tear on the drive leading to premature hard-drive death. So it is in your best interest to just make sure that your computer is not suffering from serious overheating issues. Once you have comfortably ruled this out, you can modify the auto-shutdown temp thingie with a clean conscience.
 
Good luck!

---

### Post by unrue on 2006-08-13
Hi, thanks for your response. I think that these temperatures  aren't true. If I touch under laptop when signed 100° isn't too hot. If i really worked for two years whit 90-100° , my laptop was died :) I dont' understand why Windows XP don't shut down system when laptop reach 100° . As well, i tried Speedfan program, for monitoring CPU temp. This program sign more 9° than ACPProbe, the official program for CPu temp. I'm confused ](*,)  In many cases, CPu fan start after only two minutes since i start work. It is impossible who the CPu temp have reached 90° after two minutes !! In my opinion, these temperatures are wrongs, possibly for thermal diode breaking.

---

### Post by htmlguy716 on 2006-08-13
> **unrue said:**
> It is impossible who the CPu temp have reached 90° after two minutes !! In my opinion, these temperatures are wrongs, possibly for thermal diode breaking.
It is very easy for a powerful processor to reach alarmingly high temperatures (80°C or up) in a matter of seconds or minutes if there is a cooling failure, without the case feeling very hot. However, if this reading is acually 90°F instead of 90°C, then you are probably in the clear. 90°C is equivalent to 194°F, so it is important to get the correct units.

---

### Post by unrue on 2006-08-13
Many times,CPU fan start when operative system is booting. This suggest who Ubuntu have a bad control of temperature(in my laptop, not in general). If really possible reaching 90° C in this situations? (Celsius, not fahrenheit  :o  ) Whend Xp is booting, CPu fan don't start. If i really have temperatures problems, the CPU fun must start under Xp, but not start. Why?

---

### Post by Dropknee on 2006-08-13
I got this problem too under Ubuntu 6.06, the OS dont monitor my temp like WinXP, in WinXP the fan sensor work, for example: When my CPU reach 45° the fan start to raise the RPM to try the normalize the temp.

Anyone know a good fan sensor program??? Because right now I have the fan at max RPMs and are very loud.

Pls help here too

---

### Post by em3raldxiii on 2006-08-13
This is a very interesting (and obviously vexing) problem.  If I get a minute when I am home from work, I will see if I can help you find a solution.  If you figure something out, don't forget to tell us! :D

---

### Post by sfish on 2006-08-18
I have aproblem, not concerning ubuntu, but it is about strange temperature values. Well, I dont know, whether these values are strange, but... My Pentum M 730 (in my Acer notebook) is on 47-48°C when it is idle, but when I begin doing something, when I start application or so, temperature increase to 58-60°C - in 1 second! Is it possible at all? This amount of  increase in such little time? It lasts only last 3 days  - before it was ok. Before that time, my fan ran normally, from time to time it started to blow. But now it starts and stops, starts and stops...it is very disturbing. The blows according temperature values probably, but as I said these values are very strange on my opinion. Have anyone any idea whats wrong? Maybe something with sensors...but I really dont know. Thank you for any answer.
(and sorry for my english...)

---

