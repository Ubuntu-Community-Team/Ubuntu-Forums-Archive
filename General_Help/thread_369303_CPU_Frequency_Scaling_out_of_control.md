---
title: "CPU Frequency Scaling out of control"
date: 2007-02-24
forum: General Help
---

### Post by utkjamie on 2007-02-24
First of all, I apologize for adding a new thread to this topic but I've not been able to find suitable solutions in any other threads on this problem.

I'm running Edgy with the Kubuntu desktop (Ubuntu desktop is also installed). CPU frequency scaling has been dropping my laptop CPU from 1.6GHz down to 600MHz at really strange times -- often when I'm using the laptop. I would imagine that CPU scaling is designed to kick in when the computer has low activity but in my case it's usually when I've got multiple Firefox tabs open and several applications running. The last time, for instance, I had over 10 Firefox tabs open and Ktorrent, Thunderbird and Kontact running along with the standard systray apps (e.g. Skype, GAIM, etc). Needless to say, once the CPU goes to 600MHz, it's very difficult to do anything. Last night it was taking several minutes just to switch tabs in Firefox. (It sometimes gives me flashbacks of using WinXP *shudder*). [Update: I pushed the CPU even further today with Ktorrent downloading about 8 files, Kmail and Thunderbird running, multiple tabs open in Firefox, and a video playing -- and the CPU scaling still kicked in while I was using the computer. Could this be a bug?]

I've tried many solutions I've come across. I've edited configuration files, installed sysfsutils and edited other files. I've installed Klaptop. I've tried Kpowersave. In each of those I've made setting changes for the computer to run in performance mode to no avail. In fact, Klaptop *only* gives me the option for powersave mode, so I have no idea what is overriding that setting and triggering CPU scaling.

I've read in some threads that cpufreqd is a great alternative. Even powernowd might work. The problem is that I have powersave installed and these apps require removing that first. The problem with that is that removing powersave removes both ubuntu-desktop and kubuntu-desktop and that would create an even bigger problem.

Does anyone have a solution that will actually work? Any apps I should remove or install? I'm pretty desperate because once the scaling starts all I can really do is sit back and wait for it to end (it seems to switch back to performance mode just as randomly as it scales down).

Thanks!

---

### Post by igknighted on 2007-02-24
> **utkjamie said:**
> First of all, I apologize for adding a new thread to this topic but I've not been able to find suitable solutions in any other threads on this problem.

I'm running Edgy with the Kubuntu desktop (Ubuntu desktop is also installed). CPU frequency scaling has been dropping my laptop CPU from 1.6GHz down to 600MHz at really strange times -- often when I'm using the laptop. I would imagine that CPU scaling is designed to kick in when the computer has low activity but in my case it's usually when I've got multiple Firefox tabs open and several applications running. The last time, for instance, I had over 10 Firefox tabs open and Ktorrent, Thunderbird and Kontact running along with the standard systray apps (e.g. Skype, GAIM, etc). Needless to say, once the CPU goes to 600MHz, it's very difficult to do anything. Last night it was taking several minutes just to switch tabs in Firefox. (It sometimes gives me flashbacks of using WinXP *shudder*).

I've tried many solutions I've come across. I've edited configuration files, installed sysfsutils and edited other files. I've installed Klaptop. I've tried Kpowersave. In each of those I've made setting changes for the computer to run in performance mode to no avail. In fact, Klaptop *only* gives me the option for powersave mode, so I have no idea what is overriding that setting and triggering CPU scaling.

I've read in some threads that cpufreqd is a great alternative. Even powernowd might work. The problem is that I have powersave installed and these apps require removing that first. The problem with that is that removing powersave removes both ubuntu-desktop and kubuntu-desktop and that would create an even bigger problem.

Does anyone have a solution that will actually work? Any apps I should remove or install? I'm pretty desperate because once the scaling starts all I can really do is sit back and wait for it to end (it seems to switch back to performance mode just as randomly as it scales down).

Thanks!

Ubuntu-desktop and kubuntu-desktop are ghost packages.  They exist so you can install the whole system with one go (they depend on everything a ubuntu desktop would have) rather than piece by piece.  If it gets removed there is no loss, as the packages that came with it will stay.

I might suggest you turn your power setting to performance and not let it scale at all.  Some mobo's just don't act well with the various cpu scaling protocols in linux, so if you try a few and they dont work, just disable it.

---

### Post by utkjamie on 2007-02-25
Ah, I didn't know that about the desktop packages. Good to know.

Will removing the desktop packages cause problems when I upgrade to the next release?

BTW...

Yesterday I turned off powersaved from the System Services (Runlevel Editor) to see if that would help but, according to a CPU monitor I have running, that dropped the CPU to 599MHz. When I turned it back on, the CPU went back to 1.6GHz. I just turned it off again today and the CPU seems to be steady at 1.6GHz. I'll update if anything else gets screwy. Maybe someone else is having the same problem.

