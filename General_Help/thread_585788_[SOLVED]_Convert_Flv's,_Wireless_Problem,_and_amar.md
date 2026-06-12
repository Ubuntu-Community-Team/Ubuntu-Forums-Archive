---
title: "[SOLVED] Convert Flv's, Wireless Problem, and amarok problem!"
date: 2007-10-21
forum: General Help
---

### Post by NoSmokingBandit on 2007-10-21
Woot, 3 questions at once. Well, first off, does anyone know of a good program to convert .flv movies to mp4? I like to rip YouTube videos and convert them to play on my psp, but i couldnt find anything to do that.
Second, my wireless connection seems to be uber slow in 7.10. Its a Linksys WUSB54G v4 adapter. Ubuntu recognized it right away and connects to my network, but its slow as molasses. In win xp its normal speed, but ubuntu is really slow on the wireless, i didnt know if there was some tweking that needed to be done or something? Im using frefox witht he exact same setup as i have in xp.
third: I had a problem with this before, but i thought i fixed it so i marked the thread solved, then i realized that i didnt fix it. Anywho, my SB Live card works fine until i install amarok, then the whole thing is moot. Even after i uninstall Amarok. The only cahnge i saw was the in the Volume Control winodw, under File>Change Device, my SB Live card has been moved from the _0_: radio box to the _1_: radio box. I dont see why this would affect it, but apparently it does...
Thanks for any help at all! :D

---

### Post by fragos on 2007-10-21
ffmpeg will convert flv to other formats.  You can install with synaptic.

---

### Post by NoSmokingBandit on 2007-10-22
I installed ffmpeg and ffmpegtheora because it said it was a program that uses ffmpeg, but its not im my menu of programs, is it one of those command-line only programs? If so, what program would you suggest i use? Im kind of a noob, so anything really easy would be great. In the Add/Remove programs list all i found regarding video was iriverter. Would that be what im looking for?
Thanks for the help :guitar:

---

### Post by KCPokes on 2007-10-22
For simplicity, yes FFMPEG is a command-line utility.  That said, it is easy to use even command line.  Just do a quick search and you'll find the command to convert from FLV to MP4.  I realize that most people are more comfortable with using a GUI, and I believe there are a few that interface with FFMPEG or Mencoder, but the commands to use ffmpeg are fairly easy, the utility itself is fast, so I say don't mess with a good thing.  :)

---

### Post by NoSmokingBandit on 2007-10-22
Very cool, thanks a bunch. Now i just need to get my sound working again... Stupid amarok...

---

### Post by NoSmokingBandit on 2007-10-22
For some reason my sound started working again, so i installed amarok and this time it worked. I did however install it this time through synaptic (only because it was already open) instead of the add/remove programs dialog. For now it works, hopefully it still will after a reboot.
So nobody knows why my wireless is slow then i guess... That blows. If i want to run rj45 i need a piece about 30 ft long, which would kill the speed anyway. I guess ill just have to move my desk closer to the router.

---

### Post by KCPokes on 2007-10-22
Most wireless slowdowns are driver related, from what I've seen and what I've read.  I had to blacklist my driver and go with ndiswrapper just to get speeds that were acceptable (G versus B).  How is yours set up now?  

Also, just for reference if you decide to change your mind, you can go up to 100 meters with a Cat5 cable without negatively impacting your network.  That is one LONG cable.

---

### Post by NoSmokingBandit on 2007-10-22
I just plugged in my wireless adapter and ubuntu recognized t, so i assumed it worked as best as it would. I have the windows drivers for it, but i dont know how to disable the linux driver. If you tell me how to do that I can handle ndiswrapper. I can deal with a slow connection, but one of every 3 pages or so times out it takes so long. Thanks for all your help so far, i've looked up the command line stuff for ffmpeg and its not as hard as i thought it would be. Its actually quite nice.

Edit:
I installed the xp driver via ndiswrapper and now its a whole lot faster. My signal strength is all over the place now though. It jumps from 100% to 70% sometimes. The air is really damp right now, theres a storm brewing outside, so ill watch it again after the humidity is less than 80% to see if thats slowing it down. I've had that happen win win xp except it doesnt give a numerical value to the signal strength just a "yup, its on" kinda thing lol.

---

### Post by NoSmokingBandit on 2007-10-23
In an attempt to get smb working i rebooted (still doesnt work, mind you) which caused my wireless driver to reset to rt2500usb. How do i disable that one so its permanently the ndiswrapper driver?
Also after the reboot amarok killed my sound again. This is just getting to be frustrating.

---

### Post by Austin_KW on 2007-10-23
> **NoSmokingBandit said:**
> In an attempt to get smb working i rebooted (still doesnt work, mind you) which caused my wireless driver to reset to rt2500usb. How do i disable that one so its permanently the ndiswrapper driver?
Also after the reboot amarok killed my sound again. This is just getting to be frustrating.

