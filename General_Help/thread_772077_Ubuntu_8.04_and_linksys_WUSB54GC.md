---
title: "Ubuntu 8.04 and linksys WUSB54GC"
date: 2008-04-28
forum: General Help
---

### Post by glore2002 on 2008-04-28
Hello!
I've just installed Hardy Heron but I can't find out how to configure my Wi-Fi WUSB54GC adapter properly. If someone can help me with the steps to follow, I will really appreciate that.

Thanks in advance,
glore2002.-

---

### Post by astro space zombie on 2008-04-28
I'd like to know this too, because I tried to use the old fix from Gutsy but it doesn't work with Hardy.

---

### Post by chas2007 on 2008-05-02
I have my wusb54gc working with Hardy, Gnome desktop.  I used the install script for Gutsy, as provided in the hendricks thread.  When you run it per instructions, it will indicate that wlassistant fails to install.  Ignore that.  When it's finished, you can set up the wireless via Sytem/Administration/Network.

Works like a charm for me! :)\\:D/8)

---

### Post by pichulines on 2008-05-05
Hi,

I have my wusb54gc working in hardy just plugging the device (working with module rt73usb). It seems to work properly but at 2mbps... which is a low speed.

Does anybody know how to config it to get a higher speed? thx

---

### Post by chas2007 on 2008-05-07
> **pichulines said:**
> Hi,

I have my wusb54gc working in hardy just plugging the device (working with module rt73usb). It seems to work properly but at 2mbps... which is a low speed.

Does anybody know how to config it to get a higher speed? thx

I don't know specifically how to improve the speed.  Hardy didn't work with my wusb54gc when I booted it up with it plugged in, so I installed the driver via the script that Hendricks wrote for Gutsy.

It worked after that.  I can't tell you what the speed is, because wlassistant didn't install with the script.  I would say the speed if fast/normal, it's worked very well so far.

If no one else offers advice on the speed issue, you may want to try installing the driver with the Hendricks Gutsy script.

---

### Post by smittycity on 2008-05-12
I'm having the same problem, been banging my head on it for a while. Had it working with gusty using the script and now I cant even get the poor thing to be recognized. I don't understand how there can be so many mixed results when everyone is using the same setups. Are there different versions of the script (more than one for gusty and one for feisty) and if so can someone link the newest one pleeease. Also, when I used the script I get a weird error which told me that lib6 somethinerother was broken, I seemed to have fixed it by updating it with the package manager but still no wireless. Just thought I'd throw it out there

---

### Post by smittycity on 2008-05-12
:-D :-D :-D :-D :-D :-D :-D :-D

I spoke just a little too soon! First of all, this is the first time I have ever fixed something and posted about it so I'm all proud n stuff. (By the way I am proudly posting from my laptop connected via wusb54gc!)

Ok, I was getting an error when I ran:

ndiswrapper -m

that I dont want to try to reproduce now, but it sorta pointed mt to the file ext/modprobe.d/ndiswrapper, the contents of this file should look a little like this

install usb:v13b1p0020d*dc*dsc*dp*ic*isc*ip* /sbin/modprobe ndiswrapper
alias wlan0 ndiswrapper

this is the device id: 13b1p0020 of my access point and before I edited this file it read as 13B1p0020, in a sort of desperate move I changed the B in the id to be lower case thinking that maybe it was case sensitive and low and behold it was. I made this change and ran

ndiswrapper -ma
ndiswrapper -mi

and rebooted. Now it works!

I wouldn't be at all surpized if this wasnt everyones problem but it's worth checking out. If anyone has any idea what caused this I'd be happy to know, I can see the random capitalization of things causing plenty of problems in the future.  

Well, I'm off to do internetty things with my laptop!

---

### Post by pichulines on 2008-05-30
finally I know how to speed up the wireless connection. After plug the device I execute this in a terminal:

```
sudo iwconfig wlan0 rate 54M
```

Then I restart the connection through the NetworkManager, clicking again on the wireless network I want to use.

I suppose there is a method to do this automatically always I plug the device but I have to find out.

---

### Post by CommNavRizzo on 2008-06-01
[COLOR="Red"]EDIT:[/COLOR] I reinstalled Hardy and the wireless card began working as advertised.  I don't know why it did not work when I plugged it in (after already having Ubuntu installed), but after the reinstall, it noticed the card right off the bat and I'm using the computer now to post this.

Hi all,  I'm new to the forums and this is my first time with Ubuntu.  I've used Linux distros before, but it has been a few years.  Anyway...

I was wondering if you could post a link to the "hendricks" gusty script that got the wusb54gc working.  I have plugged mine in, but it does not seem to work out of the box.

I did a search for this script, but unfortunately I did not find it myself.  Any assistance would be appreciated.  Thank you.

-J

---

### Post by kivnic on 2008-06-09
Hi everybody,
I'm getting some really mixed results, and I'm new to Ubuntu in general so I have no idea what else to try. When I installed the OS, the card seemed to be autoinstalled okay, using the rt73usb. One of my two wireless access points showed up in the list under the network icon in the upper right of the screen. I'd tried to connect to this WPA WAP using the correct password, but no luck. Then I tried manually connecting to my other WPA WAP. Still no luck. So then I changed the security on one of my WAPs to WEP... still nothing.