UPDATE: Even after shutting down the powersaved service I continue to have problems with the CPU frequency being scaled down to 600MHz. I cannot see any other running process that might be hijacking the process but whatever it is it would explain why Kpowersave settings are not being obeyed. I'm at a loss to understand what's going on and it's rendering my system useless whenever it kicks in.

---

### Post by utkjamie on 2007-02-27
As a follow-up to my previous posts, here are some possible solutions I've come across (for those who may be having the same problems).

I found some good info from the [Ubuntu Guide Wiki]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features"). The guide is good for making sure the CPU frequency scaling is configured correctly in the first place. I only recently came across it so I can't yet say if it has resolved the problems I've been having.

A more drastic approach is to simply turn off power management at the kernel level during booting. I prefer not to use this method because I'd like to use the power management options. For those cases I want that option, though, I just added a new boot option to */boot/grub/menu.lst* with *acpi=off* as a kernel boot option.

UPDATE: After following the "How-To" I mentioned above frequency scaling appears to be working perfectly. My CPU monitors show it dropping the CPU down to 600MHz when I'm not doing much but it is completely unnoticeable and the CPU immediately jumps right back up to 1.6GHz when needed.

---

### Post by Castar on 2007-03-08
Hi, I've having the same problem with my Centrino processor. Can you confirm if the link above is a good solution to the problem? Thanks!

---

### Post by utkjamie on 2007-03-09
I stopped having problems after following the instructions in the link from my previous post. CPU frequency scaling was working -- it would drop down to 600MHz while I was only web browsing, for instance but wouldn't slow the computer down to the point I couldn't use it. It would then jump up to 1.6GHz when needed.

You might need to play with a few different settings to see what works best for you, but I believe I set mine to OnDemand. I also didn't remove any software that would have caused ubuntu/kubuntu-desktop to "break". (I would verify my settings but I had to reinstall Linux a few days ago due to a crash and haven't gotten around to tweaking my powersaving settings).

---

