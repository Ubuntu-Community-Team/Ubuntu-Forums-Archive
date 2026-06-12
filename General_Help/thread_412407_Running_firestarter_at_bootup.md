---
title: "Running firestarter at bootup"
date: 2007-04-18
forum: General Help
---

### Post by ar1stotle on 2007-04-18
OK, I'm figuring this is a good idea, right? Shouldn't the firewall always be running? However, in order to get it to run, I need to run gksudo firestarter, and then I need to type in my password immediately after logging in. Is there any way to get it to run without needing to do that? Or should I not be running it all the time?

---

### Post by BoneKracker on 2007-04-18
What you need running is iptables.

I don't use Firestarter, but if it's like other modern linux firewall apps, it just sets up an iptables configuration script -- that's what needs to be run at bootup.  It probably also provides some (fairly limited, I would imagine) monitoring and/or analysis functionality.

[Edit]: oh, and I should mention, when you ran Firestarter, it probably created that script, and it probably also placed the necessary initscript into your default runlevel (or it does that when you "turn it on").  You're probably all set.

You might get a lot of value out of reading up on iptables.

---

### Post by mmikee66 on 2007-04-18
Yes Fireatarter is a IPtables manager.

But also setting it to off on boot will stop IPtables from starting on boot :(

Easy fix though :)

Firestarter -> Preferences ->Firewall 
check what you need
Start/restart firewall on program startup. With this option checked, Firestarter forces a reload of the firewall when you start the graphical interface.

Start/restart firewall on dial-out. This option adds the firewall service to the list of programs to run when a dial-up connection is established. It ensures the firewall is properly restarted when you are assigned a new IP address.

Start/restart firewall on DHCP lease renewal. This option causes the firewall to be restarted when your service provider issues you a new IP address.

---

### Post by akshaysrinivasan on 2007-04-18
Hmm ,doesn't firestarter run at startup ?There is a script named firestarter in /etc/init.d .So i reckon the firewall does start only you can't see it.May be you want to add a entry in the session manager.

---

### Post by mcduck on 2007-04-18
After installing Firestarter you'll get a firestarter script that starts the firewall on boot, and then you get the Firestarter graphical tool for configuring firewall settings. So the firewall starts automatically on boot, you don't need to start the graphical tool for any other reason than changing the firewall settings.

---

### Post by dpar on 2007-04-18
Try an experiment. Do a security scan online with Firestarter turned off, and do one with Firestarter turned on.
The results will be the same.

---

### Post by jeff58 on 2007-04-20
I am also having this problem. Since installing Feisty, firestarter does not run automatically at boot. When I issue 'sudo /etc/init.d/firestarter status' in a terminal, it says "Firestarter is stopped".

Also, I tested if the firewall is working by testing Azureus' incoming port. Right after booting, Azureus does receive incoming packets even though I don't have the necessary rules in Firestarter to allow them. However, right after launching the GUI of Firestarter, that is the only time that the packets are blocked.

I did not encounter this problem in previous Ubuntu versions which suggests that maybe there is a different configuration for Firestarter in Feisty. How can I ensure that the Firestarter service starts during boot?

---

### Post by rich.bradshaw on 2007-04-20
Firestarter is only a gui to configure itables. It shouldn't start on boot, as it is run as root, so this is a security risk.

Just set up your firewall with Firestarter, then let it be - the firewall will always be on - this isn't Windows where things like firewalls are tacked on top - iptables is a pretty low level firewall.

You don't even need a firewall in Linux really - no ports are open by default anyway. The only reason you might bother is so that you can open a service such as ssh, and only allow certain IP ranges to connect - though even that is better configured in the ssh configuration files.

---

### Post by LuxVoodoo on 2007-04-20
> **jeff58 said:**
> I am also having this problem. Since installing Feisty, firestarter does not run automatically at boot. When I issue 'sudo /etc/init.d/firestarter status' in a terminal, it says "Firestarter is stopped".

I'm also having this problem.  I posted a thread on these boards about it, but this thread is a little more active, so maybe somebody here has a fix.  /etc/init.d/ is not loading for me at startup.  I've done scans at "Shields Up" before starting the Firestarter GUI. It says I fail stealth mode.  I run the GUI and do another scan, it says I pass.  I restart the machine, log in, do another scan, and I'm back to fail.  Load the GUI and I pass.  This didn't happen when I ran in Edgy and has only been going on since I upgraded to Feisty.

---

### Post by jeff58 on 2007-04-20
> **rich.bradshaw said:**
> Firestarter is only a gui to configure itables. It shouldn't start on boot, as it is run as root, so this is a security risk.