Add the following line to /etc/modprobe.d/blacklist to stop the driver loading
blacklist rt2500usb

Also unload the running rt2500usb driver with
sudo modprobe -rv rt2500usb

Remove & reinsert the dongle and it should use the  ndiswrapper driver

---

### Post by NoSmokingBandit on 2007-10-23
Great, thanks ill try that when i reboot into ubuntu, which i wont be doing until i know how to fix my sound. I cant work without music, the silence drives me crazy.


EDIT:
ok, so i did what you said, now it doesnt recognize the wireless dongle at all. No option for it comes up in any of the network windows. I've never had to work so hard just to get to hear some music and have functioning wireless...

---

### Post by stlcoptony on 2007-10-23
I would also like to try the ndiswrapper solution (I have the intel PRO/Wireless 3945 from linux going right now - I see max of 25 kbps download and it was normally > 500kbps in XP) Can someone tell me specifically how to disable the linux driver, use ndiswrapper (I no nothing about this) and make it stay that way? I've already downloaded the driver from intel

thanks.
tony

---

### Post by Austin_KW on 2007-10-23
> **NoSmokingBandit said:**
> Great, thanks ill try that when i reboot into ubuntu, which i wont be doing until i know how to fix my sound. I cant work without music, the silence drives me crazy.


EDIT:
ok, so i did what you said, now it doesnt recognize the wireless dongle at all. No option for it comes up in any of the network windows. I've never had to work so hard just to get to hear some music and have functioning wireless...

What is the output of "lsmod | grep usbcore"

---

### Post by fragos on 2007-10-23
open /etc/modprobe.d/blacklist file and add drivername using following syntax:
blacklist driver-name

Reboot your box and use lsmod command to show the status of modules in the Linux Kernel.

---

### Post by stlcoptony on 2007-10-23
sorry if this is a stupid question, but how do I know exactly what the driver name is that I am blacklisting? Also, how do I use the windows driver with this ndiswrapper??

thanks,
tony

---

### Post by Austin_KW on 2007-10-23
> **stlcoptony said:**
> sorry if this is a stupid question, but how do I know exactly what the driver name is that I am blacklisting? Also, how do I use the windows driver with this ndiswrapper??

thanks,
tony

```
lshw -C net 
```will show you your network interfaces and the drivers they use. If you know what the wlan is using then you can blacklist it.



```
ndiswrapper -i driver.inf
``` will install the driver described by the windows inf file.

---

### Post by stlcoptony on 2007-10-23
thanks a lot, will try this soon

---

### Post by stlcoptony on 2007-10-23
Ok I got the old driver blacklisted and installed the windows version with ndiswrapper. Now I have no wireless connection at all! The network manager does not seem to recognize that there is a wireless card anymore. Can anyone help me with this/

thanks,tony

---

### Post by Austin_KW on 2007-10-23
> **stlcoptony said:**
> Ok I got the old driver blacklisted and installed the windows version with ndiswrapper. Now I have no wireless connection at all! The network manager does not seem to recognize that there is a wireless card anymore. Can anyone help me with this/

thanks,tony

Did you reboot or manually remove the old driver after blacklisting it. If not you may have both drivers loaded with unpredictable results

---

### Post by stlcoptony on 2007-10-23
I am assuming that no driver is running. I just ran "lshw -C net" and under configuration (where ipw3945 was before) it just says "latency=0"

thanks for all the help,
tony

---

### Post by Austin_KW on 2007-10-23
Is ndiswrapper module loaded. 

```
 lsmod | grep  ndiswrapper
```

If not then manually load the driver & recheck lshw -C net
```
 sudo modprobe -v ndiswrapper
```

---

### Post by stlcoptony on 2007-10-23
thanks, you are a genius. This was the one thing holding me back from getting rid of xp. Will this driver automatically load now, or do I need to do anything else?

thanks,
tony

---

### Post by stlcoptony on 2007-10-23
Ok, let me test it again, the whole computer just locked up!? I've never had this happen without windows being around.....

---

### Post by stlcoptony on 2007-10-23
well the internet started to work at normal speed, @300 - 500 kbps in synaptic, but keeps locking up completely. Do you have ideas or suggestions about this? Also, it appears that I have two drivers installed in ndiswrapper (I installed the GUI). One says hardware IS present, the other says hardware IS NOT present - but I can't uninstall the one without hardware.

thanks,
tony

---

### Post by Austin_KW on 2007-10-23
> **stlcoptony said:**
> thanks, you are a genius. This was the one thing holding me back from getting rid of xp. Will this driver automatically load now, or do I need to do anything else?

