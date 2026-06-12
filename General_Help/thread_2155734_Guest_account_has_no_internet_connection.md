---
title: "Guest account has no internet connection"
date: 2013-06-19
forum: General Help
---

### Post by Arjunanda on 2013-06-19
I have a small net-cafe type setup with three public desktop computers for our visitors to use for their emails, web etc. They are running Ubuntu 12.04 LTS. I have configured them to auto-login to guest session, and it all worksi fine.

Except the most important function: The internet connection is disabled. So practically, currently this whole setup is useless.

The internet gets activated once the regular user logs in - and then when switching back to the guest session, the connection gets enabled also there. If the regular user log out, internet connection is disabled also for the guest account.

I have been trying to find solution for this but so far did not find anything susbstantial. 
Is this a bug in the guest session binary? I guess it was not meant to behave like this - it was precisely supposed to allow web access, while protecting access to the local file system.

Any ideas?

---

### Post by zsld0423 on 2013-06-19
Unfortunately I am having this issue as well, and was just about to post here. Although mine is a Kiosk account, but it still doesn't have an internet connection at all while in that guest account. I've tried adding in "sudo /etc/init.d/networking start" to the kiosk script, but that still doesn't work. I've checked the Account settings as well to make sure the privileges are set to access the network but no luck so far.

---

### Post by Arjunanda on 2013-06-19
I just noticed: This issue comes up only on one of the desktops - in others it works just as it is supposed to. All have almost identical HW (Dell OptiPlex), and all run Ubuntu 12.04. So there must be some bit in configuration that has gone wrong on this problematic one.

So zsld, perhaps it helps you to know that in 2/3 of my cases it works as desired, and one has a problem.

---

### Post by Arjunanda on 2013-06-19
Got it solved :)

After booting up, once the Guest is logged in automatically, had to go to the network indicator applet in the in the panel on upper left, and select "Auto Ethernet". It asked password for authentication, and connected the network. After that, I rebooted, and the connection works now as expected. :)

> 
$ cat /etc/lightdm/lightdm.conf

[SeatDefaults]
user-session=gnome-fallback
greeter-session=unity-greeter

## Guest Autologin configuration by me
allow-guest=true
autologin-user=
autologin-guest=true
autologin-user-timeout=0
autologin-session=lightdm-autologin



---