Just set up your firewall with Firestarter, then let it be - the firewall will always be on - this isn't Windows where things like firewalls are tacked on top - iptables is a pretty low level firewall.

Hi! I also believe this is so. However, what I do not understand is why the firewall seems to only work when the Firestarter service is running. If it is not, packets can actually go through. This is described in the examples in my previous post as well as in LuxVoodoo's. This is somewhat confusing, not to mention the problem why the Firestarter service is not running during boot time.

---

### Post by LuxVoodoo on 2007-04-20
> **rich.bradshaw said:**
> Firestarter is only a gui to configure itables. It shouldn't start on boot, as it is run as root, so this is a security risk.

Just set up your firewall with Firestarter, then let it be - the firewall will always be on - this isn't Windows where things like firewalls are tacked on top - iptables is a pretty low level firewall.

Agreed.  However, I think a better way to explain the problem Jeff58 and I are having is that Firestarter is not saving/writing the script for our changes to iptables.  Even though running 'sudo /etc/init.d/firestarter status' in a terminal shows the firewall as not being active, the default values *are*  loaded at startup.  But I've also made changes to Firestarter that puts the computer into "stealth" mode.  Those changes are never saved and I always need to run the GUI to achieve stealth.  This was not the case before my upgrade to Feisty.   I ran GUI once or twice, made my changes, and they stuck without me ever having to run the GUI again. Now I'm having to run it full time.  So while the firewall is working without the GUI, it's not working right/the way I want it to.

---

### Post by LuxVoodoo on 2007-04-22
Not sure about anybody else, but I'm still having this problem. All ideas welcome at this point.

Thanks in advance!

---

### Post by RedSquirrel on 2007-04-22
> **LuxVoodoo said:**
> Not sure about anybody else, but I'm still having this problem. All ideas welcome at this point.

Thanks in advance!


Well, this may not be what you had in mind, but...

Unless you really like firestarter, I would configure iptables yourself. Here's a nice [HOWTO]("http://ubuntuforums.org/showthread.php?t=159661"). Works like a charm.

---

### Post by jeff58 on 2007-04-23
I am now able to load Firestarter's firewall settings on boot-up although I am still confused about some things.

Because Firestarter loads its settings using a service, I thought that maybe another service starting after the Firestarter service has started is causing the firewall rules in netfilter to revert to the default values. The idea is to delay starting the Firestarter service until that other service has already started, to somehow determine whether this is true. This is what I did:

I went into /etc/rc2.d/ and saw that firestarter has a prefix S20 along with other services running with that prefix. The next index is already S25 which is the service bluetooth in my machine. I changed the index of the Firestarter service by renaming it to S22firestarter, in order to delay its starting time until all services in the S20 index have started. I rebooted.

After the reboot, I checked the status of the Firestarter service and found out that it is running unlike the case before. I checked the ports in question and found out that the Firestarter settings are now loaded properly.

However, there are still things that confuse me. First is that when I tried renaming the Firestarter service back to its original link name, S20firestarter, the Firestarter service is still loaded upon boot-up. This is unlike before when the Firestarter service is stopped upon boot-up.

Another thing is that I understand that Firestarter is only a front-end to iptables which is used to configure netfilter. Some previous posters pointed out that the Firestarter service need to only run once and then can terminate. It does not need to be running all the time in order for the settings to work. But when I try to stop the Firestarter service, the rules I set there are not applied anymore. When I start the service, the rules are applied properly again. This suggests that the Firestarter service needs to run in the background in order for its rules to be applied. What I am thinking is that there is a change maybe in the configuration of the Firestarter settings for the Feisty package. Maybe the service script is configured to reload default iptables settings when it is exited.

I hope my post can help the others who are having this problem.

---

### Post by mcduck on 2007-04-24
> **jeff58 said:**
> I am now able to load Firestarter's firewall settings on boot-up although I am still confused about some things.

Because Firestarter loads its settings using a service, I thought that maybe another service starting after the Firestarter service has started is causing the firewall rules in netfilter to revert to the default values. The idea is to delay starting the Firestarter service until that other service has already started, to somehow determine whether this is true. This is what I did:

I went into /etc/rc2.d/ and saw that firestarter has a prefix S20 along with other services running with that prefix. The next index is already S25 which is the service bluetooth in my machine. I changed the index of the Firestarter service by renaming it to S22firestarter, in order to delay its starting time until all services in the S20 index have started. I rebooted.

After the reboot, I checked the status of the Firestarter service and found out that it is running unlike the case before. I checked the ports in question and found out that the Firestarter settings are now loaded properly.

However, there are still things that confuse me. First is that when I tried renaming the Firestarter service back to its original link name, S20firestarter, the Firestarter service is still loaded upon boot-up. This is unlike before when the Firestarter service is stopped upon boot-up.

