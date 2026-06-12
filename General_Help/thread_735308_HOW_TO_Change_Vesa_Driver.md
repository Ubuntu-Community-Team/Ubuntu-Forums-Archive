---
title: "HOW TO: Change Vesa Driver"
date: 2008-03-25
forum: General Help
---

### Post by DJAKO on 2008-03-25
I was told to

> Change your /etc/X11/xorg.conf file to use the vesa driver, and then reboot.

Search out posts on reconfiguring your X server settings once you get going again.

How would I ago about doing this. I can't find a definite answer on what lines to edit

---

### Post by fsmithred on 2008-03-25
Scroll down to the device section, and change whatever driver you have to vesa.

```

Section "Device"
	Identifier	"your video card's name"
	Driver		"vesa"
	BusID		"some bus ID"
EndSection

```


You don't need to reboot after that - just re-start the xserver, either with ctrl-alt-backspace or with 'sudo /etc/init.d/gdm restart'

---

### Post by forrestcupp on 2008-03-25
or have X configure itself.  Type
```
sudo dpkg-reconfigure xserver-xorg
```
and choose the vesa drivers in the video card list.  Then reboot or restart x.

---

### Post by DJAKO on 2008-03-25
> **fsmithred said:**
> Scroll down to the device section, and change whatever driver you have to vesa.

```

Section "Device"
	Identifier	"your video card's name"
	Driver		"vesa"
	BusID		"some bus ID"
EndSection

```


You don't need to reboot after that - just re-start the xserver, either with ctrl-alt-backspace or with 'sudo /etc/init.d/gdm restart'

After I did the sudo /etc/init.g/gdm restart in terminal my screen just went black...Nothing else has happened.

---

### Post by fsmithred on 2008-03-26
First, make sure you typed init.d and not init.g as you indicated in your post. If your screen goes black and won't respond,  try ctrl-alt-F1 or ctrl-alt-F2 to get to a console, where you can log in and do stuff. Sounds like you need to reconfigure the xserver. Make sure the monitor frequencies are correct while you're there.

 What happens if you reboot? If you're getting an error message about the xserver, look at the detailed output, and pay attention to the lines that start with EE. And, if you have another thread about this problem, please provide a link to it, or else give some idea about why you wanted to know how to change to the vesa driver. .

---

### Post by forrestcupp on 2008-03-26
It's a lot safer and easier to just do what I said in my last post.  If you can't boot to the desktop, boot to recovery mode.  You should end up as root, so type:
```
dpkg-reconfigure xserver-xorg
```
And choose Vesa as your video driver and type
```
exit
```
It should reboot to your desktop.

---

