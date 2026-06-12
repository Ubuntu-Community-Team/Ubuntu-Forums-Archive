---
title: "I can't get Xubuntu to work HELP!"
date: 2008-01-25
forum: General Help
---

### Post by Adam.W on 2008-01-25
Hello
I am new to Linux but from what I have seen It look great. so me and my work friend have a few old work desktops we set to put linux on to. We have found ubuntu to be vary good but its just going to be to much for my litle laptop. I have a Fujitsu Lifebook B2131 it has 128 mb ram and a 400mhz procesor. Then I noticed Xubuntu and found out it was a lighter OS so downloaded the ISO on to CD. the problem I have is that my laptop has not got a CD-ROM drive because it is so small but I do have a external USB CD-ROM drive. My laptop wont let me boot from the the USB CD-ROM drive. This is where I started to get abit ticked off. It is running windows 2000 at the mo. I loaded up windows ran the Xubuntu CD and there was a litle ubuntu logo so I double clicked and it said instaling Xubuntu. I thought I had it because it asked me to reboot. I said yes an the laptop colseddown and the gave my two boot options:
Windows 2000 or Ubuntu so picked ubuntu and the Xubuntu load up logo apeard. It took a long time to load but it evntualy did but with out the top and bottom bars:confused.::confused: there was a icon which said Install so I clicked it and the laptop froze and I had to switch it off. This is as far as I can get and don't have enough knoldege of linux to know what Im doing wroung. Can anybody help? How do I install Xubuntu?

Adam

---

