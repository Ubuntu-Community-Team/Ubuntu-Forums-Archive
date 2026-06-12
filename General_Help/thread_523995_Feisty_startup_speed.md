---
title: "Feisty startup speed"
date: 2007-08-12
forum: General Help
---

### Post by msingletary on 2007-08-12
I just installed a fresh copy of Feisty the other night and I've been plagued by extremely slow startup times. It probably takes close to 1.5-2 minutes to start up the system, and even longer from hibernation. I read something online which recommend installing a package called 'bootchart' and posting the results here. I couldn't figure it out on my own so I was hoping that someone else might be able to take a look and help out. The chart is attached.

Beyond that I've checked out a few threads on here with some suggestions but honestly they are probably a bit beyond what I'm comfortable and willing to do to get this fixed.

I've disabled un-needed services and the like, but I've never had Ubuntu or any other distro take this long to boot before.

Thanks in advance for the help!

---

### Post by darksidedude on 2007-08-12
what kind of hardware are we looking at, processor speed, front Side bus speed?
well I run a AMD athlon 2000xp (1.67hhz) with 1.3gb of ram and it boots up in about 45 sec

have you tried xbuntu, or even fluxbuntu?

---

### Post by msingletary on 2007-08-12
I'm running an Intel Core2 Duo 1.73GHz processor with 533MHz front side bus. I have 2GB of RAM in the system as well. Full system specs available [here]("http://www.sonystyle.com/webapp/wcs/stores/servlet/ProductDisplay?catalogId=10551&storeId=10151&langId=-1&productId=8198552921665171953").

I haven't tried any other version... should I?

---

### Post by darksidedude on 2007-08-12
well gnome is a bit "slow" (let the hate mail commence) :lolflag:
Kubuntu was faster for me  since ( IMO) QT is faster than GTK

as a bench mark you should try xubuntu or fluxbuntu ( not suported by ubuntu its what they call a "fork") they all have the same base of ubuntu

---

### Post by msingletary on 2007-08-12
> **darksidedude said:**
> well gnome is a bit "slow" (let the hate mail commence) :lolflag:
Kubuntu was faster for me  since ( IMO) QT is faster than GTK

as a bench mark you should try xubuntu or fluxbuntu ( not suported by ubuntu its what they call a "fork") they all have the same base of ubuntu

I'm sorry... I guess I wasn't clear as to what sort of speed I'm referring to. I meant the actual startup speed of the system.. boot-wise. When booting up (prior to logging in) it takes quite some time for things to get started. I've hit ALT-F1 and found that it's just checking for an existing state (hibernation?) prior to booting and that seems to take a while. Could that be causing the problem? If so, how can I turn hibernation off so that it's not even checked?

The OS itself (once booted and logged in) is quite snappy on this system and I've got no complaints. It's just that it takes nearly 2 minutes to get booted before I even get a login screen. Ugh!

Thanks again for the help and sorry for not being clear.

---

### Post by msingletary on 2007-08-15
bumpity bump?

---

### Post by Leang on 2007-08-23
i'm having the same problem as you are. wierd thing is, the first time i installed feisty, boot up time was definitely under one minute. i messed up my compiz-fusion install and decided to start over completely. i got compiz-fusion to run perfectly, but i noticed that my boot up time increased to about 3 minutes. i noticed this slowdown before installation of compiz-fusion so that's not the problem.  i hope we can figure something out.

---

### Post by kiv on 2007-08-24
I am having the same problem on a similar spec laptop..

intel core 2 duo (533fsb)
2gb ram

startup take a few mins and slows down once the orange bar gets 1/3 of the way. 

then for a min or so there is no hard drive activity and the wireless internet light blinks rhythmically.

The install is fresh & I'm not sure what to do..

help!?

---

### Post by gobbles414 on 2007-08-24
Hi all,

It has been my observation that boot-times increase significantly when restricted drivers are in use. Try disabling them and rebooting. Then you can decide if the drivers are worth the increased boot-time.

---

### Post by kiv on 2007-08-24
> **gobbles414 said:**
> Hi all,

It has been my observation that boot-times increase significantly when restricted drivers are in use. Try disabling them and rebooting. Then you can decide if the drivers are worth the increased boot-time.

It was slow on the first boot even.

---

### Post by poe503 on 2007-08-24
I just swapped motherboards from a Willamette 1.7gb P4, 400fsb to a Northwood 2.4 P4, 533 fsb.  I used the same hard drive and Ubuntu booted up without a complaint and everything is snappier except for bootup time which remains the same.  I'll check on the restricted drivers.  Thanx.

