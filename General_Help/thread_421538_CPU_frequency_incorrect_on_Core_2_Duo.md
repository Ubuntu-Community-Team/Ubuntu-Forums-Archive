---
title: "CPU frequency incorrect on Core 2 Duo"
date: 2007-04-24
forum: General Help
---

### Post by ahaslam on 2007-04-24
I have an Intel Core 2 Duo E6300. Its stock speed is 1862MHz and it'd overclocked to 3150MHz. My problem is that the CPU Frequency panel plugin shows 2.33GHz. Benchmarks do show that performance is lacking a little from my Zenwalk install, but that may simply be the extra services along with the Gnome desktop. So I don't know whether it's real or just a misreading.

As I don't throttle my cpu under Zenwalk I disabled the cpu frequency manager & power management in Ubuntu but strangely cpu scaling still works.

I have attached a couple of screens showing the situation. The Ubuntu screen shows a few relevant settings, current speed (after setting the performance governor) & simple hardware info. The Zenwalk screen shows what should be shown (look at the conky info).

Any help would be greatly appreciated, I don't need cpu throttling but I do need to know that the full speed is available.

Tony ;)

---

### Post by rufius on 2007-04-24
I'm thinking that the Gnome System Monitor is showing you what its reading from the chip's registers. Try this to make sure:

```
cat /proc/cpuinfo | grep '^cpu MHz'
```

Post what it outputs and that'll tell us what its up to. cpuinfo shows the current clock speed, so my chip which is 2GHz is currently at 1.667 GHz because I have it clocked down since its a laptop.

---

### Post by ahaslam on 2007-04-25
```
ahaslam@desktop:~$ cat /proc/cpuinfo | grep '^cpu MHz'
cpu MHz         : 2333.000
cpu MHz         : 2000.000
```

With a fsb of 450MHz, those figures should be 2700 & 3150. Is it reading the fsb wrong, or is it actually setting it?

---

### Post by Rui Pais on 2007-04-25
> **Anthony Haslam said:**
> ... I don't need cpu throttling but I do need to know that the full speed is available.

Hi,
i don't know if i understood the issue correctly but seems to me that it's just the frequency governor that put your cpus freqs at minimum, the correct thing anyway. 
If your computer starts to do somethi8ng that need full speed it will be automatically turned to maximum either on one cpu or on both according to the needs.

You can easily set both to maximum with a basic utility like cpufreq-set (from the package cpufrequtils) but that will only waste energy and force the cpu to produce only more heat.

hth


edit:
btw cpu freqs applet refers only to one of the cpus (i don't know if you know that, cause you have only one of those applets on your panel) i hit an annoying behavior (a bug?) when i set 2 applets, one for each cpu, cause the second applet was never correct ...

---

### Post by ahaslam on 2007-04-25
The governor was set to performance.

I find it weird how frequency selection still works as I've disabled the relevant services & blacklisted the kernel modules (maybe I'm not doing it properly, [see here]("http://ubuntuforums.org/showpost.php?p=2532557&postcount=5")). I would be happy if scaling was completely disabled.

---

### Post by Rui Pais on 2007-04-25
ummm maybe blacklist failed.
whats the output of:
```
lsmod | grep freq
```

---

### Post by ahaslam on 2007-04-25
Thank you for your reply, here's the output:
```
ahaslam@desktop:~$ lsmod | grep freq
acpi_cpufreq           10760  1 
cpufreq_powersave       3072  0 
cpufreq_userspace       6176  0 
cpufreq_ondemand       10640  2 
cpufreq_conservative     9736  0 
cpufreq_stats           8416  0 
freq_table              6336  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
processor              34952  2 acpi_cpufreq,thermal
```
I assume that means it failed?

I added:
```
# stop cpu frequency scaling
blacklist acpi-cpufreq
blacklist powernow-k8
```
Powernow-k8 doesn't work anyway, I thought I'd make sure it didn't try loading it.

Did I do something wrong, any ideas?

---

### Post by Rui Pais on 2007-04-25
yes they are loaded and working.

You may need to add to blacklist list all 
acpi_cpufreq, cpufreq_powersave, cpufreq_userspace, cpufreq_ondemand, cpufreq_conservative, cpufreq_stats. 
But sometimes blacklist can't prevent them to load (with default kernel i got a floppy module always loaded, that i blacklist and i don't even have a floppy driver)

you can use cpufreq-set to set to maximum and add those instruction to a start script or rc.local. 
There must be a conf file to set the default governor but i don't know which one, sorry.

btw, why do you want to disable this? there are only advantages and no down side (at least that i know).