Another thing is that I understand that Firestarter is only a front-end to iptables which is used to configure netfilter. Some previous posters pointed out that the Firestarter service need to only run once and then can terminate. It does not need to be running all the time in order for the settings to work. But when I try to stop the Firestarter service, the rules I set there are not applied anymore. When I start the service, the rules are applied properly again. This suggests that the Firestarter service needs to run in the background in order for its rules to be applied. What I am thinking is that there is a change maybe in the configuration of the Firestarter settings for the Feisty package. Maybe the service script is configured to reload default iptables settings when it is exited.

I hope my post can help the others who are having this problem.

What causes the confusion is that Firestarter is divided in 2 parts, the service/script that controls and configures the iptables firewall, and the GUI that is used to configure the firestarter script. To have active firewall the service/script has to be running (and it should start automatically on boot), but the Firestarter GUI is not needed.

When people are saying that you don't need to run Firestarter all the time they are talking about the GUI, not the service.

---

### Post by jeff58 on 2007-04-24
> **mcduck said:**
> What causes the confusion is that Firestarter is divided in 2 parts, the service/script that controls and configures the iptables firewall, and the GUI that is used to configure the firestarter script. To have active firewall the service/script has to be running (and it should start automatically on boot), but the Firestarter GUI is not needed.

I understand. Does that mean that the default behavior of the Firestarter script being stopped after boot-up is a bug? I would like to be sure I am not missing anything before reporting it as such.

---

### Post by mcduck on 2007-04-25
> **jeff58 said:**
> I understand. Does that mean that the default behavior of the Firestarter script being stopped after boot-up is a bug? I would like to be sure I am not missing anything before reporting it as such.
Yes, I believe it's a bug. It should work start on boot, and it does on my desktop machine. But on my laptop it stopped working when I installed network-manager. But I think there already is some bug report about this..

---

### Post by dustigroove on 2007-04-29
All the previous being said... what would be the appropriate way to automate launching the Firestarter GUI after login?

Ideally having the GUI/Notification icon load up last on login is my goal, and it would be preferred to not be prompted for my password. Entering 'gksudo firestarter' in System >  Preferences > Sessions > Startup Programs launches the GUI at login, but does not accomplish A or B for me.

Suggestions appreciated, thanks!

---

### Post by nick1 on 2007-05-04
Greetings,

I believe Firestarter is not enabling my firewall rules on system bootup.

First, some information:

I am using Ubuntu Feisty Fawn 7.04 desktop edition
I have Firestarter version 1.0.3 installed
I have a fairly strict policy setup:
inbound traffic policy:  default (meaning all inbound traffic is blocked)
outbound traffic policy:  restrictive by default, whitelist traffic (only allowing HTTP/S and Samba(SMB) out)

The reason I believe Firestarter is not enabling my firewall rules on system bootup is because when I issue the following command...

```
sudo iptables -L
```

...I do not see any of my firewall rules listed.  This command is used to list the entire set of firewall rules.  It's as if Firestarter did not implement my firewall policy.

Only when I manually startup Firestarter (System > Administration > Firestarter) is my firewall enabled.  Reissuing the previous command displays my firewall rules.

Is this a bug? What is the resolution to this problem?

Thanks,

*Nick*

---

### Post by KrazyPenguin on 2007-05-04
> **dustigroove said:**
> All the previous being said... what would be the appropriate way to automate launching the Firestarter GUI after login?

Ideally having the GUI/Notification icon load up last on login is my goal, and it would be preferred to not be prompted for my password. Entering 'gksudo firestarter' in System >  Preferences > Sessions > Startup Programs launches the GUI at login, but does not accomplish A or B for me.

Suggestions appreciated, thanks!

Try my howto  for automatically starting Firestarter without root password for Feisty
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Firewall)

Let me know how it goes.
;-)

---

### Post by dustigroove on 2007-05-05
[COLOR=Black]Thanks Krazy.  Your guide mentions that editing the sudoers file in this way is not secure. How great of a risk does this pose?
[/COLOR]

---

### Post by KrazyPenguin on 2007-05-05
> **dustigroove said:**
> [COLOR=Black]Thanks Krazy.  Your guide mentions that editing the sudoers file in this way is not secure. How great of a risk does this pose?
[/COLOR]

I don't think it is a BIG security threat.

All the Firewalls and Virus scanners that run on Windows don't require root privileges, so I would say that it is still safer than using a Windows Firewall.

I can't honestly answer this question.  Maybe somebody else knows the exact answer.

I test my computer at shieldsup and it is undetectable.

---