thanks,
tony

You can add ndiswrapper to /etc/modules & it will load on boot

---

### Post by stlcoptony on 2007-10-23
any idea why it keeps locking up? Or why I can't uninstall that other driver?

thanks,
tony

---

### Post by Austin_KW on 2007-10-23
The windows driver may not play well with ndiswrapper. But check the output of "lsmod" for any drivers that might conflict with the ndiswrapper.

I am guessing that it must have installed 2 different drivers from the inf file. Not sure why.

---

### Post by stlcoptony on 2007-10-23
Wow, thanks. I have been asking questions on here for like 3 weeks trying to fix this. Spent about half the day today, but at least it is fixed. Seems fine now

thanks,
tony

---

### Post by NoSmokingBandit on 2007-10-23
I dont have time now ( i really need sleep) but ill try that tomorrow, thanks for the help Austin. I blacklisted the rt2500 or whatever its called driver my wireless was using then installed the ndiswrapper driver, but on a reboot it stopped, so running 'sudo modprobe -v ndiswrapper' should work from my limited knowledge.
If i manage to screw that up ill just move my desk over to where i can run cat5. Wireless is a good bit slower than a physical connection anyway.
First priority though is fixing my freaking sound. Its frustrating. I can hear things, but not when i have my favorite player installed. Would it be the kde files hating gnome? idk, sorry im such a linux noob lol. I guess i have to learn somehow.

---

### Post by NoSmokingBandit on 2007-10-24
So nobody has any idea why amarok makes my sound stop working?
I suppose i could try songbird, but that seems to be a bit too big. Amarok has just the features i want, nothing more nothing less.

Edit:
Still havent fixed the wifi. I blacklisted the rt2500usb driver in /etc/modprobe.d/blacklist, installed the windows driver through ndiswrapper's gui frontend (ndisgtk), and could not get a connection for anything. In order to fix it i had to completely uninstall ndis wrapper via synaptic and un-blacklist the rt2500usb driver. Could someone write a step-by-step guide for me, i really dont know what im doing.
From what i gather i must install the windows driver in ndiswrapper, blacklist the current(slow) driver by adding "blacklist rt2500usb" to /etc/modprobe.d/blacklist, then run "sudo modprobe -rv rt2500usb" to unload the rt2500usb driver.

Edit2:
I notice the name of the driver on the linksys cd is also rt2500usb. I thought this might be the problem since i blacklisted that name, so i renamed the files wusb54g (the model no) and changed all the links in the inf to use wusb54g instead of rt2500usb. Installed that driver, unplugged/plugged in the dongle and it says the ndiswrapper driver is working, its a 54mb connection, but i never connect, i just get the two orbs witht eh blue comet thing for a few minutes before it decides its done. So i decided to install the official drivers from the cd; i uninstalled the wusb54g versions and installed the originals, unplugged/plugged in the dongle and the same thing happens.

---

### Post by NoSmokingBandit on 2007-10-25
*cough*
*bump*

---

### Post by NoSmokingBandit on 2007-10-26
Come on, does nobody know how to help me? I've been on xp all week since i cant relly do anything with the uber slow connection.

---

### Post by Austin_KW on 2007-10-26
Ok one more option for wireless connection. There is an older (more stable) linux driver set for the ralink chip-sets. Many of us still use these older drivers but they must be manually configured or configured in the /etc/network/interfaces file. You can not use the networkmanager to set them up but they do work well.

Check [http://rt2x00.serialmonkey.com/wiki/index.php/Downloads](http://rt2x00.serialmonkey.com/wiki/index.php/Downloads) and you want the rt2570 driver (CVS hourly). For instructions on using it look at [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) ; this is for ralink rt73 but is very similar to the rt2570 just use the rt2570 tarball.

---

### Post by NoSmokingBandit on 2007-10-26
great, thanks man, ill reboot into linux right now to try it out. Even if it doesnt work i can start narrowing down where the problem is. Ill let you know what happens after i get it done.


Edit1:
I followed the guide and wheni was dont it loaded ndiswrapper drivers which worked great, but i knew that wasnt what was supposed to happen so i rebooted and now it doesnt recognize my wireless dongle in the network properties.


Edit2:
It pissed me off so i re-installed gusty. You say get the 2570 drivers, but ubuntu loads the 2500 drivers by default. Could this be my problem? Should i try installing 2570 drivers and blacklisting the 2500?

Edit 3(lol):
I looked around and saw that the 2500 drivers are for pci-based wireless devices whereas the 2570 drivers are for usb dongles. So i would assume now that i must install the 2750 drivers and blacklist the 2500 ones. Which i will now do.

Edit 4 (WIN!):
Solved it with a guide from someone (cant remember their name...) now it works great.

/thread.

---

