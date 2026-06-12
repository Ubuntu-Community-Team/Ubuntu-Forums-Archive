---
title: "Ubuntu slow compared to Windows XP"
date: 2007-08-07
forum: General Help
---

### Post by megagram on 2007-08-07
Hi everyone! I am a regular Mac user but my Mac is gone for a few weeks so I've installed Ubuntu on to an old Dell Optiplex with a 2.2GHz P4, 512MB DDR333 RAM and a 40 GB HD. I also installed WinXP just in case.

I absolutely love Ubuntu and absolutely detest using Windows but I find WinXP to be considerably more responsive on this machine in comparison to Ubuntu. Web pages load faster, photos load much faster and overall, the experience is just more 'zippy' on XP.

Is there a reason for this that is obvious? Does Ubuntu need more resources than XP to run? Should I consider a different Linux distro?

Any help and input would be greatly appreciated thank you!

Graham

---

### Post by FleetAdmiral74 on 2007-08-07
Hmm...with your specs, this Ubuntu distro should be working ok. If you want to stick with an Ubuntu varient, try Xubuntu. If that is still slow...its likely there is something with the hardware/drivers that is slowing you down.

I kinda know what you mean, but this was because I knew tons about XP and knew how to slim it down. Was living on 17 processes most of the time, so switching to an OS where I knew nothing did made it seem kinda slow since I could not customize.

Stick with it, I think you will be pleased in the end with a nice fast system.

---

### Post by yogo on 2007-08-07
I have a Dell with almost the same specs except for double the ram and my processor is 2,53 but Ubuntu flies with ease on my PC. XP was ok but Ubuntu is faster.

---

### Post by hardyn on 2007-08-07
non-ideal video drivers can really drag a graphical system down

---

