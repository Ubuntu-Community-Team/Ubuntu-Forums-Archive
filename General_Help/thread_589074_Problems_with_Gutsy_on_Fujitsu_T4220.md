---
title: "Problems with Gutsy on Fujitsu T4220"
date: 2007-10-23
forum: General Help
---

### Post by miyoung on 2007-10-23
I just installed Gusty on my Fujitsu T4220 Lifebook and for the most part I can't complain but I have few issues that I would like to resolve and have been unable to fix them so far.

1)  The first most important issue is the fact that the fan on the computer will not turn on.  I used the terminal to check on the processor temperatures but it read only 27 C on both Cores (I have a duel Core processor.)  I think that due to the erroneous reading the fan never comes on since the computer thinks that it is never hot.  How can I get the computer to read correctly on the processors so the fan will turn on?

2)  The Fn F6 and Fn F7 brightness control keys do not work.  The screen brightness is whatever it was from the prior boot into the windows side of the hard driver.  Does anyone know how to enable functionality for those keys or at least be able to control the brightness?  I have tried through the terminal and the powermanagment window to no avail.

3)  Desktop enhancements from compiz did not work until I installed a gl xserver addon.  Now, however when I log in I do not get the gnome login status window which tells me that the desktop and nautilus are loading, etc.  Instead I get an ugly black x for the hardware cursor.  Does anyone know how to get the gnome login progress window back or at least how to get rid of the black x?

---

### Post by DagMan on 2007-10-23
That first issue is pretty worrying because there might not be anything to keep it from overheating entirely.  Most hardware today would shut the computer down if the processor got to hot, but it's a BIOS controlled thing and who knows then...

I doubt this will do it or it would have been on boot likely, but 
sudo modprobe thermal
sudo modprobe fan

for the brightness you can try
sudo modprobe video


It sounds like there is an acpi module needed for your notebook which hasn't loaded for conflicts of other things having loaded instead, or that you don't have support yet for these things.  I really don't know where the starting point is, but the incorrect temereature reading would for me be a bit of a worry when it's saying its that cool and we know that its very unlikely and the fan does not come on.

---

### Post by miyoung on 2007-10-23
Unfortunately I get nothing for any of those commands, literally no outpu.  Fortunately for the computer and my sake, it doesn't run very hot on Ubuntu so there hasn't been any noticeable damage, and I really doubt that there is any yet.  Thanks for the effort.  What could I do about the acpi issue?

---

### Post by miyoung on 2007-10-23
I think I have an idea but I just need a little help form someone to get it moving.  From the windows side I see that the there are actually four temperature sensors, two of which report the temperature for "thermal zone 1 and 2" which are reported at 79 deg Fahrenheit whereas the actual temperature is measured from core 0 and 1 which reports the actual core temperature at 138 deg Fahrenheit.  I can monitor this temperature actively from the Windows side so I know that this is the right sensor but I don't know how to get Ubuntu to see it.

---

### Post by DagMan on 2007-10-24
try the following and see if you hit any jackpots along the way.  Some things may load but then not provide funtionality, but can't be unloaded so a reboot would be required.

I can't say that I think this is a great idea btw.  Your processor certainly gets very very hot very very fast without any external cooling and it doens't have to be doing anything to create a lot of heat.  The boot process creates plenty of heat as well, so be prepared to kill your computer if you want to persue this by trial and error in the following.

these are all modules that look like they might either be for specific laptops or appear in the acpi folders and I just don't otherwise know what they are, so trying them out one by one.  sudo modprobe ....

sony_acpi
pcc_acpi
dev_acpi
tc1100-wmi
thinkpad_acpi
asus_acpi
toshiba_acpi

the lack of a fujitsu module doesn't mean that another one doesn't handle what you need.  Usually something that handles it is picked up during boot though.  