---

### Post by kiv on 2007-08-24
> **poe503 said:**
> I just swapped motherboards from a Willamette 1.7gb P4, 400fsb to a Northwood 2.4 P4, 533 fsb.  I used the same hard drive and Ubuntu booted up without a complaint and everything is snappier except for bootup time which remains the same.  I'll check on the restricted drivers.  Thanx.

are you uising wireless internet?

cos mines blinks alot while theres no hdd activity during the period of slow bootup.

---

### Post by poe503 on 2007-08-24
Nope, just 56k dialup.

---

### Post by misfitpierce on 2007-08-24
I got Feisty 32 bit on 64 bit processor with wifi and all and it boots in about 30 seconds tops

---

### Post by apetresc on 2007-08-24
The bootgraph output indicates that ipw (the wireless driver) is staying active for a lot longer than it should be. This is a common problem if dhcp'ing for a network address takes a long time. Try disabling the network card and rebooting, and see if it still takes forever when it's not trying to connect to a network.

---

### Post by G3XOI on 2007-08-24
The same thing happens to me on my laptop, I think it's something to do with the wireless switch! Because when I turn it off and restart it boots up fine, but as soon as i turn it on and restart the start time lags.

---

### Post by kiv on 2007-08-24
> **G3XOI said:**
> The same thing happens to me on my laptop, I think it's something to do with the wireless switch! Because when I turn it off and restart it boots up fine, but as soon as i turn it on and restart the start time lags.

yes its the same on mine..turn off wireless.. boots fine!

is there a fix?

---

### Post by poe503 on 2007-08-24
> **poe503 said:**
> I just swapped motherboards from a Willamette 1.7gb P4, 400fsb to a Northwood 2.4 P4, 533 fsb.  I used the same hard drive and Ubuntu booted up without a complaint and everything is snappier except for bootup time which remains the same.  I'll check on the restricted drivers.  Thanx.

I timed it and it takes 35 seconds to boot to login and then 5-10 seconds to fully install the window.  I'm not complaining about the bootup time but its interesting that bootup doesn't speed up with the faster system.

---

### Post by Batuhan on 2007-08-24
I had the same problem, my machien was trying to get an adress from unconnected ethernet and it was literally waiting for 30-40 seconds.
When I install feisty, the first thing I do is:

```
sudo update-rc.d -f networking remove
```

And it solves my slow boot problems.

---

### Post by kiv on 2007-08-25
> **Batuhan said:**
> I had the same problem, my machien was trying to get an adress from unconnected ethernet and it was literally waiting for 30-40 seconds.
When I install feisty, the first thing I do is:

```
sudo update-rc.d -f networking remove
```

And it solves my slow boot problems.

hey thanks. I have found turning off my wireless adapter before it boot ubuntu fixes the problem.. however i have to turn it back on once in ubuntu which is a slight pain but no biggy.

what does that command do ? disable netowrking altogether? cos i need my wireless connection.

---

### Post by apetresc on 2007-08-25
> **kiv said:**
> what does that command do ? disable netowrking altogether? cos i need my wireless connection.

Nope, "rc.d" is merely Ubuntu's startup manager; it brings up processes during boot. Basically you wrap up everything that needs to be brought up in "rc scripts", and then assign them runlevels (boot stages) during which they should be run. Removing networking from rc.d simply disables its startup script. Your networking is still there, it's just not rc.d's problem anymore. The problem that everyone was having is that rc.d was waiting for the wireless network to come up (which was taking a long time) before it would bring up other network-related proccesses, hence the long wait.

So in short, the line is perfectly safe, the only difference is that you'll have to manually connect to the network once your machine is done booting up.

---

### Post by rcoconnell on 2007-08-26
I applied this successfully to my fresh install of Feisty.  Unfortunately, recovering from hibernate still seems slow.  Is there a tool like bootchart to see what's going on?  Is there a way to apply this fix to hibernate as well?

---

### Post by psg6801 on 2007-08-26
I was experiencing a boot time of over 2 mins on a fresh install of Feisty. Did an alt F1 on boot and found it was hanginf on " Configuring network interfaces". I followed the directions in this post  [http://ubuntuforums.org/showpost.php?p=2419738&postcount=16]("http://ubuntuforums.org/showpost.php?p=2419738&postcount=16") and my boot time dropped to 25 secs!!!!! woohoo!!!

---

