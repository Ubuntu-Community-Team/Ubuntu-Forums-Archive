---
title: "Ubuntu crashes very often"
date: 2014-02-02
forum: General Help
---

### Post by DanyalDenyo on 2014-02-02
I've been using ubuntu on my Sony Vaio VPCS1 laptop for main OS for some time now. I love ubuntu except it crashes way too often. Google Chrome and Chromium makes it crash very easily especially when running flash. I've switched to Firefox and it makes it crash less but I still get crashes every now and then. The screen freezes first, I can only move the mouse cursor but the computer doesn't respond to any clicks, audio keeps playing for a minute or so until the computer completely locks up. It crashes the same way every time. The same thing happens every time I go to suspend. I am also to wake the computer up from suspend.

Today it kept logging the same message on syslog for around half an hour.

Feb  2 13:44:11 levent-VPCS13DGX whoopsie[5278]: whoopsie 0.2.24.1ubuntu1 starting up.
Feb  2 13:44:11 levent-VPCS13DGX whoopsie[5278]: Using lock path: /var/lock/whoopsie/lock
Feb  2 13:44:11 levent-VPCS13DGX whoopsie[5288]: whoopsie 0.2.24.1ubuntu1 starting up.
Feb  2 13:44:11 levent-VPCS13DGX whoopsie[5288]: Using lock path: /var/lock/whoopsie/lock
.
.(kept doing it)
.
Feb  2 14:13:56 levent-VPCS13DGX whoopsie[4567]: whoopsie 0.2.24.1ubuntu1 starting up.
Feb  2 14:13:56 levent-VPCS13DGX whoopsie[4567]: Using lock path: /var/lock/whoopsie/lock
Feb  2 14:13:56 levent-VPCS13DGX whoopsie[4579]: whoopsie 0.2.24.1ubuntu1 starting up.
Feb  2 14:13:56 levent-VPCS13DGX whoopsie[4579]: Using lock path: /var/lock/whoopsie/lock
Feb  2 14:17:01 levent-VPCS13DGX CRON[4634]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

Thank you!

---

### Post by PotatoHead007 on 2014-02-02
Not sure what the log means, but it sounds like your RAM fills up. How much RAM do you have, and how full is it when it freezes? Could also be a processor/graphics issue.
Also, what Ubuntu version are you using?