### Post by Sunflower1970 on 2007-08-07
I have pretty much the same specs (just more RAM) as the above, too, and my Dell (it's a Dimension 8200) runs much faster than XP...
I thought I read somewhere that Optiplexes are a bit more temperamental trying to get Linux on it...some people on the Dell forums were having trouble with Optiplexes..(I check the Linux forum from time-to-time..)

Don't Optiplexes normally have an Intel graphics card in it...? Has that been configured properly..? Isn't there something called the 915solution or something like that for Intel cards in Synaptic..?

---

### Post by megagram on 2007-08-07
Hey thanks so much for the help guys. I'm guessing it might be the graphics card/drivers then. It would seem to make sense as my main complaint is the general feel of 'lagginess' compared to XP. The optiplex I am running has an on-board 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (stolen from HW Info) which in turn is using the i810 driver for X.org conf. This was all done automatically at install time though. Is there more I should be doing?

---

### Post by jeffmills on 2007-11-15
> **megagram said:**
> Hey thanks so much for the help guys. I'm guessing it might be the graphics card/drivers then. It would seem to make sense as my main complaint is the general feel of 'lagginess' compared to XP. The optiplex I am running has an on-board 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (stolen from HW Info) which in turn is using the i810 driver for X.org conf. This was all done automatically at install time though. Is there more I should be doing?

I have the same feeling... with my Ubuntu 7.10 installation and ATI Radeon X850XT. It's just so slow compared to WindowsXP. 

The point about customizing is good, but not in this case. I am tallking about a clean WindowsXP installation vs a clean Ubuntu 7.10 installation.

I think it has to do with the fact that GUI interaction is just faster on Windows in general, because it is part of the kernel. While in Linux, it runs in user space (right?) Therefor, I don't think Linux can become as fact without some major changes.

---

### Post by pikaia on 2007-11-19
I am experiencing the same slowness as compared to XP.

I do know how to slim XP and am running it VERY slim.  But even things such as typing online or email often result in lag, which almost NEVER happened with XP.  I like Ubuntu and want to stick with it, but I'm kind of annoyed by the decrease in responsiveness.  

Slower boot
Slower page load in Firefox

XP loads in ~30 seconds
Ubuntu ~1.5 minutes.

I've done some searches but haven't found how to slim down the startup to increase responsiveness, any ideas?  I have updated the nvidia drivers, and my machines specs are AMD X2 4200, 2GB RAM Nvidia 7600 GS, so there should be no reason for lag.

thanks for any insight.

Oh, running Feisty.

---

### Post by anoopjohn on 2008-02-26
I have the same experience here on my IBM T40 with 512MB RAM. One thing I have noticed is that firefox hogs a lot of memory. So does simple applications like gedit. I have tried xfce and it was faster but firefox and gedit memory usages remained the same. But I like gnome and would like to keep it. Are there settings in gnome that we can change to increase the performance like the settings in XP - best appearance options and best performance options?. I have also noticed that there are quite a lot of applications running in the background in ubuntu. I am attaching my ps -A output with this. The only server process that I have started (I think) is the dictd process. Is there some way in which I can just turn these on and off when they are required. Also how do I know which process is required and which is safe to turn off? I am also attaching a top output showing the memory usage. What should I do to speed up my ubuntu system? I am using the generic kernel. Should I switch to i386? If i switch to i386 kernel, will that result in compatibility issues with existing drivers or applications?

---

### Post by azadpanchi on 2008-02-26
I am running a Dimension 2400 with just a little bit more RAM and similar processor.  Even though some of memory is not very good Ubuntu flies for me and I have LAMP, samba, SSH all running in the back ground.  I really didn't change any drivers, everything was detected fine without a problem.

I would play around with the drivers to see what I can get.  I would also try to see if CPU or memory being maxed.  Try 'free -m' and also do 'top' and see if CPU is under a high load.  Based on that you can do the following wil in top, shift+p to sort via process and shift+m to sort via memory usuage.  Also you can type 'ps aux' to see all the process being run.  Maybe this way you can narrow down if there is a program hogging the resources.  

Also I would goto System->Administration->Services and make sure only the services you need are starting up.  Be sure to look through /var/log/messages for a recurring theme, you are looking for any errors or strange comments over and over again.  I am not sure what sort of setup you have but it cannot hurt to run badblocks to see if there are any badblocks on the hard drive.

Just a few things I would do.

---

### Post by azadpanchi on 2008-02-26
> **anoopjohn said:**
> I have the same experience here on my IBM T40 with 512MB RAM. One thing I have noticed is that firefox hogs a lot of memory. So does simple applications like gedit. I have tried xfce and it was faster but firefox and gedit memory usages remained the same. But I like gnome and would like to keep it. Are there settings in gnome that we can change to increase the performance like the settings in XP - best appearance options and best performance options?. I have also noticed that there are quite a lot of applications running in the background in ubuntu. I am attaching my ps -A output with this. The only server process that I have started (I think) is the dictd process. Is there some way in which I can just turn these on and off when they are required. Also how do I know which process is required and which is safe to turn off? I am also attaching a top output showing the memory usage. What should I do to speed up my ubuntu system? I am using the generic kernel. Should I switch to i386? If i switch to i386 kernel, will that result in compatibility issues with existing drivers or applications?

This may sound crazy but just get a little more memory and you will be very surprised, 256 mb more will make a big difference for you.  Also run memtester, swap is being used before getting closer to maxing out physical memory, although memory allocation is not so cut and clean but I would test just the same.  Also if you are running memtester badblocks couldn't hurt either.

Try using Opera if you are running other things and you are really being slowed down, it has a smaller memory foot print.

---

### Post by xeth_delta on 2008-02-26
> **jeffmills said:**
> I think it has to do with the fact that GUI interaction is just faster on Windows in general, because it is part of the kernel. While in Linux, it runs in user space (right?) Therefor, I don't think Linux can become as fact without some major changes.

I am not sure this would really be a reason for a noticeable speed difference, if Windows works that way, anyway (I do not think the kernel of the OS would take care directly of the GUI, even though Windows was thought mainly as a GUI OS).

Years ago, I first started using RedHat Linux. It was a bit sluggish at the beginning. I am trying to remember how the speed improved. I remember installing proper nVidia drivers and compiling a newer kernel. IIRC there was a speed benefit especially noticeable when compiling a 2.6 version kernel. I will post here if I recall what else I did.

Closer to the topic, I have Ubuntu installed on three computers. They seem to be quite responsive and fast. The old one is based on an Athlon XP 1600+ (1400 MHz), 512MB ram, GeForce2 GTS 32MB. The other too ar far newer. The fastest distro I've used has to probably be Gentoo.

To the OP. Are you using any 3D accelerated window manager (compiz/beryl)? If that is the case, then you should make sure your video card driver is properly configured. You can try:
```
glxinfo | grep -i direct
```
If you have hardware acceleration the answer on the terminal should be a simple "yes".

---

### Post by ellalan on 2008-02-27
Hi
Mine is PentiumIII 1999 model, it was pre-installed with W98. I upgraded to XP last year and I was totally disappointed. Recently I installed Ubuntu and the old machine works like new. I have only 10GB HD and 512MB RAM but the components in the machine are solid. Ubuntu is fast, Internet doesn't hangs,stable. All in all Ubuntu is superior to XP and the support from the Forum is fantastic. I will never miss XP.:)

---

### Post by anoopjohn on 2008-02-28
Thanks for all your replies. 

I have implemented some of the configurations as mentioned in

[http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/](http://kmandla.wordpress.com/2007/10/20/howto-set-up-gutsy-for-speed/)
[http://ubuntuforums.org/showthread.php?t=89491&highlight=startup+processes&page=2](http://ubuntuforums.org/showthread.php?t=89491&highlight=startup+processes&page=2)

I also made configurations to the theme. Took out wallpaper, took out icons from menus. The system is faster but firefox still has issues. I downloaded opera and am trying it out.

I stopped the following processes from starting up
anacron
atd
apport
bluetooth
cupsys

Took down /dev/tty3 to /dev/tty6
Cut down to single desktop
Removed the trash applet
Removed the tracker applet
Removed the deskbar applet and the user-switcher applet

Kills nm-applet after logon

Overall the system feels a lot more faster with lot more memory freed up for lot more simultaneous applications. But firefox always plays the spoil sport. It is because I tend to keep a few (around 15) tabs open. 

I have not set the vm.swappiness yet. I have however set the kernel parameters for speeding up the broadband connection. I have not run any tests with or without the params though.
[http://ubuntuforums.org/archive/index.php/t-624684.html](http://ubuntuforums.org/archive/index.php/t-624684.html)

I will post back with any additional tweaks that I figure out

---

### Post by vanadan on 2008-04-05
try using swiftfox (firefox optimized for speed).. maybe it helps..

---

