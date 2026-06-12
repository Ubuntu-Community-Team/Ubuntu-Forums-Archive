---
title: "Ubuntu Consistently Crashing When X Server is Running!"
date: 2015-06-22
forum: General Help
---

### Post by cobalt2 on 2015-06-22
Whenever I'm working with Ubuntu and X Server running, I can't go for more than 5 minutes without my system crashing. I did a memory test, which it passed. Then I tried to install the linux-crashdump, in order to get a log of the crash. Terminal said, "Some packages could not be installed. The following packages have unmet dependencies: linux-crashdump: Depends: kdump-tools but it is not installable. E: Unable to correct problems, you have held broken packages. Then I tried running dpkg ino order to repair any broken packages. The program isn't detecting any broken packages. Is there an alternate way get the crash report?

---

### Post by oscar-tiderman on 2015-06-23
What version of Ubuntu are you running? I have checked in both 14.04 and 15.04 and both have kdump-tools in standard repos. Have you tried sudo apt-get install --fix-broken? What sources/repos have you enabled?

---

### Post by DennyTrend on 2015-06-23
Did you first?


```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by cobalt2 on 2015-06-25
> [COLOR=#000000]What version of Ubuntu are you running? I have checked in both 14.04 and 15.04 and both have kdump-tools in standard repos. Have you tried sudo apt-get install --fix-broken? What sources/repos have you enabled?[/COLOR]

I typed sudo apt-get install linux-crashdump. I'll try your apt-get and see what happens.

---

### Post by tgalati4 on 2015-06-25
Don't get your hopes up.  If the standard log files *dmesg*, /var/log/syslog don't pick up a consistent software crash, then it's possible that you have a hardware problem.  It's not uncommon for graphics card memory to go bad and cause a freeze, or simply the GPU gets hot and halts.  What is your hardware?  What is the temperature of your GPU?

---

### Post by cobalt2 on 2015-07-01
> **oscar-tiderman said:**
> What version of Ubuntu are you running? I have checked in both 14.04 and 15.04 and both have kdump-tools in standard repos. Have you tried sudo apt-get install --fix-broken? What sources/repos have you enabled?

[COLOR=#000000]```
sudo apt-get install --fix-broken
```[/COLOR][COLOR=#000000]didn't work.
[/COLOR]
[COLOR=#000000]I have Ubuntu 14.10. [/COLOR][COLOR=#000000]
[/COLOR][FONT=UICTFontTextStyleBody]
[/FONT][COLOR=#000000]What repo do I need to have enabled in order to get kdump-tools?

[/COLOR][COLOR=#000000]@DennyTrend:
Upgrade, update and autoremove were successful. Dist-upgrade failed. After entering these commands I'm still having this problem. The problem is so bad that when I launch Nautilus, my computer crashes in the middle of loading.

[/COLOR]> **tgalati4 said:**
> Don't get your hopes up. If the standard log files *dmesg*, /var/log/syslog don't pick up a consistent software crash, then it's possible that you have a hardware problem. It's not uncommon for graphics card memory to go bad and cause a freeze, or simply the GPU gets hot and halts. What is your hardware? What is the temperature of your GPU?
[COLOR=#000000]
AMD Athlon 64 X2 5200+ Dual Core CPU
4 GB PC800 DDR2 SDRAM
500 GB HD
Nvidia GeForce GTX 750 graphics with 1 GB GDDR5 memory. 

I don't know how to check my GPU temperature.
[/COLOR]

---

### Post by tgalati4 on 2015-07-02
Here's a link of representative power and temperature levels for your graphics card:  [http://www.anandtech.com/show/7764/the-nvidia-geforce-gtx-750-ti-and-gtx-750-review-maxwell/22](http://www.anandtech.com/show/7764/the-nvidia-geforce-gtx-750-ti-and-gtx-750-review-maxwell/22)

I would also check your power supply.  If the PSU is noisy, that can cause the GPU to crash.

Some things to try:

Declock the GPU in BIOS.  Raise the GPU voltage.  Try setting GPU to run slower or cooler (using the proprietary nVidia driver).  [http://ubuntuforums.org/showthread.php?t=2264860&highlight=nvidia+geforce+temperature](http://ubuntuforums.org/showthread.php?t=2264860&highlight=nvidia+geforce+temperature)

Install *psensor* and plot some temperatures.

---

### Post by cobalt2 on 2015-08-30
I did a system restore and installed Ubuntu 14.04 LTS, thinking it would provide more stability. I barely completed the installation despite all of the volatility. With 14.04 LTS installed, again my system would crash after no more than 5 minutes after starting an X server session. I tried turning acpi off by adding this to the GRUB:
```
GRUB_CMDLINE_LINUX="acpi=off"
```

It was a tradeoff: My system was stable, but it was no longer able to be put into standby. I found a workaround. I was able to use my BIOS settings to automatically turn off the hard drives after being idle for a time. I still could not put my computer into standby on demand.

Not being satisfied with this compromise, I did more research. Finally I came across [this page]("http://halffull.org/2008/10/25/how-to-fix-an-ubuntu-crash/") that cited AMD&#8217;s Cool&#8217;n&#8217;Quiet feature as a cause of Ubuntu system crashes. The user even has the same CPU model as me, an AMD Athlon 64 X2 5200+. In BIOS I went to Power Use Overclock Settings, and disabled AMD K8 Cool&#8217;n&#8217;Quiet and removed the acpi=off entry in GRUB.

 Now having acpi enabled was not causing my system to crash, except when I put it into standby sometimes, it would not wake up, forcing me to manually shutdown and restart. When I was successfully able to resume from standby, only pressing the power button brought the computer out of standby. when using the keyboard or touchpad to wake up my system, it was unresponsive. 

How do I enable using my keyboard or touchpad to resume from standby. 

Why is my system crashing sometimes when resuming from standby?

---

### Post by tgalati4 on 2015-08-30
Resuming from standby has always been an issue in Linux.  Sometimes it works, sometimes it doesn't.  Troubleshooting is difficult and the work-arounds are sometimes not obvious.  So patience is key, but things are generally fixable.

Go through the settings in /etc/default/acpi-support:

```
more /etc/default/acpi-support
```

Make some changes to that file and reboot.  You will have to search for common changes that are made to make things work.  If your graphics are not resuming, (Control-Alt-F1 does not bring up a terminal) then you might need to reload the GPU module upon resume--so put it in the acpi-support file.  As far as keypad for resume--sometimes the BIOS allows you to set the key you want for wake--spacebar, "P" key, or "Shift" key.  Otherwise you need to put the key in an event-handler that the resume scripts monitor.  It is not easy.

Next time you come out of resume with a blank screen, hit Control-Alt-F1 to get a terminal.  Then hit Control-Alt-F8 to get back to the graphical Desktop.  If neither of those work, then try the Magic Keys to reboot.

---

