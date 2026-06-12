---
title: "[SOLVED] troubleshooting abrupt shutdown"
date: 2008-04-10
forum: General Help
---

### Post by abujenin on 2008-04-10
My computer (running 7.10) doesn't last a few hours without shutting down abruptly, even without any application running. Could it be from the graphic card (nVidia GF 6200)? I tried looking into system log and just found "--MARK--" before restart. Also many application shutdown abruptly, Firefox, Totem, Log Viewer, ...
Any suggestions on how to troubleshoot this problem or what is causing it would be appreciated.

---

### Post by Rocket2DMn on 2008-04-10
If the computer suddenly just shuts down, that could be a sign of either a power supply failure, or more likely, an overheating problem on your processor.  What kind of processor are you using?  Are you on a desktop or laptop?  Is it custom built?  Do you fans run on high a lot (or not at all)?

---

### Post by Maconvert on 2008-04-11
Hello,

I'm having the exact same problem.
I replaced my powr supply and the problem is still happening.
I'm going to look at the processor fan next.

It's really annoying.

Cheers.

---

### Post by Rocket2DMn on 2008-04-11
Maconvert, if you processor is a few years old, or if you have ever replaced (or even just disconnected and reconnected) the processor fan or heatsink, you may need to apply thermal paste between the processor and heatsink.  I had a problem on my gameserver computer last summer where after taking off the heatsink to clean it, the remnants of a tiny cooling strip disintegrated and I had to use thermal paste to get the computer to stay active since it was shutting itself down because of overheating.
That's good advice for the OP, too, if overheating seems to be the source of the problem.

---

### Post by abujenin on 2008-04-15
After disabling the nVidia proprietary drivers, my pc stopped shutting down abruptly. But I lost 3D acceleration. My display card is nVidia GeForce 6200.

---

### Post by Rocket2DMn on 2008-04-15
How did you install the proprietary drivers initially?  Just using the built in method - Restricted Drivers Manager?

Another option is to use a program called Envy to install restricted drivers - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Just note that before you do a system upgrade to Hardy, you will need to run
```
sudo envy --uninstall-all
```
Then you can download the newer version of Envy for Hardy and you won't need to worry about uninstalling it before doing further upgrades.

---

### Post by abujenin on 2008-04-15
Thanks. That's a nice script. I installed the drivers with it and will keep my pc running and see who much uptime i get.

---

### Post by abujenin on 2008-04-17
It's still shutting down.

---

### Post by Rocket2DMn on 2008-04-17
Can you please post
```
uname -a
sudo lshw -C cpu
```
Also right click a panel (taskbar) and hit Add to Panel, then find Hardware Sensors Monitor and add it.  Right click the new icon that appears and hit Preferences.  Under Sensors tab se if you can enable the CPU temperature monitor.
If the Hardware Sensors Monitor is not available, you need to install "sensors-applet".
If the CPU option is not available, you may need to install "lm-sensors"
"hddtemp" may also be a useful program to have.

Basically, we want to know how hot your processor is running.

---

### Post by abujenin on 2008-04-17
CPU temperature is now 40 C
I removed the NVIDIA drivers with Envy to stop the shutdowns. 
uname and lshw output is in the attached text file.

---

### Post by Rocket2DMn on 2008-04-17
OK that stuff seems to be OK.  When you say that the computer shuts down abruptly, does it go through the shutdown sequence or does it suddenly just power off?
I am a little unclear on your processor(s) though, are you running double pentium 4s?  But why is it 64 bits wide?  If you know exactly what processor(s) you are running, please tell me.

---