---

### Post by ahaslam on 2007-04-25
> **Rui Pais said:**
> yes they are loaded and working.

You may need to add to blacklist list all 
acpi_cpufreq, cpufreq_powersave, cpufreq_userspace, cpufreq_ondemand, cpufreq_conservative, cpufreq_stats. 
But sometimes blacklist can't prevent them to load (with default kernel i got a floppy module always loaded, that i blacklist and i don't even have a floppy driver)
The terminal output lists them with ' _ ' but in reality they have ' - ' which should it be for the blacklist (I assume it follows the file name, ie. ' - ') ?

> **Rui Pais said:**
> 
you can use cpufreq-set to set to maximum and add those instruction to a start script or rc.local. 
There must be a conf file to set the default governor but i don't know which one, sorry.

btw, why do you want to disable this? there are only advantages and no down side (at least that i know).
I can change the governors & add to rc.local with no problem (distro universal) ;)
I want to disable it because it's using the wrong (lower) frequencys, no matter the governor.

---

### Post by ahaslam on 2007-04-25
OK, ' _ ' or ' - ' makes no difference here. I now have the following within the blacklist:

```
# stop cpu frequency scaling
blacklist acpi_cpufreq
blacklist cpufreq_powersave
blacklist cpufreq_userspace
blacklist cpufreq_ondemand
blacklist cpufreq_conservative
blacklist cpufreq_stats
blacklist powernow_k8
```

And cpu scaling still hinders. Why does it persist? The scaling part of the kernel config is practically the same in Zenwalk (no powernow), so rebuilding wont help. Does Feisty have a version of rc.modules, where all modules are listed and commented out as required, or does it rely upon the blacklist? Maybe I should just rename/delete these modules & drivers to be done with it, but I'd like to find a proper way ;)

---

### Post by Rui Pais on 2007-04-25
> **Anthony Haslam said:**
> The terminal output lists them with ' _ ' but in reality they have ' - ' which should it be for the blacklist (I assume it follows the file name, ie. ' - ') ?
why? blacklist, i think, must contain the name of the modules explicit and they are named with the _ (you can try load and unload them to check). I missed that detail from your post of your blacklist....

> 
I can change the governors & add to rc.local with no problem (distro universal) ;)
I want to disable it because it's using the wrong (lower) frequencys, no matter the governor.
oh, i see. That's strange... 
so if you enter:

sudo cpufreq-set -c 0 -f NN000000

it not change to that frequency?

could be a bug? not an hardware issue since it seems to work on your zenwalk...

---

### Post by Rui Pais on 2007-04-25
you answer faster then me.

can you unload the modules? 

Anyway, you can compile the kernel without cpufreqs scaling or ony with governor for performance.

btw, what
```
cpufreq-info | grep available
```
gives?

---

### Post by ahaslam on 2007-04-25
> **Rui Pais said:**
> 
can you unload the modules? 
I try to be proactive rather than reactive, so no, how is that done?

> **Rui Pais said:**
> Anyway, you can compile the kernel without cpufreqs scaling or ony with governor for performance.

Yes I am aware, though my Zenwalk install has the same option set under cpu scaling (bar powernow) but as cpufreq is not installed & I don't load the modules, I have no scalling (when I do the same problem is apparent, it's not just Ubuntu).

> **Rui Pais said:**
> btw, what
```
cpufreq-info | grep available
```
gives?
```

ahaslam@desktop:~$ cpufreq-info | grep available
bash: cpufreq-info: command not found
```

Your help is appreciated, I've become too used to Zenwalk/Slackware.

---

### Post by Rui Pais on 2007-04-25
> **Anthony Haslam said:**
> I try to be proactive rather than reactive, so no, how is that done?
I was just curious to see if theycan be unloaded or something requires them to be load. My idea was left only acpi_cpufreq (not unloadable i think) and see if the cpufreq goes to the maximum or stays where it is.
unlaod modules with sudo modprobe -r modulename (tab helps to fill possible names) to reload is the same thing except -r flag. It's harmless you can play with no worries. 
You could try too load  sudo modprobe cpufreq_performance that it's the governor that will give the most in terms of freqs.
  
> 
Yes I am aware, though my Zenwalk install has the same option set under cpu scaling (bar powernow) but as cpufreq is not installed & I don't load the modules, I have no scalling (when I do the same problem is apparent, it's not just Ubuntu).
ah well, that seems more normal. As long as you do scaling the freqs don't behave, thats it. Maybe an hardware issue then... or some problem due to the fact you have overcloked... did that happens with "normal" clock?
> ```

ahaslam@desktop:~$ cpufreq-info | grep available
bash: cpufreq-info: command not found
```

