---
title: "ThinkPad Fan Always On"
date: 2006-11-03
forum: General Help
---

### Post by Sethro on 2006-11-03
Hi everyone I posted a topic earlier and no one seeemed to wanna help me out](*,) 

I have a IBM ThinkPad T43 and I just installed Ubuntu 6.10 , Ive searched the forums alot and so far I have'nt found a solution to the fan always on and blowing out cold air. It kills my battery and makes alot of noice too.

Please help me out

one ubuntu user to another

---

### Post by giorgione on 2006-11-06
Hi, 
I have a Thinkpad T60p with Edgy and I experience the same problem. The fan is running the whole time. I would be very interested in an solution to this problem as well. Thanks.

---

### Post by Sethro on 2006-11-06
> **giorgione said:**
> Hi, 
I have a Thinkpad T60p with Edgy and I experience the same problem. The fan is running the whole time. I would be very interested in an solution to this problem as well. Thanks.

Yeah and also did you get Bluetooth to work?

---

### Post by Jingo on 2006-11-06
I have a T42, and the fan is only running all time when on ac. On battery its much better.
The problem is wellknown on [http://thinkwiki.org](http://thinkwiki.org).

Install sensors-applet to monitor you temp from your systray. I found fan always on due to GPU (radeon 7500) never cools off.

Remember to enable dynamicClocks in xorg.conf.
Use rovclock(not in repos, but easyli compiled) to underclock you radeon gfx.

---

### Post by Sethro on 2006-11-06
> **Jingo said:**
> I have a T42, and the fan is only running all time when on ac. On battery its much better.
The problem is wellknown on [http://thinkwiki.org](http://thinkwiki.org).

Install sensors-applet to monitor you temp from your systray. I found fan always on due to GPU (radeon 7500) never cools off.

Remember to enable dynamicClocks in xorg.conf.
Use rovclock(not in repos, but easyli compiled) to underclock you radeon gfx.

Right will try the fixes you posted, and also did you have a biometric fingerprint scanner and bluetooth. If so did you get them to work?

---

### Post by kkinder on 2006-11-06
I assume it's because by default it tries to keep the system cool when plugged in. It's a hardware thing.

I have a T41, and my fan is also usually on when plugged in, but with the slow speed. I'm not aware that it causes much undue wear, as those fans are really built to last.

But it is noisy and does drain your battery.

---

### Post by apelete on 2006-11-06
I have exactly the same problem on a Thinkpad X60, even though there is no dedicated graphic card.
There seems to be some problems with Duo core family's frequencies control. Hope there will be a patch soon in one of the next kernels...

---

### Post by apalacheno on 2006-12-06
Have a look at [ThinkWiki]("http://www.thinkwiki.org/wiki/Problem_with_fan_noise"). There is no real solution yet, but there are possible hacks.

Cheers,
apalacheno

---

### Post by Roger Mudd on 2007-04-27
Sorry to revive a dormant thread, but I'm having the same problems with the fans on my T42. I am curious as to what temperatures you were seeing with your Thinkpads. Using lm-sensors and sensors-applet I'm getting CPU temps in the high 40s and low 50s (Celsius) and GPU temps hovering in the mid 50s. This is while plugged into a power source.
I don't think it's a huge issue. According to [Intel]("http://processorfinder.intel.com/details.aspx?sSpec=SL6N5#"), the "thermal specification" is 100 Celsius. I've never seen it get close to that.
I guess the fan noises are just a minor annoyance, but it would be nice to have a solution.

---

### Post by Wulfrunner on 2007-04-30
I have a brand new T60p and I experience the same problem--somehow windows is able to regulate the fan so that it does not go on unless it is working hard. I had Gentoo on here for a while and even when underclocking the GPU (aticonfig --set-powerstate=1), setting the cpufreq to powersave, and *turning off* one of the CPU's, the fan still came on. This problem is not so bad with Feisty, the fan still comes on way too much, but there are actually times when it is off (like when I have just turned it on). 

I suspect that the problem comes from two things: 
1) The system is not using the entire range of ACPI control for all devices; this is clear from the high temperature and the battery life (which is 75% of that in Windows) 
2) The trigger points for fan activity are set too low (cat /proc/acpi/ibm/thermal  -- the first number is the CPU the fourth is the GPU for me)

---

### Post by ScarletPimpernell on 2007-07-17
I just installed 7.04 on my thinkpad T42 and the fan is still a problem. It's really quite annoying.

Has there been a working fix to this yet?

---

### Post by doog519 on 2007-07-17
I had a R40 with the same problem.
I ended up installing Suse 10.2 and that was the end of my fan problems.

I am still running FF on my Dell laptop without any problems.

Not trying to promote Suse but it was a quick fix for me. I just didn't have the time to figure the fan problem out.

---

### Post by ScarletPimpernell on 2007-07-17
Thanks doog,

Yeah it is quite disconcerting that Ubuntu doesn't deal with this issue 'out of the box'.

The reason I bought a thinkpad T42 in the first place was due to the encouraging feedback regards thinkpad's and their compatibility with Ubuntu, on this forum.

I would appreciate it if anyone who has encountered, and fixed this particular problem with Ubuntu would be kind enough to point me in the right direction.

---

