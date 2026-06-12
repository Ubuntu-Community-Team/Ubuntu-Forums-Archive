---
title: "ubuntu 14.04, fan always on"
date: 2014-04-20
forum: General Help
---

### Post by KillEmAllx on 2014-04-20
Hi forum, I just did a fresh install of Ubuntu 14.04 on my Asus Zenbook UX32A, and it runs good. The only problem I seem to have, in comparison to 13.10, is that the fans run almost all the time, like nonstop, even when not doing a lot. I've installed both TLP and CPUfreq, and can't really say if it helps since it's one of the first things I do when doing a fresh install. I just hope they do their job.

I have two questions:

1. Is there any tool to control the fans? I'd like to control at what temperature they should run, right now they run all the time and my laptops CPU runs at an average of 48[COLOR=#545454][FONT=arial]°[/FONT][/COLOR]C, which I think is pretty normal and no reason for the fans to go nuts (I check this with Psensor).

2. Is the CPUfreq indicator compatible with TLP? Could this be the cause of my problem? I want to be able to change battery-modes to PowerSaving or Conservative, and that's what CPUfreq does, just don't wanna mess anything up by installing it alongside TLP.
EDIT: I've unninstalled CPUfreq just to see if it helps with the fans but nope, same thing. I've installed it again, alongside TLP.

If you have any other tips for battery saving, they're more than welcome.

Thanks in advance.

---

### Post by trag on 2014-04-20
Do you have AMD graphics?

---

### Post by KillEmAllx on 2014-04-21
Nope, Intel HD Graphics 4000...

---

### Post by Tobios on 2014-04-28
Hey,
I have exactly the same problem with my ux32a and Ubuntu 14.04.
Have you found a way to solve the problem ?
I've tried to control the fans, but it doesn't work, I think we cannot control the fans with a software.
Maybe there is a kernel patch to solve the problem ?
Thank's.

---

### Post by Tobios on 2014-04-28
I found that but I didn't understand well how to use it : [http://forum.notebookreview.com/asus/705656-fan-control-asus-prime-ux31-ux31a-ux32a-ux32vd.html](http://forum.notebookreview.com/asus/705656-fan-control-asus-prime-ux31-ux31a-ux32a-ux32vd.html)

---

### Post by KillEmAllx on 2014-04-29
Yes I've found that too but I don't really get it either.
My fan runs almost all the time now.. I'm using TLP and CPUfreq (set to conservative, sometimes on powersave), but the fans run all the time. They turn on and off and on and off... Really annoying...
Anyone, please help...

---

### Post by Tobios on 2014-05-02
The problem is solved for me since I've installed indicator-cpufreq. 
I actually don't know why, and when I set the max power ( 1,40GHz ), the fans are not turning at theire max speed.

Have you found something ?

---

### Post by KillEmAllx on 2014-05-14
Nope, fans still run like crazy.. Do you have both TLP and CPUfreq? I'm thinking if installing is the cause of this bug...

---

### Post by Ubi_one_2014 on 2014-05-14
sudo apt-get install i8kutils