Your help is appreciated, I've become too used to Zenwalk/Slackware.
thats because you don't have cpufrequtils installed. It's an excellent app to monitor and set frequencies, at ubuntu is at repos. 
You can get the same info with:
cat ```
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```
and
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
```

---

### Post by ahaslam on 2007-04-25
Your suspicion was correct, acpi-cpufreq can't be unloaded, "in use".
I've always used 'cpufreq-selector -g <governor>' so set the governor, nice to know new ways ;)
My overclock is not an issue, the system is working fine & both the bios & Zenwalk report the correct freq. When running at the normal clock speed cpu scaling still uses the wrong freq's, only lower.
I'll leave the cpufreq package for now, I really want rid of it altogether if possible. 

Anyway, I'm now going to resort to renaming the relevant files, failing that I'll compile a kernel without cpufreq support.

---

### Post by ahaslam on 2007-04-25
Changing the file name worked, but it nags me about it.
You can see the proper freq in the screenie, just a pity the module can't be removed/disabled.

[ATTACH]30838[/ATTACH]

Does Ubuntu have an equivalent to rc.modules (example below)? If not it'll be time for a custom kernel.

[ATTACH]30839[/ATTACH]

---

### Post by Rui Pais on 2007-04-28
Hi again Anthony,

i stumped on something that may interest you in relation to this issue.

I was playing with a new installation of feisty (based on mini/server install+base system) and i get  the exact opposite of your problem. Cpu frequency always at maximum and no minimum for scale... 
i take a while till discover that  the service responsible for frequency scaling is powernowd (+powernowd.early) and just needed to install that package to get it (i should have known this before :().

So maybe you can solve your problem by just turn those services off or even remove them.
hth.

---

### Post by ahaslam on 2007-04-28
Thanks for your continued support. I had already disabled that service, it made no difference as it did nothing for my intel anyway. 

My filesystem went screwy on my Fiesty install so I'm back on my Zenwalk install. I hope this won't be an issue in the future as C2D's are becoming very popular. Maybe I'll try out the x86 version when I get some time, I know the Ubuntu site says for amd & intel, but the iso still says amd64 :-k

---

### Post by Rui Pais on 2007-04-28
sorry no more ideas.
but compiling a new kernel should solve the issue, as long as you compile a module only for performance governor (or none at all). I never use ubuntu ones. Either they are buggy, with stuff not only recommended for debug enabled by default and usually old (feisty is the exception in this last point). I used emission sources and later stay by beyond sources. Fast and solid.
> **Anthony Haslam said:**
> ... I hope this won't be an issue in the future as C2D's are becoming very popular. Maybe I'll try out the x86 version when I get some time, I know the Ubuntu site says for amd & intel, but the iso still says amd64 :-k
don't worry with the amd64 it's just the old nomenclature from the time that at 64b AMD ruled and alone... btw if you compile the kernel you can tune it to c2d specifically. A nice extra.

---

### Post by ahaslam on 2007-05-01
Compiling the kernel *without* scaling support would have solved the issue, but it's too late now, Ubuntu (or ext3) went postal.

---

### Post by fakie_flip on 2007-05-04
Removing that annoying powernowd package by using apt may help.

---

### Post by fakie_flip on 2007-05-04
> **Anthony Haslam said:**
> Compiling the kernel *without* scaling support would have solved the issue, but it's too late now, Ubuntu (or ext3) went postal.

Compile your own kernel without cpu scaling support.

---

### Post by ahaslam on 2007-05-05
I'm trying Feisty again (32 bit this time) and the service stops when power management is disabled, so there is no issue. Cpu benchmarks also function properly under 32 bit & I found it to be simple misreading, performance remains the same with or without scaling & it's comparable with other distro's.

So either way, enabled or disabled, there is no real issue with 32bit Feisty ;)

---

### Post by fakie_flip on 2007-05-11
Performance with what remains the same as what? Do you mean the performance in 32 bit Ubuntu is the same with 64 bit Ubuntu? What do you mean?

---

### Post by fago on 2007-07-24
hm, so the problem doesn't exist in 32bit feisty?
I'm running 64bit here and have exactly the same problems.. The cpu is overclocked, but as soon as I activate EIST in my bios, the frequency is wrong.. (way too low).

Have you managed to solve the problem now?

---

### Post by fago on 2007-07-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91553](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91553) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				also see this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91553](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/91553)

seems to be a bios problem :/

---