### Post by abujenin on 2008-04-18
It doesn't go through any shutdown process as if someone pulled the power cord off. And it actually restarts. If I leave it a few hours, I come back and see a fresh login screen. But after removing the drivers, it's up now for  10 hours.
The CPU sensor is still show 40 C and I don't think its accurate because my cpu fan is multi speed and I ran a heavy application which caused the fan to speed up but the sensor was still showing 40 C.
I think the processor is Intel Pentium 4, just one. This is the motherboard [http://www.msicomputer.com/product/p_spec.asp?model=PM8M3-V](http://www.msicomputer.com/product/p_spec.asp?model=PM8M3-V)
I miss playing some game.

---

### Post by Rocket2DMn on 2008-04-18
That really sounds like an overheating or power failure problem to me.  Is the computer custom built?  Are you able to try a different power supply?  Have you added new hardware recently (extra drain on the power supply or just a bad device)?
You can check some logs in /var/log like (but limited to) messages, messages.0 (and so on), dmesg, and faillog.  No guarantees on finding anything though, esp. if it's a power problem.  If you still thing it might be a driver problem, please post
```
lspci | grep VGA
cat /etc/X11/xorg.conf
```

---

### Post by abujenin on 2008-04-18
The computer is custom built by me. I started with the built in display chip, but about two months ago I decided to upgrade to a graphic card and the problem started, I was running Fedora 8 at that time and used kmod-nvidia driver. [http://forums.fedoraforum.org/showthread.php?t=182863](http://forums.fedoraforum.org/showthread.php?t=182863). 
I tried cooling the pc;  I changed the power supply. But that didn't solve the problem.

Then I switched to Ubuntu. 
May be it's the graphic card heating up when I use the drivers.

---

### Post by Rocket2DMn on 2008-04-18
You may consider looking at your Xorg.0.log (and other Xorg logs) for errors - if you see anything suspicious, do post.
Have you tried putting the old video card back in to see if the problem goes away (you will most likely have to reconfigure X if you do).  Is the newer power supply more powerful than your old one?  If the newer video card drains more power and you are already tight for watts, that could easily be the source of the problem.  Pentium 4 era computers are some of the most power hungry desktops/laptops ever built, and throwing a powerful video card in the mix really piles on the watts.

---

### Post by bulletgani on 2008-04-30
my system with athlon X2 6000 on ECS MB  with 4GB ram and internal Nvidia 6100 graphic card started experiencing random/abrupt shutdowns as soon as I upgraded from Ubuntu 7.10 to 8.04. It was rock solid  with proprietary Nvidia driver before the upgrade. After the upgrade using nvidia driver causes shutdowns while watching videos. the problem of abrupt shutdowns seems to go away when the opensource "nv" driver is used in Xorg.conf. 

I want to use the "nvidia" driver to run compiz. Any fixes would be appreciated.

attached are Xorg, lspci and lshw

thanks 

-G

---

### Post by abujenin on 2008-04-30
I recently upgraded to 8.04 and installed Nvidia drivers with EnvyNG and the system now fails "restarts" during every boot process. I can only start using recovery mode.

---

### Post by Rocket2DMn on 2008-04-30
Ok, I want to try something a little different.  Uninstall the nvidia drivers from EnvyNG, then run
```
sudo apt-get remove nvidia-glx nvidia-new-glx
sudo apt-get remove linux-restricted-modules-*
sudo apt-get autoremove
sudo rm /lib/linux-restricted-modules/.nvidia_new_installed
^^ignore any file not found errors ^^
sudo apt-get install linux-restricted-modules-`uname -r`
```
Now reinstall the nvidia drivers from EnvyNG.

---

### Post by abujenin on 2008-04-30
It didn't work. I uninstalled Nvidia drivers with EnvyNG, restarted, did the commands (see attached) and then installed with EnvyNG but faced the same problem.

The Ubuntu logo shows up on start up, the progress bar completes, then the following messages appear:
* Starting anac(h)ronistic cron anacron   [OK]
* Starting deferred execution scheduler atd [OK]
* Starting perodic command scheduler crond  [OK]
* Checking battery state ...           [OK]
* Running local boot scripts (/etc/rc.local)  [OK]

The screen flashes them 3 times, then the computer restarts.

---

### Post by Rocket2DMn on 2008-04-30
Wait so what happens?  The computer just continuously restarts?  Or can you login at the GUI or at least at a tty?  If you can't get into Ubuntu, reboot into the recovery mode kernel (the second option at GRUB) and remove the package(s) we just installed with
```
apt-get remove linux-restricted-modules-`uname -r`
```
And reconfigure X
```
dpkg-reconfigure xserver-xorg -phigh
```
then reboot normally
```
reboot
```

---

### Post by abujenin on 2008-05-01
I did start it with recovery mode; it was the only way. Now I removed the restricted-modules and rebooted, but still no 3D accerlation.

---

### Post by Rocket2DMn on 2008-05-01
OK, why don't you post
```
compiz --replace
```
for me as well as your most recent xorg.conf file
```
cat /etc/X11/xorg.conf
```

---

### Post by abujenin on 2008-05-01
Output is attached.

---

### Post by Rocket2DMn on 2008-05-01
OK, I think we have tried pretty much everything.  I know other people have had issues after upgrading from Gutsy to Hardy, regardless of video card or system specs, so you want to consider backing up all your important stuff and installing Hardy fresh.  Compiz has just been such a problem for people, I think it's more trouble than it's worth.  So again, it may be time to consider a fresh install of Hardy.

---

### Post by bulletgani on 2008-05-03
I did a fresh install of Ubuntu hardy ....... the same behavior is repeating with nvidia driver.

I can get the machine to shut down EVERYTIME about 1 min into this video.

[http://www.youtube.com/watch?v=bd2B6SjMh_w](http://www.youtube.com/watch?v=bd2B6SjMh_w)

---

### Post by bulletgani on 2008-05-03
Looks like this is not ubuntu related.

[http://www.fixya.com/support/t372407-ecs_geforce6100sm_m_powers_off_without](http://www.fixya.com/support/t372407-ecs_geforce6100sm_m_powers_off_without)

---

### Post by abujenin on 2008-06-04
I fixed it; no more abrupt shutdowns after I replaced the 450W power unit with a 550W one. 
Nvidia drivers installed with EnvyNG gave me an error of different kernel module than the installed drivers, so I installed the package provided by Nvidia website, which builds the kernel module. But upgrading the kernel requires running that package again.
The GPU was also heating up to 60 C + so I installed two fans, which cooled down the heatings but didn't stop the shutdowns unitl I replaced the power supply.

Thanks for all your help and patience on this problem.

---

### Post by Rocket2DMn on 2008-06-04
Glad you got it working, it WAS the power supply like I thought :)
Happy Ubuntu-ing!

---

