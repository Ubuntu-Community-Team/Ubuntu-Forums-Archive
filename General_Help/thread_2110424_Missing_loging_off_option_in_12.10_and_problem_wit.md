---
title: "Missing loging off option in 12.10 and problem with restarting network"
date: 2013-01-30
forum: General Help
---

### Post by firekage on 2013-01-30
Hello.

I've been testing Ubuntu live from usb pendrive but one thing bugs me. There is no such a problem with Xuibuntu or Mint versions.

I run Ubuntu live from usb, than created user by useradd and after that i want to log off and log in as a created user - there is no icon/option/possibility in right upper corner (with ubuntu logos). 

Is this normal? I can only enter on created account by killing Xorg, than i see unity greater and can type my login and password. I thing that this is some kind of bug because on Mint distros and Xubuntu i can log off from "root" account right after boot of live system from pendrive. 

Is there a way to fix it?


And second:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1070879](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1070879)

Is there a fix for that? I'm amazed because of this bug. Can't believe it but it happened to me also.

---

### Post by bogan on 2013-01-30
Hi!,** fireKage,**

In12.10 'Ubuntu Tweak>Session indicator',  there is an option to:"Remove the log out item"; Un-Tick it.

There is also one for the Shut down item & to suppress the logout/shut down confirm/cancel Window.

I do not know anything about the networking unity shutdown.

Chao!, **bogan.**

---

### Post by firekage on 2013-01-30
> **bogan said:**
> Hi!,** fireKage,**

In12.10 'Ubuntu Tweak>Session indicator',  there is an option to:"Remove the log out item"; Un-Tick it.

There is also one for the Shut down item & to suppress the logout/shut down confirm/cancel Window.
**.**

Thank You. It works.


Only one problem still remains: network, networking after resume from suspend. Not only it doesen't work, but X crashes, freezes...till to hard reset.

---

### Post by bogan on 2013-01-31
> **firekage said:**
> Thank You. It [Ubuntu Tweak} works.


Only one problem still remains: network, networking after resume from suspend. Not only it doesen't work, but X crashes, freezes...till to hard reset.I have found that after waking from Sleep, inserting a - [known to work OK] - USB Wifi Adapter Dongle, forces recognition of both and re-connection.

I do not get the crashes, but freezes sometimes respond to 'Ctr+c'.

Chao!, **bogan**.

---

### Post by firekage on 2013-01-31
> **bogan said:**
> I have found that after waking from Sleep, inserting a - [known to work OK] - USB Wifi Adapter Dongle, forces recognition of both and re-connection.

I do not get the crashes, but freezes sometimes respond to 'Ctr+c'.

Chao!, **bogan**.

Thanks.

In my case it crashes, freezes and i can only hit ctrl+alt+del to reboot. It happens on ubuntu created to boot from usb pendrive. Strange thing is that other systems, like xubuntu, mint (mate, xfce edition), doesen't have this crashes, freezing. I can suspend, than resume and not only system works but internet too. With Ubuntu - not.

---