### Post by seshomaru samma on 2008-01-25
try this:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by Lord Illidan on 2008-01-25
From [http://www.xubuntu.org/get](http://www.xubuntu.org/get) :

> To run the Desktop CD (LiveCD + Install CD), you need 128 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to run or 192 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM") to install. The Alternate Install CD only requires you to have 64 [MB]("http://en.wikipedia.org/wiki/Megabyte") [RAM]("http://en.wikipedia.org/wiki/RAM").

---

### Post by Adam.W on 2008-01-25
I manage to get Xubuntu on my Laptop and I am very happy. I do have a few problems and would be greateful if someone could help.
I have a fujitsu Lifebook B2131.

1. I can't seem to get the screen resolution to show 1024x768? I have done all the conf,x11 stuff that I have done befor but it hasent worked on this laptop?

2. How do I get my touchscreen to work is there anywhere I can get the drivers for Xubuntu?

3. I have a wirless internet card is there anywhere I can get the drivers for this?

Thanks for the help

Adam

---

### Post by ugm6hr on 2008-01-25
> **Adam.W said:**
> 1. I can't seem to get the screen resolution to show 1024x768? I have done all the conf,x11 stuff that I have done befor but it hasent worked on this laptop?
2. How do I get my touchscreen to work is there anywhere I can get the drivers for Xubuntu?
3. I have a wirless internet card is there anywhere I can get the drivers for this?

Not sure I can help - but I can at least let you know what information might be useful.

So - post the output from:
```
lspci
lshw -C display
lshw -C network
```

And also post the current content of /etc/xorg.conf (copy and paste from):
```
mousepad /etc/X11/xorg.conf
```

PS: Do you mean touchscreen or touchpad?
EDIT: Just seen the specs for that laptop - and yes you do mean touchscreen.  There is a driver available as a patch: [http://www.conan.de/touchscreen/lifebook-2.6.html](http://www.conan.de/touchscreen/lifebook-2.6.html)
However, it suggests that it should already be part of the mainline Linux kernel - so, in theory, it should just need the xorg driver: [http://www.conan.de/touchscreen/evtouch.html](http://www.conan.de/touchscreen/evtouch.html)
This gives settings for the xorg driver (in xorg.conf): [http://www.akos.uklinux.net/biblo-linux/#rh.touch](http://www.akos.uklinux.net/biblo-linux/#rh.touch)

---

### Post by rosegarden78 on 2008-01-25
Although Xubuntu GG will work I couldn't get Compiz Fusion running.  I believe Xubuntu uses the same kernel as Ubuntu so the Grub will probably say Ubuntu kernel no matter what.  As far as Xubuntu I believe it's a marketing campaign like Mac although I could be wrong.  If you run a XFCE Deskop instead of GNOME I think you're using "Xubuntu."

If you start with a fresh install of Ubuntu and install all the Compiz packages except one (it asks to uninstall compiz don't use it) and XFCE and the Avant Window Manager you can get the Mac dock with Vista 'eye candy.'  Only it's much, much more useful than just candy.

The wireless in XFCE you need to add the System dock on your panel.  If you don't have sound you need to install xfce4-mixer and add volume control to your panel.  If you don't have wireless you need to run Network Manager or type nm-applet.  This will give you wireless bars in your system dock.

If you're using a BCM43xx based card there should automatically be option to install restricted drivers or download fw-cutter.deb from the Internet.  Otherwise if your card is not supported by Linux and no drivers/cutters exist you might consider purchasing an Ubuntu-supported wireless card.

Good luck!

P.S.  Google "ubuntuforums workable eye candy avant compiz" to find the article EDIT: or click [here]("http://ubuntuforums.org/showthread.php?t=385981").  Did I mention you may wish to run 'nautilus' when using Xfce?

---

### Post by Adam.W on 2008-01-26
I am a newby and I dont realy understand what you have just told me. Sorry but I need to be told in more detail befor I can understand.

Adam

---

### Post by ugm6hr on 2008-01-26
> **Adam.W said:**
> I am a newby and I dont realy understand what you have just told me. Sorry but I need to be told in more detail befor I can understand.

Adam

Look at the link in my signature below (Enter Code....).

Then read my post above and enter the commands exactly.  They give details about your hardware for us to see.  They will not change any settings at all.

---

### Post by Adam.W on 2008-01-29
I copyed the text you gave me into the terminal and this is what I got:

-v              Be verbose
-n              Show numeric ID's
-nn             Show both textual and numeric ID's (names & numbers)
-b              Bus-centric view (PCI addresses and IRQ's instead of those seen by the CPU)
-x              Show hex-dump of the standard portion of config space
-xxx            Show hex-dump of the whole config space (dangerous; root only)
-xxxx           Show hex-dump of the 4096-byte extended config space (root only)
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]   Show only devices in selected slots
-d [<vendor>]:[<device>]        Show only selected devices
-t              Show bus tree
-m              Produce machine-readable output
-i <file>       Use specified ID database instead of /usr/share/misc/pci.ids.gz
-D              Always show domain numbers
-M              Enable `bus mapping' mode (dangerous; root only)
-P <dir>        Use specified directory instead of /proc/bus/pci
-H <mode>       Use direct hardware access (<mode> = 1 or 2)
-F <file>       Read configuration data from given file
-G              Enable PCI access debugging

I will copy the next text and post it next.

Adam

---

### Post by Adam.W on 2008-01-29
I just typed in the next lot of text you gave me and got this:

gedit /etc/X11/xorg.conf
The program 'gedit' is currently not installed.  You can install it by typing:
sudo apt-get install gedit
bash: gedit: command not found

What do I do?

---

### Post by Adam.W on 2008-01-29
I used abiword instead ( abiword  /etc/X11/xorg.conf )

I copyed this if this helps?

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems Cyber 9525"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768" "800x600" 
	EndSubSection
EndSection

---

### Post by Lord Illidan on 2008-01-29
It's not a good idea to use abiword, since it is a word processor not a text editor.

Since you're using xubuntu substitute mousepad instead of gedit

```
sudo mousepad /etc/X11/xorg.conf
```

---

### Post by Adam.W on 2008-01-29
Ok done that now what do I need to do?

---

### Post by ugm6hr on 2008-01-29
> **Adam.W said:**
> Ok done that now what do I need to do?

First - an apology.  I forgot about the gedit vs mousepad issue - I have corrected my previous post in case anyone else reads this thread in the future.

Your xorg.conf includes 1024x768 as default resolution, so I have no idea why it doesn't default to that on booting.  What resolution does it show?

The other commands are 3 separate commands.  The output you got looks like a help file for lspci.  Not sure how you got that.  Maybe try again - 1 line at a time.

---