Before anything else though, how are you checking the temperature that you're reporting?  If you have a /proc/acpi/thermal_zone folder and it has a file or subfolder or subfolders with a file or files in it then try reading it, for example if I do this
cat  /proc/acpi/thermal_zone/THRM/temperature
it tells me that right now my processor is 47 C
I have a core 2 and don't know why I don't get a reading for each one but the way mine cools it's not relevant to see each one, and I can watch the file and see that it's changing and looks normal.  If you have a file like this then likely you have a module loaded that's looking after this.  If you didn't get any output from the modprobe fan modprobe thermal, then it sounds like they either loaded when you did it or were already loaded, so take a look.  It wouldn't explain your fan not coming on still, but having a think at it now, it's possible that your system has things loaded.  Wheather they are actually supporting your hardware properly or not I'm not sure.

You should get output from the following
```
lsmod | grep fan
lsmod | grep thermal
lsmod | grep acpi
```

I get this.
```
Dean ~ $ lsmod | grep fan
fan                     5508  0 
Dean ~ $ lsmod | grep thermal
thermal                14088  0 
processor              32088  2 acpi_cpufreq,thermal
Dean ~ $ lsmod | grep acpi
asus_acpi              17052  0 
acpi_cpufreq           10536  0 
freq_table              5520  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
processor              32088  2 acpi_cpufreq,thermal
```

If you're getting output here and can read a sane looking tempature from /proc/acpi then I don't know what's causing the fan not to come on.  Look around in /proc/acpi/thermal_zone and see what you see.

---

### Post by rcampbell on 2007-10-24
Hi, I recently got a T4220 as well, and here are this issues I encountered:

1. The fans work fine for me, so I can't really say what your problem is for that. You may want to check the BIOS. there is a setting there that changes the fan speed between 'Normal' and 'Silent'. It may be set to silent for you. Thats not likely the problem but I guess it is worth a shot...

2. The brightness keys don't work here either. I believe it is an ACPI issue. If I watch my dmesg output while pressing the Fn+F7 or F8 I get the following output:

```
Oct 23 22:32:07 tablet kernel: [ 2838.232000] ACPI Error (psargs-0355): [\_SB_.PCI0.GFX0.LCD_.BLNF] Namespace lookup failure, AE_NOT_FOUND
Oct 23 22:32:07 tablet kernel: [ 2838.232000] ACPI Error (psparse-0551): Method parse/execution failed [\_GPE._L1C] (Node df812168), AE_NOT_FOUND
Oct 23 22:32:07 tablet kernel: [ 2838.232000] ACPI Exception (evgpe-0576): AE_NOT_FOUND, while evaluating GPE method [_L1C] [20070126]

```

I havent looked to see if there have been any bugs reported on launchpad for this yet.

3. Regarding Desktop Effects. It does not work (well) with the X3100 so it is blacklisted by Compiz at the moment.

Also, the digitizer did not work right away for me. I had to uncomment a few lines in Xorg.conf and run 'setserial /dev/ttyS1 port 0x0220 irq 4 autoconfigure' to get it working.

The screen rotation is a little buggy as well. When it is rotated any way (left, right, inverted) the desktop doesn't redraw correctly and my windows leave trails of artifacts when they're moved. Very annoying.

Other than these issues the tablet works pretty well in linux, compared to previous laptops of mine.

Hope some of this helped, or at least pointed you in the right direction

---

### Post by DagMan on 2007-10-24
> **rcampbell said:**
> 
2. The brightness keys don't work here either. I believe it is an ACPI issue. If I watch my dmesg output while pressing the Fn+F7 or F8 I get the following output:

```
Oct 23 22:32:07 tablet kernel: [ 2838.232000] ACPI Error (psargs-0355): [\_SB_.PCI0.GFX0.LCD_.BLNF] Namespace lookup failure, AE_NOT_FOUND
Oct 23 22:32:07 tablet kernel: [ 2838.232000] ACPI Error (psparse-0551): Method parse/execution failed [\_GPE._L1C] (Node df812168), AE_NOT_FOUND
Oct 23 22:32:07 tablet kernel: [ 2838.232000] ACPI Exception (evgpe-0576): AE_NOT_FOUND, while evaluating GPE method [_L1C] [20070126]

```

I havent looked to see if there have been any bugs reported on launchpad for this yet.

Do you get anything when you run this and hit the key combos
```
tail -f /var/log/acpid | grep "received event"
```
If you get nothing then likely your laptop just isn't supported by the acpi project yet.  If you do get output, any at all, then it's that ubuntu's acpi-support package isn't able to account for every possible laptop out there when it trys to put all the logic together, and it can be setup manually with a bit of work.
It seems like something is happening though possibly, since you get a dmesg output.

