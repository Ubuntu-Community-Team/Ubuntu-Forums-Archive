---
title: "High temperatures when using Ubuntu 14.04"
date: 2015-03-10
forum: General Help
---

### Post by danbuz on 2015-03-10
Hi guys,

For the past few days I use ubuntu 14.04 on a new laptop, and I noticed 2 things:

1 - The machine is overheating - psensor shows up to 94C when using Firefox or Chromium with no more than 3 tabs opened and no flash player.
When idle - about 72-74. The processor is last gen i5 and the GPU is Nvidia (I've installed the driver, even tried with xorg.. the same temperature)

2 - The battery is not capable of more then 2 hours of work - even with turned off Wi-fi and Bluetooth and installed TLP.. This is compared with Windows 7 -
the battery with disabled wi-fi and Bluetooth is up to 5-6 hours.. The fan is constantly working on Ubuntu, and it is quiet on windows...

First I though it is a dust issue - but no?! I've tried XFCE and it is fine, but I prefer Unity.. What might be the case?

I know Linux is power hungry and I do not care much about the battery since I use the machine mainly when I'm home, but the OVERHEATING is a 
big issue for me..

Could someone share a solution or a thought on the subject?

Thanks in advance!

P.S. - I've tried 14.04 on older hardware with Intel GPU + i3 and the same things appeared - poor battery life and overheating - but not so much as compared to the newer configuration?!

---

### Post by dino99 on 2015-03-10
First to check: is there some usefull warnings/errors logged ? Then how is set powersaving ?  Maybe do some app's profile.

[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

---

### Post by danbuz on 2015-03-10
Thanks for the fast reply. No Warnings or errors. Powersaving - just TLP automatically set the battery mode when power supply is off, I always turn off the bluetooth. Than
set to dim the display after 5 min when not active..

While I'm typing this only chromium is opened with 3 tabs and the temp is 72C and I read that for my processor 72C is when heavily loaded with tasks..

---

### Post by pmi2 on 2015-03-10
Same here, desktop w. quad core i5 and 8Gb of RAM.  Not heat (i have three fans in the machine), but excessive CPU load.

Your laptop may be overheating, because there is some kind of process or task running in the background and loading the processor.  I am experiencing this w. 14.04 LTS and Unity on a quad core i5 with 8Gb of RAM, to the point that my desktop slows noticeably at times.  

I also have Linux Mint installed in a dual boot for comparison, and not seeing it there.

So if this is whats happening, you would not see anything on your desktop, unless you run some kind of monitor, like the Ubuntu "System Monitor" from the official Repository, or "Top" in a terminal window, or "GKrellM" etc.  

I have been running "Top -i" in a terminal but that is not the only option.

Keep an eye on the Compiz process, to see if it is active when the machine should be idle, is it consuming more than 1~2% of CPU when you are only in your browser, doing nothing, etc...

---

### Post by gifford on 2015-03-10
Yes, run system monitor and see if you can find out what processes are CPU hogs. How new is your Ubuntu install?
Is it 14.04.2 with 13.16 kernel?

---

### Post by danbuz on 2015-03-10
I watched the activity, no strange apps are consuming excess power. The strange thing is that I do not have compiz manager installed, but compiz process sometimes uses 130 MB memory and some times up to 270.. Only hot corners activated.

I'm even with latest 13.18 kernel. 

I noticed that firefox is pretty consuming app, while on windows 7 is the opposite - Chrome is the most consuming..

Other thins that I noticed is that after reboot hot corners are not active and I should turn them on via unity tweak tool every single time, which is annoying ...

If Mint is less consuming is it possible to install Unity on mint with the same functionality as it like on Ubuntu?

I really like ubuntu and I did not used it since 10.10, and back than it was SOLID ROCK, there was times when I did not rebooted my laptop for more than 3 weeks and it was smooth like butter :) 

Than I switched to Xubuntu, but now I'm in love with Unity and I want to solve this issue?!

---

### Post by pmi2 on 2015-03-10
I don't know about Unity on Mint, never occurred to me to investigate that.  

I am pretty new to Unity in any case.  When i run Firefox on Unity, I have Adobe Flash disabled most of the time.  Even then, just spinning the scroll wheel on my mouse, Firefox CPU usage can go up and then the screen starts to lock up and will not scroll smoothly.  That does not seem to happen on Windows 7, or Mint.  

However, in my case I can clearly see the CPU usage spike when it happens (I have the terminal window set to "Always on Top"), so perhaps we do not have the same issue after all.

---

### Post by danbuz on 2015-03-10
> **pmi2 said:**
> then the screen starts to lock up and will not scroll smoothly.  That does not seem to happen on Windows 7, or Mint. 

Absolutely the same here! Firefox dim out and it is not active for a while.. 

Ok, someone else suggest a solution. Is there a way to troubleshoot? Some kind of paid support even ???

I browse the internet for more than 3 days and still nothing ( I noticed that many complain a similar issues though)..

---

### Post by danbuz on 2015-03-13
Update

Guys, the situation is getting worse! Yesterday overheating caused 3 shutdowns of the system for the FIRST TIME since I use my laptop.
On the Intel website it's mentioned that the max temp for my processor is 100C and I did not get any temp below 76 with 14.04!

I installed many apps that could be installed without messing each other - TLP, CPUfreq, Thermald and so on.. 
I installed Nvidia-Prime ( I use Geforce) and switched to intel GPU and the processor was in power-save mode too..
Than tried the opposite - nothing changed.

Ubuntu was fresh installed and the problem started since the beginning of the usage. Only 2 application are capable to
do the harm - for example audio playing and firefox/chromium with 1-2 tabs opened and the one is playing video for example.

Right now I use Windows 7, forefox opened with more than 9 tabs (2 videos one in pause) Xampp, Music plaing and Photoshop
and the temperature is 68. I installed Mint on another partition just to test and the temps are way lower than Ubuntu.

I want to use Unity SO HARD, but I can't figure out what to do to solve my problem. I searched every possible solution for more than
5 days and still no luck.

What might cause this problem guys, please share your opinion, need some support here, really!

Thanks in advance!

---

### Post by gifford on 2015-03-13
Sorry about the issues you are having. I wonder, maybe with the older hardware if you could install Ubuntu 14.4.1 and see if 
you have the same issues. It uses kernel 3.13.

---

### Post by pmi2 on 2015-03-13
> **gifford said:**
> Sorry about the issues you are having. I wonder, maybe with the older hardware if you could install Ubuntu 14.4.1 and see if you have the same issues. It uses kernel 3.13.With respect, the OP wrote ... > The processor is last gen i5 and the GPU is Nvidia...Is that really so old?

I am experiencing some issues w. CPU load on a quad core i5 (i5-3550 CPU @ 3.30GHz × 4), which can sometimes slow down my Firefox browser significantly, despite having Flash disabled, and Adblock Plus installed.  Im on a desktop with multiple fans, so overheating is not an issue, but still... :???:

In the case of a laptop, it is not just the greater amount of current and power consumed by the CPU, but also the self-heating by the battery as it is put under continuous load that makes the problem worse.  At a minimum, battery life will be shortened by higher temps and more cycles.

At the very least, I would read the system log to see if there are any odd entries, check the processor load using Top or something similar if the problem is consistent and repeatable, etc...

---

