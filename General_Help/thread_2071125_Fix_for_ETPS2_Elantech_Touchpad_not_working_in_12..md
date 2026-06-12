---
title: "Fix for ETPS/2 Elantech Touchpad not working in 12.04"
date: 2012-10-14
forum: General Help
---

### Post by hasanyonereally on 2012-10-14
Hello,

this is for anyone that has problems with their touchpad not working on Ubuntu 12.04 x32, or that the touchpad appears as a mouse in terminal -> xinput. 

I have an Acer Aspire One 725. 

When I first installed Ubuntu i had problems with the touchpad. No matter what I did it was unresponsive. So I went googling on my other comp to find a fix for this. There is a dirty fix going around that makes the touchpad work temporarily. 

[I]cd /etc/modprobe.d/
gksudo gedit options.conf[/I]

adding: *options psmouse proto=imps* to the text file.
Then running: 
[I]sudo modprobe -r psmouse 
sudo modprobe psmouse[/I]

While this will make the touchpad work, it will no longer be customizable. When you try to find it in terminal -> xinput it will come up as a mouse. Something like PS2 Mouse, or something similar. I wanted to turn of the tap-to-click but couldn't since I couldn't find it neither in system settings or from the command line. 

So what i did was this. First remove the *options psmouse proto=imps* from modprobe.d

Then in terminal: 
[I]cd /etc/X11/
gksu gedit xorg.conf[/I]

And at the end of the text-file add: 
[I]Section "InputClass"
	Identifier "ETPS/2 Elantech Touchpad"
	MatchProduct "ETPS/2 Elantech Touchpad"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "AreaTopEdge" "50"
EndSection[/I]


Reboot and Voilá! The touchpad is back and I could remove the annoying tap-to-click which was making my pointer go bananas all over the screen while i was writing. 

Also in xinput it's listed as ETPS/2 Elantech Touchpad. 

Great success!

---

### Post by hasanyonereally on 2012-10-15
So I rebooted my computer now and the touchpad was not working again. 

Apparently the system had made a copy of my xorg.conf with the name xorg.conf~

I just removed it and things were working again. But why was that created? Some auto-update?

---

### Post by simontaylor on 2012-10-25
I'm having a similar problem with ETPS/2 not being recognised.

Has your solve stuck?

Best,
Simon

---

### Post by simontaylor on 2012-10-25
went through the steps outlined above... xinput still does not recognise ETPS/2

but no replication of xorg.conf

---

### Post by hasanyonereally on 2012-10-27
Hi! 

Everything I did while I was logged in sucked. Couldn't get the touchpad working. I was logged in automatically at first but i had to change that to get the pad working. 

The only solution I have found so far is to:
1. enable log in. 
2. While you are at the login-screen you can toggle the touchpad ON/OFF by pressing FN+F7. 

By default it's turned off. If you toggle it on and then log in it works like a charm.

---

### Post by empollondefisica on 2012-12-21
@hasanyonereally

Xorg.conf~ is a backup file created by gedit when you saved the file.  You can disable the creation of backup files if you do not want those any more.  They generally end with "~"

In regards to the problem, I know this is a solved thread, but I would like to post the solution I found for my computer. I have an Acer A0-725, and I struggled with its Elantech touchpad for about a month.

What I found was that blacklisting the **acer-wmi** driver was all I had to do. The process is simple:
```

cd /etc/modprobe.d
gksudo gedit blacklist.conf

```

There is a long list of "blacklist .." items.  Add **blacklist acer-wmi** to the bottom of the list, save, reboot.

You may have to turn the touchpad on initially.  Mine was off by default; but, after turning it on, it has been on at each boot-up.

---

### Post by jakfish on 2013-01-24
Asus EEE 900/Lubuntu 12.04

I can confirm that blacklisting acer-wmi will restore hardware right click to the eee 900.

My left click is broken so I can not vouch for its success.

Huge thanks to empollondefisica--I had searched to no avail until finding this thread.

Jake

---

### Post by athmane19 on 2013-10-30
thanks;)

---