**Edit: **This link[ [http://askubuntu.com/questions/396584/system-crashes-frequently](http://askubuntu.com/questions/396584/system-crashes-frequently) ] comfirms what i said, it could be a problem with your graphics driver. What graphics card do you have, and is the driver updated?

---

### Post by DanyalDenyo on 2014-02-02
Thank you and sorry for the lack of information on my part.

My Ubuntu version is 64-bit 13.10. Computer has 8 GBs ram installed. It has 103 GBs free on Ubuntu partition. Graphics card is NVIDIA® GeForce® 310M GPU. Graphics driver is Gallium 0.4 on NVA8.

I run System Monitor and check it regularly. So far I've never seen the RAM get even half full.

I tried to install Nvidia's graphics drivers but they didn't work properly (when booting Ubuntu the splash screen looks unusual, display doesn't work outside lightdm). I am using the default driver Ubuntu installed for my graphics card.

I am going to try the latest nvidia driver again and see how it goes.

---

### Post by PotatoHead007 on 2014-02-02
Ok, RAM is not the problem. When installing the nVidia driver, you might encounter the disability to get a GUI login(due to the fact that the driver may not be supported fully)..
If that happens, you will need these commands to save you(login with CTRL+ALT+F1):

sudo apt-get remove --purge nvidia-*
sudo apt-get install ubuntu-desktop (make sure that you have internet conenction for this)
sudo rm /etc/X11/xorg.conf
echo 'nouveau' | sudo tee -a /etc/modules

What this does is remove the nvidia drivers, allowing you to boot into GUI. Then you can try again, or follow one of these methods: [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)
Hope all goes well :)

Sources: [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html), [http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely), head-bashing experience

---

### Post by DanyalDenyo on 2014-02-02
I downloaded the latest version of nvidia drivers (NVIDIA-Linux-x86_64-331.38) and somehow managed to install them. Ubuntu wouldn't boot for several times, kept freezing. Being the newbie I am I tried to booth with other ubuntu versions and recovery modes in grub. I was able to boot the os with one of them so I did 

```
sudo apt-get remove --purge nvidia-*
```

it removed all the other nvidia drivers except the one 331.38 which was installed. Tried to boot once more and now I was able to load the GUI.

```
sudo apt-get install ubuntu-desktop
```  --> everything was up to date

Now Ubuntu starts up with a really low resolution splash screen further messed up with random text all around and I get a black screen when I hit ctrl+alt+f1. However it's pretty good in ctrl+alt+F7. 

I want to test this driver because browser performance feels a lot better so maybe it won't crash as much now. Do you think I will have any problems booting the system? How do you think I can fix the terminal issue? 

Thank you!

---

### Post by PotatoHead007 on 2014-02-02
> **DanyalDenyo said:**
> 
I want to test this driver because browser performance feels a lot better so maybe it won't crash as much now. Do you think I will have any problems booting the system? How do you think I can fix the terminal issue? 

Thank you!

Glad to hear you got out of the driver nightmare :P
I have never had this problem, but i found links that should definitely fix it :) try these:

[http://myubuntutrix.blogspot.com/2013/03/fix-low-resolution-on-bootsplash-screen.html](http://myubuntutrix.blogspot.com/2013/03/fix-low-resolution-on-bootsplash-screen.html)
[http://askubuntu.com/questions/127851/change-boot-screen-resolution](http://askubuntu.com/questions/127851/change-boot-screen-resolution)

Those instructions should work. If they don't, i will keep digging :P 
Btw the Ctrl+Alt+F1/F2/F3/F4/F5/F6/F8/F9 are all for opening a console login. Using F7 will get you into GUI, and it should actually do that without promt.

Again, hope this fixes your problems :)

---

### Post by DanyalDenyo on 2014-02-03
Couldn't boot the system (with NVIDIA-Linux-x86_64-331.38.run installed) after I tried to restart the second time and after a lot of trouble I was able to go back to an older Nvidia driver 319(proprietary,tested). My terminal looks like this:

[http://sdrv.ms/1bigxmc](http://sdrv.ms/1bigxmc)

Looks horrible and hard to see but at least I can tell what I am typing. Sometimes some windows look entirely black when alt+tabbed into. Minimizing and maximizing again fixes it.

However it is much better overall. Computer runs a lot cooler, suspend works, performance is much better and no crashes yet. I wonder if there's a better driver than the nvidia319(proprietary,tested). There's an nvidia-319-updates(proprietary) driver on the list. One has -updates other is tested but it's the same version :confused: What's the difference? 

I found this driver [http://packages.ubuntu.com/precise-updates/nvidia-331-updates](http://packages.ubuntu.com/precise-updates/nvidia-331-updates)

Would installing it from that package be any different from installing 331.20 manually from Nvidia?

Also, what driver version works best with 64bit Ubuntu 13.10 in your experience?

Again, thanks for the help :KS

---

### Post by PotatoHead007 on 2014-02-03
> **DanyalDenyo said:**
> There's an nvidia-319-updates(proprietary) driver on the list. One has -updates other is tested but it's the same version :confused: What's the difference? 

I found this driver [http://packages.ubuntu.com/precise-updates/nvidia-331-updates](http://packages.ubuntu.com/precise-updates/nvidia-331-updates)

Would installing it from that package be any different from installing 331.20 manually from Nvidia?

Also, what driver version works best with 64bit Ubuntu 13.10 in your experience?

Again, thanks for the help :KS

I think -updates means that it just has some bug fixes or something, but am not sure.
That packet looks the same, maybe it has some modifications for Ubuntu.. I used the one that you used(NVIDIA-Linux-x86_64-331.38.run) and, after installing an extra drive from System settings > Additional drivers, it fixed it all. 
Here is a link to one that should work flawlessly(although, in this world, its rare :P): [http://packages.ubuntu.com/precise/nvidia-current](http://packages.ubuntu.com/precise/nvidia-current) I know its older, but it seems to work nontheless. 
Honestly, i have 0,0% experience with Ubuntu 13.10 as i use 12.04 LTS, but i do know something about the system etc. 
Hope i helped, and if not, just say it :P

---

