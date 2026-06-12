---
title: "Firefox freezes randomly - once every 3 minutes"
date: 2012-11-05
forum: General Help
---

### Post by asuastrophysics on 2012-11-05
Hey all,

Recently, my computer seems to have completely fallen apart. The only thing I've done to it is allow update manager to install minimum updates (supported and security releases only). Firefox will freeze, go "dark", stay there for a while, and then come back to life. This happens completely at random. It will go for hours just fine, and then have a fit where it freezes 16 times in 5 minutes. During the freeze, I cannot operate any other program whatsoever. I click on terminal, and it just blinks on the unity taskbar until firefox decides to behave. 

Which log file in ~/var/sys/log/ should I look at to troubleshoot this?

---

### Post by neotrikz on 2012-11-05
Try to clear your cache . is the version of firefox current ?

---

### Post by danelwillis on 2012-11-05
Ive had a smiler problem if i try downloading using Firefox it becomes UN-responsive if the computers not being used an when i say that i mean to get to get a cup of tea the download has frozen i fixed it by updating my Firefox well, i removed it completely then i reinstall it the latest one at the time

---

### Post by asuastrophysics on 2012-11-06
> **neotrikz said:**
> Try to clear your cache . is the version of firefox current ?

Thanks for your responses guys. Cache is cleared and Firefox is at version 15.0

The best way that I could describe this problem is to compare it to a computer with a failing hard drive or similar I/O error. Everything freezes up, much like it does as the hard drive "clunks". Then, once the hard drive corrects itself and reads the sector, everything goes back to normal.

Except my hard drive is perfectly fine and checks out OK. Cables look good, too. 

Anyone know of a particular log file in the directory /var/log/ that might be useful here?

---

### Post by mardybear on 2012-11-06
Hi asuastrophysics.

Has your system really 'fallen apart' or is it just a Firefox problem? Your system never 'freezes' when running other apps and when Firefox is closed? Any difference if you run a different browser, such as Chromium?

Not sure what you mean by go 'dark'? Your not talking about a screensaver issue?

I believe the latest version is Firefox 16.0.2. Are you sure your system is up to date? It should show up as an update...i would recommend upgrading to the latest version to see if anything changes.

Does it happen on a specific website, such as when flash is running (can be very heavy on a system)?

Do you use Firefox sync?

Have you modified any Firefox settings via about:config?

Sorry i can't help with your log file question as i'm not on my Ubuntu system. I'm not sure Firefox keeps a log file...you could try searching through your var/log folder (whatever pathway) but i'm not sure if you would find anything useful.

mardybear

---

### Post by mardybear on 2012-11-07
Forgot to mention, you can also run a system monitor such as 'top' via terminal, sort processes via CPU usage (shift + p), and see if any other processes are eating up your processor(s) when your system hangs.

mardybear

---

### Post by Habitual on 2012-11-07
Create a new user on the system and login as that user, reproduce the elements that caused the initial issue and see if the problem still exists.

---

### Post by asuastrophysics on 2012-11-08
mardybear, thank you so much for your in-depth response. I will answer your questions one at a time, as it is more organized that way. 

> **mardybear said:**
> Has your system really 'fallen apart' or is it just a Firefox problem?
I'm not exactly sure. It appears to lock up the entire OS. By "lock up" and "falling apart", I mean that I cannot launch or open any other program when it happens, and it's difficult just to get to a TTY (CTRL + ALT + F_) screen. 

> **mardybear said:**
> Your system never 'freezes' when running other apps and when Firefox is closed?
That is correct. 

> **mardybear said:**
> Any difference if you run a different browser, such as Chromium?
I honestly haven't tried another browser. I will try one though, now that you mentioned it, and see if there is any noticeable difference. 

> **mardybear said:**
> Not sure what you mean by go 'dark'? Your not talking about a screensaver issue?
I should have explained this better, sorry. I am running compiz on top of Unity, and there is a setting in compiz that "darkens" any currently-running applications if they are not responding. It's a nice visual touch to help alert you that the program you are using has locked up.

