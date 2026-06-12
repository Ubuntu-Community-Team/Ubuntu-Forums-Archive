---
title: "Running Virtualbox"
date: 2007-01-28
forum: General Help
---

### Post by lbyrd33 on 2007-01-28
I just installed virtualbox on Dapper with success. One thing that is bothering me is that the fullscreen mode does not work. The window enlarges however the virtual machine screen only occupies about 1/2 of the screen. Being also a VMware user I realize that the virtualbox software is pretty good and a little faster running windows so I want to completely switch to it.  Any help on this matter would be greatly appreciated.

---

### Post by chocolatemintmocha on 2007-01-29
I'm having the same issue.

---

### Post by Karl S. on 2007-01-30
Had the same problem and tried to fix it in a stupid way. I changed the screen resolution in Windows XP while running it in VirtualBox, and this screwed up my resolution. Couldn't see or do anything. So: don't do that.

I thought I might be able to fix the resolution problem if I started into VGA mode (F8 on startup), but it didn't work. So far as I can tell, I *can* run Windows XP in VGA mode, but it's kind of a pain to have to tell it to start into VGA everytime I start my Virtual Machine. Any suggestions for a permanent fix would be appreciated. If you haven't already noticed, I'm a total beginner, so if you have any suggestions, be as explicit as possible. Thanks.

---

### Post by caled on 2007-02-11
I have managed to get fullscreen working properly by installing the guest additions, an option in the devices drop down menu within the guestOS's window. I have noted however that virtualbox will not resize the window to suit your screen so if you choose a resolution not supported by your monitor, it will go blank or possibly do damage to your monitor if you take that to full screen. I use 1280x1024 for the guestOS which works properly when taken up to full screen. 
Seems like a good program.

---

### Post by Rich78 on 2007-02-11
From my experience of it, the VM OS resolution needs to match that of your host OS resolution.

Either lower your host resolution or up your VM OS resolution to match.

---

### Post by skenagle on 2007-02-13
I have now installed XP twice in VirtualBox thinking i must have done something to mess things up.

But after the second install i had the same exact problem..
First bootup everything is fine, i can see menus, right click stuff..etc..

perfect windows install ..

but then i decide to install the guest additions (did the same thing last time)

and after boot up...
XP loads up.. wallpaper appears... but thats it...

IF i move my mouse around it shows the mouse but nothng else... no icons or anything..

If i move my mouse around, the last command i gave it.. (like if i sent ctrl/alt/delete) is rendered while i move my mouse... but its not an active window... 
ITs just painted on my screen

I think this happened after i installed the additional tools...

my resolution is only increased to the same as my ubuntu, or below... and it fries my whole setup.

does any of this make sense to anyone?

Its such a cool program, it is making me sad not to be able to use it.


Thank you for any help anyone can give.

---

### Post by linuxfanatic1024 on 2007-02-13
The problem I have is that whenever I click to start the guest, my computer suddenly reboots itself. This never happened on Fedora on the same machine.

---

### Post by skenagle on 2007-02-14
> **linuxfanatic1024 said:**
> The problem I have is that whenever I click to start the guest, my computer suddenly reboots itself. This never happened on Fedora on the same machine.

Hey let me ask this... for audio settings in the VBOX options for that particular guest install... do you have "Alsa" chosen by any chance.

If you do, switch it to OSS or disable sound in the guest install....

let me know what happens.

---

### Post by bmt on 2007-02-14
> **skenagle said:**
> ... do you have "Alsa" chosen by any chance.
I'll jump in here: well spotted!  I just experienced the rebooting on a VM that worked fine until I set ALSA for the sound option.  OSS is okay.

---