---

### Post by miyoung on 2007-10-24
Dagman,

Thank you for your help.  It appears that the fan is now working though I can't say I know why.  I will however check using the information you gave me.  Anyways, I am not going to argue with the result.

---

### Post by miyoung on 2007-10-24
Okay so I need to modify my fan problem a little.  The fan does work but only ventillates moderately.  It still triggers off of Thermal zone 1 and 2 which are located in the acpi file under temperature as TZ00 and TZ01.  The real sensors are called core 0 and core 1 but I do not know how to find them.  Given that, what I need to be able to do is either trigger the fan of of those sensors or find a way to set the fan to max regardless of the internal temperature of the computer.  Can anyone help me with that?

---

### Post by miyoung on 2007-10-24
Good news.  I have been able to access the core 1 and core 2 temperature sensors and now the fan is much more responsive plus I can monitor the temperature using the temperature applets for Linux.

This is what I did.

sudo apt-get install ls-sensors
sudo sensors-detect

and then I rebooted.

Horay.

I would still like to change the threshold temperatures for the fan still all the same.  Does anyone know how to do that?

---

### Post by miyoung on 2007-10-24
Sorry,

I meant
sudo apt-get lm-sensors

---

### Post by ApoXX on 2007-10-26
I'm also running 7.10 on a T4220. Most of the functionality seems to be working and compiz fusion works great (I had to add SKIP_CHCKS=yes to /etc/xdg/compiz/compiz-manager). It's fun using the stylus to interact with the cube.

The only things I haven't figured out yet yet are the screen brightness control and the button mapping/rotation. I also need to take a look at cpu frequency scaling/governor, I'm not totally sure it's working or at least being reported correctly.

Has anyone figured out the brightness issue yet? There is a device entry in **/proc/acpi/video/GFX0/LCD/brightness** but when I try echoing values into it, it doesn't actually change anything. I'm getting the same messages in dmesg as rcampbell, nothing shows up in /var/log/acpid for the event.

I assume the buttons and rotation can be mapped with xmodmap but I haven't looked into it yet. 

I'm planning to throw together a tutorial on installing Linux on the T4220.

---

### Post by miyoung on 2007-10-29
Compiz works fine for me, though it did not at first.  I installed glxserver or something like that and then it worked fine.  The only problem I have is that now that I have installed that I don't have the little status window that runs between login and the desktop.

Anyways, I can confirm a CPU scaling governer problem for Ubuntu.  My cpu is a 2.0 dual core intel centrino and ubuntu scales it down to a measily 800 MHz.

Brightness controls, haven't figured those out yet either.

---

### Post by rcampbell on 2007-11-03
Hm, after reading your post about the cpu scaling not working, I decided to check mine out again. I'm almost positive that the scaling worked at least once, because I remember watching it change on the gnome frequency scaling monitor applet. But, checking out out now, it seems to be stuck at 800MHz for me as well.  I've changed the governor and tried manually setting the frequency with cpufreq-selector, and nothing works.

I haven't been able to get the brightness buttons (or the tablet buttons) working yet either. On a side not though, I tried Fedora 8 and the screen rotation works perfectly there, so apparently that problem is fixed somewhere upstream.

---

### Post by kazik on 2007-11-16
> **ApoXX said:**
> 
I assume the buttons and rotation can be mapped with xmodmap but I haven't looked into it yet. 


This won't be so easy according to this guy:
[http://jan.rychter.com/software/fjbtndrv/fjbtndrv.html](http://jan.rychter.com/software/fjbtndrv/fjbtndrv.html)

I got the buttons (under the screen) working (on ArchLinux actually) by taking his driver source, updating it to my liking, and then using xmodmap.

But for some reason ACPI on my T4220 is all screwed up.

---

### Post by rcampbell on 2007-11-21
Has anyone had any progress getting the CPU frequency scaling working?

---

### Post by debenham on 2007-12-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/177076](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/177076) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've logged a bug for the cpu scaling not working.
It is at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/177076](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/177076)

---