> **mardybear said:**
> I believe the latest version is Firefox 16.0.2. Are you sure your system is up to date? It should show up as an update...i would recommend upgrading to the latest version to see if anything changes.
I am currently running Ubuntu 11.10. I have a lot of updates available, so I will go ahead and install all of them and see if that helps.

> **mardybear said:**
> Does it happen on a specific website, such as when flash is running (can be very heavy on a system)?

It appears to only happen when both facebook and youtube are running (adobe flash is the scorn of the computing Earth I tell you! Wouldn't be surprised if it was flash that was causing this)

> **mardybear said:**
> Do you use Firefox sync? Have you modified any Firefox settings via about:config?
I'm not exactly sure what firefox sync is, so I assume not. This is just a stock version of firefox on a freshly-installed (3 months ago) version of ubuntu. No configuration files have been altered in about:config or otherwise to my knowledge.

---

### Post by mardybear on 2012-11-08
Hi again asuastrophysics.

Registered Ubuntu user...that's cool, didn't know that existed.

Wanna go fast - me like. Every user has their own preferences, but if you really wanna go fast you might not want to use Compiz and Unity.

You may have narrowed it down to either Firefox or flash - i agree with you about flash, resource heavy.

Update your system and get back to the group, see if the updates and newest Firefox 16.0.2 run better for you.

Although i believe Firefox is a better browser, you could try Chromium for comparison.

When Firefox is running and your system is giving you problems, run 'top' via terminal and see if a process called plugin-container (something like that) is running. It can easily be disabled.

If the system is freezing exactly every 3 minutes, it could be related to your power save/screensaver settings - doublecheck.

If still a problem, disable your Compiz and Unity desktop effects (hardware heavy) or try logging into a different desktop manager, if you have any installed (XFCE, LXDE, etc).

If still a problem, paste the output of 'sudo lshw' (prints your hardware) from your terminal into your next response.

mardybear

---

### Post by asuastrophysics on 2012-11-08
> **mardybear said:**
> Hi again asuastrophysics.

Registered Ubuntu user...that's cool, didn't know that existed.

Wanna go fast - me like. Every user has their own preferences, but if you really wanna go fast you might not want to use Compiz and Unity.

You may have narrowed it down to either Firefox or flash - i agree with you about flash, resource heavy.

Update your system and get back to the group, see if the updates and newest Firefox 16.0.2 run better for you.

Although i believe Firefox is a better browser, you could try Chromium for comparison.

When Firefox is running and your system is giving you problems, run 'top' via terminal and see if a process called plugin-container (something like that) is running. It can easily be disabled.

If the system is freezing exactly every 3 minutes, it could be related to your power save/screensaver settings - doublecheck.

If still a problem, disable your Compiz and Unity desktop effects (hardware heavy) or try logging into a different desktop manager, if you have any installed (XFCE, LXDE, etc).

If still a problem, paste the output of 'sudo lshw' (prints your hardware) from your terminal into your next response.

mardybear

Will do. Just ran all the updates. I haven't had a freeze in a little while now. It will go away for days, and then come back with a vengance (freeze every 3 min, etc). I will get back to you if the freezing continues. I seem to be in the clear for now. Thanks a bunch for your awesome help! :P

---

### Post by CmdGabriel on 2012-12-12
> **asuastrophysics said:**
> Hey all,

Recently, my computer seems to have completely fallen apart. The only thing I've done to it is allow update manager to install minimum updates (supported and security releases only). Firefox will freeze, go "dark", stay there for a while, and then come back to life. This happens completely at random. It will go for hours just fine, and then have a fit where it freezes 16 times in 5 minutes. During the freeze, I cannot operate any other program whatsoever. I click on terminal, and it just blinks on the unity taskbar until firefox decides to behave. 

Which log file in ~/var/sys/log/ should I look at to troubleshoot this?

You are not alone. I have got the same problem. It usually stays a couple days and then everything is fine again. Today I had the same problem. It seems that some websites are responsible. (perhaps mircosoft sponsored... ;) )

---

### Post by gnusci on 2012-12-31
I had the same problem, and the only thing that worked out for me was:

(backup your firefox data)

$ sudo apt-get --purge remove firefox
$ sudo apt-get remove adobe-flashplugin
$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install firefox

Then firefox worked fine againg.

---