### Post by Castar on 2007-03-09
I tried the above procedure to no result. :(  

My Ubuntu is so sluggish that it is not usable anymore. I have had the problem with Edgy, which made me try out openSUSE 10.2. I also had the same problem, after some normal behaviour the clock would freeze at 600MHz even though it was running at 100% load for an hour! The difference was that with oS the throttling would be working normally for some time before going permanently down.  Edgy and Feisty would start from the lowest point. This happened I think due to the generic kernel. :confused: 

This is a major issue IMO and apparently no-one cares about it. :confused:

---

### Post by utkjamie on 2007-03-10
Scratch what I said in the previous post. The problem has resurfaced on my fresh install and what I thought had worked previously doesn't appear to be the solution. I tried so many things the first time around -- powernowd, cpufreq, powersave, etc -- and edited so many files it's hard to say what fixed the problem.

The "scorched earth" approach would be a use the *acpi=off *option during boot up (just add it as a boot option to /boot/grub/menu.lst). That should turn off power management completely at the kernel level. It's not the preferred solution for obvious reasons but, like you said, there doesn't seem to be a pressing concern to resolve a problem that a lot of people seem to be having.

Let me know if you have any luck and I'll do likewise.

---

### Post by utkjamie on 2007-03-11
At this point I think I can safely say that this is the unresolved problem that destroyed the Linux honeymoon phase for me. It's frustrating that there seems to be no solutions and, apparently, only two Ubuntu users that are having this problem.

As an example, the problem is so bad that it has taken me nearly 10 minutes to navigate to the UbuntuForums.org web site and to this specific post so I could reply to it. Even in powersave mode, is that considered acceptable?

The part I don't understand about this CPU scaling problem is that I specifically instruct Linux to run in 'performance' mode, which means that it is to run at maximum speed, no exceptions. I verify that this is indeed the governor that CPU scaling is running under and yet it still runs at a sluggish 600 MHz even when the applications are demanding more. It's like Linux is saying *"yeah, I know what you told me to do but your input is irrelevant to me."*

Can anyone at least tell me if this is a distro-specific problem or a Linux kernel problem? I've lost hours of productivity over the past two days because of this problem and I'm reaching the end of my patience.

---

### Post by Castar on 2007-03-12
Actually, I think it is a kernel problem as I had the same issue with openSUSE. The latest versions of both distros are using the generic kernel, whereas Dapper and 10.1 (I think) used the 386, 586 etc. kernels. Dapper was running very well on my laptop for example. Unfortunately, the software in Dapper is old so I cannot use it and I don't think that I should.

Also, we're not the only ones to experience the problem. I've seen it in at least 10 threads on this in Ubuntu but for some reason they become inactive as no-one knows how to help. I have tried all the solutions there with no success.

I am starting to think that my honeymoon IS actually ended... :(

---

### Post by utkjamie on 2007-03-12
A problem in the kernel would explain why the scaling settings are being ignored and why none of the different daemons I've tried actually work (although somehow I had it working before a crash corrupted my filesystem and I had to reinstall Linux).

Compiling a custom kernel is on my "to do" list somewhere. Maybe I'll have to bump it up to a higher priority.

Thanks for letting me know the problem is bigger than just my computer!

---

### Post by utkjamie on 2007-03-13
This definitely appears to be a kernel bug:

[LIST]
[*][Bug #36014]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/36014")
[*][Bug #71772]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/71772")[/LIST]It looks like it may be fixed in kernel 2.6.20.  Let's hope...

---

### Post by Castar on 2007-03-13
Actually it hasn't been fixed. I was using Feisty for a while (which has 2.6.20) and it was ugly... :confused:

---

### Post by ac4000 on 2007-03-28
I'm not sure whether this will be useful, but I installed cpufrequtils (apt-get) to easily change the governor settings.  In at least my case, setting the mode to performance sidesteps the system guessing at how much processing power you want (although I should note that in my case ondemand actually works fairly well and I hear it saves a lot of power and runs cooler).  If you edit /etc/defaults/cpufrequtils and change ENABLE to true, it will set the mode you've set at boot time, which would allow you to keep your ACPI enabled.  I'm using 2.6.17 on an Athlon XP, so again this may not be useful at all, but just in case....

---

### Post by Castar on 2007-03-28
I can confirm that with the latest kernel in the Feisty Fawn Beta (2.6.20-13) throttling works properly again! Apparently there was a patch applied setting the correct voltages for the centrino processor.

More information [here]("http://ubuntuforums.org/showthread.php?t=388828"). I know that upgrading to the beta is not the best but it does solve the problem AND Kubuntu Feisty  rocks ;).

---

### Post by utkjamie on 2007-03-28
Unfortunately the cpufrequtils settings hasn't worked for me, ac4000 -- but I appreciate the info nonetheless.

I'm glad to hear that the bug has been tackled in Feisty Fawn! It's been like using an abacus with a keyboard all this time! ;-)

---

### Post by utkjamie on 2007-04-08
Alright, after an extreme amount of frustration, I think I may have found a solution for those of us not yet using Feisty.

First, I followed the instructions for setting up my system for my Centrino processor using:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

That, in itself did nothing to fix the problem -- and may have nothing to do with the solution, but I did it before doing the following.

I then followed the cpu frequency scaling directions from:
[http://www.math.dartmouth.edu/~sarunas/D620F6.html]("http://www.math.dartmouth.edu/%7Esarunas/D620F6.html").

Rebooted and it seems to be working fine now. (And I'm hoping it continues working fine.)

---

### Post by Castar on 2007-04-22
utkjamie, can you confirm that your system is working correctly now? 

btw, I've been using Feisty and it behaves perfectly.

---

### Post by utkjamie on 2007-04-22
I had some data corruption last weekend that screwed up my /home partition, so I'm going to just go ahead and do a fresh Feisty installation sometime this week or next weekend -- when I'm freed up from this last week of classes. I'll let you know how it goes.

---

### Post by Ujoux on 2007-04-22
So i'm finally registering myself on this forum because i have the exact same problem.

Had it on Edgy... still there on Feisty !

I also figured that it was scaling down to 600Mhz when i was running huge processes (like VirtualBox or a game in Wine).

Tried everything i could find on this problem, still no luck.

Right now i'm only using Firefox and no problem, the frequency stay at 1800Mhz as I wanted.

But if i run Wine it will be ok for 5-10 minutes then drop to 600Mhz.

Really really annoying...

---

### Post by Ujoux on 2007-04-23
I think i maybe figured it out.

At last resort I decided to take apart my laptop.
Removed a big stack of dust on the heatsink.

It seems to be ok now, i won 20°C (reduced from 94°C to 74°C at full load) and it's not going down to 600Mhz anymore.
It was probably due to the cpu overheat protection.

Maybe it will help you too ;)

---

### Post by Castar on 2007-04-23
Actually, I want to report the same thing!

I have found that with the old BIOS of my laptop (ver A02, Dell Latitude X1) openSUSE throttles perfectly well! The reason? The processor thermal table was updated in A03 and A06 to versions 1.1 and 1.2. Therefore, when the laptop reaches 70 deg. C, it will automatically reduce to the lowest possible frequency (in my case 600MHz) to protect the CPU!

I have now downgraded to the old BIOS and openSUSE 10.2 that runs on 2.6.18 is running excellently. Also, I have finally noticed that when the laptop is cold, in the beginning of operation the system throttled fine. It was only after some time that the temperature rise leads to the protective state of the lowest frequency. 

Apparently the kernel that Feisty runs (2.6.20) has the new thermal tables implemented. As I can rememeber, 2.6.20-13 (in the beta) was problematic but the throttling was fixed in 2.6.20-14 and has stayed like that of course in 2.6.20-15 which is the Feisty final kernel.

The problem is reported [here]("http://http://gentoo-wiki.com/HARDWARE_Dell_Latitude_X1#BIOS_updates"). So, the people with this problem can either downgrade their BIOS or update to Feisty!

---

### Post by utkjamie on 2007-05-02
I've been using Feisty for over a week now and haven't noticed any scaling problems with it so the fix comes as a very anticipated relief!

---

### Post by Castar on 2007-05-03
I know the feeling :KS

---