read [http://www.cyberciti.biz/faq/controlling-dell-fan-speeds-temperature-on-ubuntu-debian-linux/](http://www.cyberciti.biz/faq/controlling-dell-fan-speeds-temperature-on-ubuntu-debian-linux/) as well

---

### Post by KillEmAllx on 2014-05-21
> **Ubi_one_2014 said:**
> sudo apt-get install i8kutils

read [http://www.cyberciti.biz/faq/controlling-dell-fan-speeds-temperature-on-ubuntu-debian-linux/](http://www.cyberciti.biz/faq/controlling-dell-fan-speeds-temperature-on-ubuntu-debian-linux/) as well

Thanks but isn't that just for Dell laptops?

---

### Post by Robert_Hubbard on 2014-05-26
Has anyone found a solution to this issue?

---

### Post by twu026 on 2014-06-16
I am using the ASUS UX32VD with Ubuntu 14.04 LTS. 

So apparently this model of laptop lacks the sensor feedback required for fan control by the kernel. This results in a very noisy fan that seems to be ON most of the time!

I found a 'hack' C program ([http://www.linlap.com/asus_ux32vd]("http://www.linlap.com/asus_ux32vd")) which works OK for me so far. Using the parameters suggested by the program author, my fans run very quiet and the system remains cool.

Just do a search for 'fan' in the **comments** section near the end of the webpage and you will find a pastebin link to the C source code. Instructions to compile the source code to an executable is in the comments of the source code.

Disclaimer: Like the author of this program says,** use at your own risk!** I've only just started to use this program myself so am a bit paranoid about overheating. I pop open xsensor every now and then to check the temperature just to be safe / calm my fears.

---

### Post by KillEmAllx on 2014-06-16
> **twu026 said:**
> I am using the ASUS UX32VD with Ubuntu 14.04 LTS. 

So apparently this model of laptop lacks the sensor feedback required for fan control by the kernel. This results in a very noisy fan that seems to be ON most of the time!

I found a 'hack' C program ([http://www.linlap.com/asus_ux32vd](http://www.linlap.com/asus_ux32vd)) which works OK for me so far. Using the parameters suggested by the program author, my fans run very quiet and the system remains cool.

Just do a search for 'fan' in the **comments** section near the end of the webpage and you will find a pastebin link to the C source code. Instructions to compile the source code to an executable is in the comments of the source code.

Disclaimer: Like the author of this program says,** use at your own risk!** I've only just started to use this program myself so am a bit paranoid about overheating. I pop open xsensor every now and then to check the temperature just to be safe / calm my fears.

Thanks for the info! It's too risky for me though, I want to avoid risky stuff as much as possible...
Any tips then? Is it good to use CPUfreq indicator at all? I mean, is it good for the cpu to change governors or speed that isn't "natively" supported?

---

### Post by twu026 on 2014-06-17
I've been using CPUfreq indicator on my UX32VD without any adverse effects. 

In fact, switching to 'powersave' mode in CPUfreq has been really handy when I am running off battery and need endurance.

---

### Post by KillEmAllx on 2014-06-18
> **twu026 said:**
> I've been using CPUfreq indicator on my UX32VD without any adverse effects. 

In fact, switching to 'powersave' mode in CPUfreq has been really handy when I am running off battery and need endurance.

Do you have TLP installed as well? And which governor do you use by default? Ondemand or Conservative?

---

### Post by twu026 on 2014-06-19
Yes, I have TLP installed. But honestly, I can't tell what effect it has on my laptop.

If I am running off mains power, I usually use Ondemand. When I am on battery and not doing anything computationally intensive, I usually switch to Powersave.

---

### Post by KillEmAllx on 2014-06-20
> **twu026 said:**
> Yes, I have TLP installed. But honestly, I can't tell what effect it has on my laptop.

If I am running off mains power, I usually use Ondemand. When I am on battery and not doing anything computationally intensive, I usually switch to Powersave.

Thanks for the tip, I was "afraid" that TLP and CPUfreq would drain the battery somehow.

---

### Post by consman on 2014-08-20
I have the same problem with my Bonobo Extreme 6 from System 76  - I upgraded to 14.04 using a fresh install and now the fan runs all the time. It rarely ran before, even under a very heavy load.  I have 32 GB of RAM.

---

### Post by Eugen_Covaci on 2015-02-01
I had the same problem on my HP laptop and I solved it with
```

sudo apt-get install thermald

```
For further informations see: [https://01.org/linux-thermal-daemon/documentation/introduction-thermal-daemon%20](https://01.org/linux-thermal-daemon/documentation/introduction-thermal-daemon%20)
Update: **It works only for Intel CPU**

---

### Post by cyril5 on 2015-06-30
For the record, I have accidentally drives my fan crazy on my laptop (a no brand with Ubuntu Studio) with a simple keys combinaison : Alt+Fn+1
The same combinaison to toggle off.
Hope this helps.

---

