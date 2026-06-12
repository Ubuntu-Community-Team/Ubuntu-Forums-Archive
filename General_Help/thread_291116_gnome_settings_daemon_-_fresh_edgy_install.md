---
title: "gnome settings daemon - fresh edgy install"
date: 2006-11-02
forum: General Help
---

### Post by mjziegle on 2006-11-02
I can't seem to find a solution for this anywhere but many people seem to be having this problem.  

Here are my symptoms.  I installed a fresh copy of edgy.  Then I installed linux-restricted-modules-generic and xorg-driver-fglrx to get my madwifi and fglrx drivers for my laptop.  I configured my /etc/network/interfaces.

It takes 5 minutes for the desktop to load after I login and I get this message ...

There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

... (end)

I tried adding gnome-session to ~/.Xsession and putting "gnome-session-manager" in my system/sessions/startup.  ](*,) 
The theme isn't ubuntu human but the gnome default.  Please help.  Thanks.

---

### Post by mjziegle on 2006-11-02
I found that when I removed the linux-restricted-modules package that everything worked like it was supposed to.  Unfortunately that  means that my wireless and fglrx don't work anymore.  

Is it possible this is a problem with the madwifi-ng module that is now the default for atheros cards?

---

### Post by odelay on 2006-11-05
I'm having the same problem (along with 10 billion other people).  The best I can do is just run in Fail-Safe mode.  Somebody save us!!!!

---

### Post by markba on 2006-11-05
Bug is already known:
"gnome-settings-daemon crashes at login"
[https://launchpad.net/distros/ubuntu/+source/control-center/+bug/61381](https://launchpad.net/distros/ubuntu/+source/control-center/+bug/61381)

No work around at hand at this time.

---

### Post by mjziegle on 2006-11-06
I narrowed the problem down to wpa_supplicant on my system.  I was working fine with WEP encrypted systems.

---

### Post by eagle63 on 2006-11-06
Interesting thing for me is that I ONLY get this error when I connect to my box via VNC.  If I just login at the machine itself there's no problem.  But anytime I VNC to the box it always throws this error, and my desktop-theme reverts to the ugly gnome default.  

Hopefully this gets fixed soon...  :)

---

### Post by risbac on 2006-11-07
> **mjziegle said:**
> I narrowed the problem down to wpa_supplicant on my system.  I was working fine with WEP encrypted systems.

How did you manage to know where the problem was coming from? The only error messages I have are not detailed enough, I dont know where to look at... Thanks!

---

### Post by mjziegle on 2006-11-08
> **risbac said:**
> How did you manage to know where the problem was coming from? The only error messages I have are not detailed enough, I dont know where to look at... Thanks!

Using LAN
1. Fresh install of edgy - everything works
2. Installed linux-restricted-modules which includes the new atheros-ng driver and fglrx - everything works
3. Installed xorg-driver-fglrx and fixed xorg.conf - everything works
Using Wireless
4. Used wireless without encryption - works
5. Used wireless with WEP - works
6. Used wireless with wpa_supplicant invoked through ivpriv in /etc/network/interfaces - didn't work anymore

Never installed network-manager.  Also didn't try invoking wpa_supplicant from command line.  Maybe its a problem with the way ivpriv and wpa_supplicant.  I had my wireless config file in ~/.wireless/wpa_supplicant.conf.  Maybe that was the problem.

---

### Post by valmy on 2006-11-09
In my case the same symptoms appears after I changed the network settings.
It turned out that the localhost alias had become unrecognized. I edited /etc/hosts, and make sure there's a line:

127.0.0.1  localhost

And then everything work normally after reboot.

---

### Post by gosh on 2006-11-14
> **valmy said:**
> In my case the same symptoms appears after I changed the network settings.
It turned out that the localhost alias had become unrecognized. I edited /etc/hosts, and make sure there's a line:

127.0.0.1  localhost

And then everything work normally after reboot.

And make sure you have 
```
auto lo
```
in your /etc/network/interfaces

---

### Post by zorkerz on 2006-11-15
I am having the same problem.  It deffinatly revolves around some wireless changes I made but I don't know what.  I updated from dapper with no problems.  I now think my /etc/network/interfaces file has problems.  I have the auto lo line in there.  Could someone show me their interfaces file or tell me the necessary lines for it to work.
thanks a bunch

---

### Post by FastZ on 2006-11-15
This is a problem I am having on my Ubuntu Server install as well.  I installed the gnome-desktop just two days ago and now everytime I try to login, i get this five or so minute wait and then the error stated above.  I have looked at my /etc/hosts and /etc/network/interfaces/ files and nothing is out of the ordinary for me, yet I still get the problem every single time.  

I have been running Edgy desktop on my desktop computer and my laptop computer since the day the final version came out and have not had this problem one time on either of those machines...just on the server, which i installed Edgy server on two days ago.

I dont think this has anything to do with a wireless issue seeing how my server is not wirelessly connected to anything.  Wireless doesnt even work on my laptop when using Edgy... :(

---

### Post by zorkerz on 2006-11-16
I fixed my problem with help from this bug [https://launchpad.net/distros/ubuntu...ter/+bug/61381]("https://launchpad.net/distros/ubuntu/+source/control-center/+bug/61381") thanks again Paul.  The problem for most people seems to have been an incorrectly setup /etc/network/interfaces or /etc/hosts file  Mine way the later I had an incoherent line.  Hope this helps.  My I believe was caused when I messed with wireless apps but Im not entirely sure.
good luck

---

