---
title: "linux-restricted-modules-2.6.22.14-generic -- no one minding the store?"
date: 2007-10-30
forum: General Help
---

### Post by gregconquest on 2007-10-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/158631](https://bugs.launchpad.net/ubuntu/+bug/158631) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				On ubuntu 7.10 Gutsy Gibbon, if I click
System -- Administration -- Restricted Drivers Manager
I get an error box that says:
```
You need to install the package 
linux-restricted-modules-2.6.22.14-generic 
for this program to work
```
I can't find anything like this in add/remove software, and a search for this turns up very 2 discussions that haven't helped.

A search for the more general:
linux-restricted-modules 
does turn up more. It seems from a little delving, that sometimes some of the packages lag behind the main kernel -- sometimes by a few days.

It's been over ten days now. If these situations usually resolved themselves in a few days at worst, and this has been going on ten days, then why isn't there at least mention of the ERROR by name on the net? I searched for the error message I got, the same one verbatim that 100,000's of other users are presumably also seeing, and there is nothing. I'm stymied. Surely this would be easy to resolve...

Since I'm discussing it here, the 2.6.22.14 error message will now perhaps be documented, but what about next time? We need specific errors documented online. Or am I wrong in saying that this is a problem that can be overcome?

Greg

---

### Post by EriktheUnready on 2007-10-30
Funny, initailly I also had this bug, but after updating the repo's and manually updating what I needed  the restricted driver manager seemed to work. Only thing is, I cannot recall what I did to get it gone, (if I recall it was showing in synaptic, but wouldn't work). have you tried without symnaptic, apt-get? 

(My mind is gone trying to get ruby & rails up on 7.10.)

---

### Post by gregconquest on 2007-10-30
> **EriktheUnready said:**
> Funny, initailly I also had this bug, but after updating the repo's and manually updating what I needed  the restricted driver manager seemed to work. Only thing is, I cannot recall what I did to get it gone, (if I recall it was showing in synaptic, but wouldn't work). have you tried without symnaptic, apt-get? 


I was advised to try
apt-get install linux-restricted-modules-2.6.22.14-generic
on the launchpad page for this (link at top of thread), and this worked!

Now, though, I enabled the Nvidia restricted drivers and ubuntu won't boot. It goes all the way to the GUI load and then just hangs at a black screen. I can get in via recovery mode, but I don't know what to do. startx still hangs. Either I figure out how to reverse or fix the restricted driver boot hang (a day or so), or I will have to flash the partition with an image from last week...

Greg

---

### Post by Therion on 2007-10-30
> **gregconquest said:**
> ... I can get in via recovery mode, but I don't know what to do. startx still hangs. Either I figure out how to reverse or fix the restricted driver boot hang (a day or so), or I will have to flash the partition with an image from last week...
From the command prompt, after booting into Recovery Mode, try:
```

nano /boot/grub/menu.lst
```
Scroll down past all the # signs until the first line that starts with Kernel.  It's a long line that will go off the end of your display and end with -ro -splash -quiet.
Edit out the "-splash".
Ctrl+X to save, confirm the overwrite and reboot.

---

### Post by gregconquest on 2007-10-30
> **Therion said:**
> From the command prompt, after booting into Recovery Mode, try:
```

nano /boot/grub/menu.lst
```
Scroll down past all the # signs until the first line that starts with Kernel.  It's a long line that will go off the end of your display and end with -ro -splash -quiet.
Edit out the "-splash".
Ctrl+X to save, confirm the overwrite and reboot.

OK. I did that, Now I can read the text scrolling by ... but the ending, after mounting my drives and acpi, the text scrolls off the screen too quickly to read what's being echoed.Then the screen goes black like before.

Greg

UPDATE:
I followed the instructions here:
[https://bugs.launchpad.net/ubuntu/+bug/158631]("https://bugs.launchpad.net/ubuntu/+bug/158631")
I entered:
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-generic
```
and I no longer get the same error.

This is not all fixed now, but one source of the problem is. Somehow, linux-restricted-modules-generic never was installed.

---