* Why did it only seem to autodetect one of my WAPS (two SSIDs are broadcast, only one appeared on the list)

* How do I find out the reason it's not connecting?

* Am I using the best driver for this task?

* Has anyone else successfully connected to a WPA WAP using this configuration?

Thanks in advance.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=73487&d=1213047149[/IMG]

---

### Post by kivnic on 2008-06-09
One more question - from reading the forums, I get the impression that my wireless password won't be remembered even once this is working. I'd like the password to be saved and for the wireless adapter to autoconnect for every user as soon as the machine turns on. Any suggestions?

---

### Post by Tom--d on 2008-06-09
Ndiswrapper + rt73 windows driver = Wireless is perfect! :D

---

### Post by kivnic on 2008-06-10
> **Tom--d said:**
> Ndiswrapper + rt73 windows driver = Wireless is perfect! :D

I gave Ndiswrapper a shot. I can see my access points, but don't have any luck connecting to them - even when I turn off all security. It's really strange because I have about 4 different computers connected to those WAPs without any problems.

---

### Post by calman on 2008-06-21
> **CommNavRizzo said:**
> [COLOR="Red"]EDIT:[/COLOR]I was wondering if you could post a link to the "hendricks" gusty script that got the wusb54gc working.

dunno if it's too late but here it is:

[http://www.uluga.ubuntuforums.org/showthread.php?t=516649](http://www.uluga.ubuntuforums.org/showthread.php?t=516649)


> **pichulines said:**
> It seems to work properly but at 2mbps... which is a low speed.

Does anybody know how to config it to get a higher speed? thx
That's EXACTLY the problem I'm having, but the updates download at a horrifying 35 kb/s...sometimes, though, they go at 400 kb/s but then jump down to 35.  This device's drivers for Ubuntu are just really unstable, I can't believe some people get out of the box 100% support.  Everyone has a different problem with it...

---

### Post by bbboB on 2008-07-18
I just upgraded to Hardy yesterday and ran into some of the same problems as some of you in this thread.
Prior to the upgrade, I was using the driver that came with the antenna and ndiswrapper.
The conclusion I've come to is that there is a variance in the Linksys antenna and for some, the rt73usb driver will work.
In my case, I had a whole whoppping 1-2 Mb connection speed after the upgrade...LOL
The connection information after a right click of the Network Manager icon revealed that my driver was the rt73usb.
I reinstalled the rt73 driver that came with my antenna into ndiswrapper and gave it a reboot.
Things seem fine now with a pretty steady 24Mbs (I am the length of the house from the router) and the same speed is confirmed with XP.
The only problems I'm encountering now is that if the connection is broken, I can't get it to reconnect without doing a reboot.  Any suggestions?

---

### Post by bossfn on 2008-09-15
Wow. Thank you SO much. This is the best tip of all time. 5x faster transfers on the WLAN instantly.


> **pichulines said:**
> finally I know how to speed up the wireless connection. After plug the device I execute this in a terminal:

```
sudo iwconfig wlan0 rate 54M
```

Then I restart the connection through the NetworkManager, clicking again on the wireless network I want to use.

I suppose there is a method to do this automatically always I plug the device but I have to find out.

---

### Post by Michl on 2008-09-17
> **chas2007 said:**
> I have my wusb54gc working with Hardy, Gnome desktop.  I used the install script for Gutsy, as provided in the hendricks thread.  When you run it per instructions, it will indicate that wlassistant fails to install.  Ignore that.  When it's finished, you can set up the wireless via Sytem/Administration/Network.

Works like a charm for me! :)\\:D/8)

Please, please, can you give the steps you followed.
I follow the hendricks, thread, downloading and
extracting the gutsy script, but I just cannot
get anything to work.  Nothing changes in the
network applet in Heron.

Does ndiswrapper install automatically?  This seems
to be one of the problems when I follow the instructions.

Thanks for ANY help, pointers, etc.

---

### Post by chas2007 on 2008-10-08
Michl,

I don't remember anything more than the instructions in the Hendricks thread.  BUT... not to long ago I had to do a reinstall.  This time, I did the install while the WUSB54GC was plugged into the computer... and Voila!  It just worked, without my having to run a script or do anything.

That is, the  WUSB54GC worked, was recognized as a functioning piece of hardware.  I still had to configure the name of my wifi network and security code, but that was easy.

It's been working fine ever since. :)

---

### Post by chas2007 on 2008-10-08
> **bbboB said:**
>  [...] The only problems I'm encountering now is that if the connection is broken, I can't get it to reconnect without doing a reboot.  Any suggestions?
When that happens to me (not very often, but sometimes) I just unplug the WUSB54GC, wait a moment, and plug it back in.  It reconnects and starts working, without having to reboot.  It works with Hardy, even though it wouldn't do that with Gutsy.

---

