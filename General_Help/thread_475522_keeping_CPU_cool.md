---
title: "keeping CPU cool"
date: 2007-06-16
forum: General Help
---

### Post by milan_koko on 2007-06-16
I'm migrating from Windows XP to Ubuntu desktop but am having some trouble with cpu overheating. It has been that way since the day I bought it so I don't think anything should be replaced(i.e. cooler). 

I solved problems with overheating in WinXP with a program called CpuIdle. You can read [here]("http://www.cpuidle.de/works.php") what it does. Now this nice program keeps my CPU temperature at 55 degrees Celsius in summer. If I should turn it off it would go up to 90 degrees or even more.

And here is the problem. I need an application like that to run linux or my CPU is going to fry itself. I installed lm_sensors and it goes to 90 degrees in 5 minutes, even if I don't run any applications but gnome. The readings are accurate, I checked in BIOS. Now as I understand from web [page liked above]("http://www.cpuidle.de/works.php") , this should already be implemented under linux and running all the time. But it obviously isn't working for me. 

> Modern operating systems like Linux execute the HLT instruction in an idle priority thread. This thread is always executed when the CPU is otherwise idle. No additional execution time for HLTing is needed, the CPU will not run slower.

While other operating systems like Linux always used this mechanism, Windows only learned it with NT. But even with NT and following versions it is only enabled when the BIOS and ACPI implementation is recognized by the OS.

My hardware specs: 
cpu: AMD AThlon XP 1800+ 
mb: Abit KX7-333

Can anybody help me?

shor version: I need a program that will issue a HLT command while I'm not using cpu. Probably needs to have special support for VIA KX chipset.

---

### Post by trippinnik on 2007-06-16
Did you build it yourself?  There are some ways in linux to control the temperature but they work better for laptops or processors with frequency scaling.  Even thought your PC has been over heating since you got it, you should really find out why it's getting so hot.  I had an Athlon XP die because it started overheating, the heatsink was clogged with dust.  Really you should just try a nice powerful heatsink fan and put some silver stuff between the CPU and the heatsink.

---

### Post by energiya on 2007-06-16
> **milan_koko said:**
> 
Now this nice program keeps my CPU temperature at 55 degrees Celsius in summer. If I should turn it off it would go up to 90 degrees or even more.

My hardware specs: 
cpu: AMD AThlon XP 1800+ 
mb: Abit KX7-333


:shock::shock::shock::shock::shock::shock::shock: 55-90 dregrees Celsius?!?!
I have a Athlon XP 1700+ and it now rates at 25 degrees and my room temperature is 30. In winter I get about 14-17 degrees Celsius. I use [http://tldp.org/HOWTO/Athlon-Powersaving-HOWTO/approaches.html#commandline](http://tldp.org/HOWTO/Athlon-Powersaving-HOWTO/approaches.html#commandline) to get theese low temps. Without it I get about 34 degrees (I turned power saving mode off when I started writing this).
For you it should be (well, for KX133 actualy, but maybe it works for KX333 ?)
> 
enable: setpci -v -H1 -s 0:0.0 52=$(printf %x $((0x$(setpci -H1 -s 0:0.0 52) | 0x80)))
disable: setpci -v -H1 -s 0:0.0 52=$(printf %x $((0x$(setpci -H1 -s 0:0.0 52) & 0x7f)))

but if you're not a console junkie you could try Athcool or coolrun (I just put the one for my KT600 to be executed at startup).

Your CPU is way to hot !!!

---

### Post by mcduck on 2007-06-16
> **milan_koko said:**
> I'm migrating from Windows XP to Ubuntu desktop but am having some trouble with cpu overheating. It has been that way since the day I bought it so I don't think anything should be replaced(i.e. cooler). 
Well, that tells everything important. You definitely need to check that the cooler is correctly installed and clean. And probably need some better cooling for your CPU or your case.

With normally working cooling CPU will never overheat, not even running at 100% use for weeks. Overheating is always a sign of some problem, and if it has happened from the day you bought the machine there must be something wrong with the way the machine was put together.

---

### Post by milan_koko on 2007-06-16
I have a weird positioning inside the case. It's quite an old case. There is no airflow and hot air from power supply goes directly into CPU cooler. I will remove it and put on a new paste, but I don't think that's the problem here.

After some research I too found out same things you wrote energyia. Now it's running on 45 degrees and i'm satisfied:p

---

### Post by hessiess on 2007-06-16
> There is no airflow and hot air from power supply goes directly into CPU cooler

get a bigger heatsinc, and a new case. no wonder its overheating if the hot air from the psu is going onto the cpu heatsink!

take the side of your comp and put a desk fan pointing into it. this should fix the problem, and alow you to use 100% of your cpu

---

### Post by milan_koko on 2007-06-16
yeah that would help, but I can't work this way. It has to be neat:D

---

### Post by hessiess on 2007-06-17
it would work temperely....:)

---

