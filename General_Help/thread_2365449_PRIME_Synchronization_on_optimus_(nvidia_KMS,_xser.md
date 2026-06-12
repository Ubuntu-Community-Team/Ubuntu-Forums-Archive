---
title: "PRIME Synchronization on optimus (nvidia KMS, xserver-1.19.3+, nvidia-prime"
date: 2017-07-06
forum: General Help
---

### Post by mc4man on 2017-07-06
It's working here. Obviously not needed for Wayland but wayland is currently non-functional with nvidia-prime

method here
Switch to gdm3 if not already (will work with lightdm, for 16.04.3 or newer stay with lightdm
Install nvidia drivers 375.66 or higher, reboot
In terminal - 
```
sudo nano /etc/modprobe.d/zz-nvidia-modeset.conf
```
Add this line, adjust 375 if using newer driver, ex. 381 or 384 ect.
```
options nvidia_375_drm modeset=1
```
Save changes, exit nano
In terminal
```
sudo update-initramfs -u
```
Reboot

Note: one could also just edit /etc/modprobe.d/nvidia-graphics-drivers.conf  on the last line instead on creating a new file. Same affect,  the new file method may be slightly more persistent, i.e., an update to nvidia that doesn't up the version #..
To check - 
```
sudo cat /sys/module/nvidia_drm/parameters/modeset
```
Should return Y

```
xrandr --verbose
```
1st. section, (the laptop display),  should show PRIME Synchronization: 1 

Ex. here - 
> $ xrandr --verboseScreen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
eDP-1-1 connected primary 1920x1080+0+0 (0x46) normal (normal left inverted right x axis y axis) 345mm x 194mm
	Identifier: 0x42
	Timestamp:  18328
	Subpixel:   unknown
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       0
	CRTCs:      0 1 2
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	_MUTTER_PRESENTATION_OUTPUT: 0 
	EDID: 
		00ffffffffffff0030e4d90200000000
		00150103802313780a15d59e59509826
		0e505400000001010101010101010101
		0101010101017e3680b070381f403020
		350059c2100000190000000000000000
		00000000000000000000000000fe004c
		4720446973706c61790a2020000000fe
		004c503135365746312d544c4232004b
	[COLOR="#0000CD"]PRIME Synchronization: 1[/COLOR] 
		supported: 0, 1
	scaling mode: Full aspect 
		supported: None, Full, Center, Full aspect
...........

Note that upgrading nvidia driverversions  will require redoing the above, i.e., edit # in the modeprobe file to match new driver #, then run the sudo update-initramfs -u command again

---

### Post by mc4man on 2017-07-07
Can also report it's now working in 16.04 with lightdm & upcoming HWE packages. This is better news than the state of in 17.10..
If not using the 16.04.3 image for install then one must get on the HWE path, info here
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
Basically just run this, you don't need to do the kernel but probably a good idea to do so. If nvidia drivers are already installed I'd either remove them if doing the HWE  kernel or switch to Intel, install the HWE kernel, reboot & re-install or switch back to nvidia, ect.
```
 sudo apt  install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04 
```
or for just xserver
```
 sudo apt install --install-recommends xserver-xorg-hwe-16.04 
```
 
> $ apt-cache policy xserver-xorg-core-hwe-16.04
xserver-xorg-core-hwe-16.04:
  Installed: 2:1.19.3-1ubuntu1~16.04.1
  Candidate: 2:1.19.3-1ubuntu1~16.04.1
  Version table:
 *** 2:1.19.3-1ubuntu1~16.04.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-proposed/main amd64 Packages
        100 /var/lib/dpkg/status
     2:1.19.3-1ubuntu1~16.04.1~7 500
        500 [http://ppa.launchpad.net/canonical-x/x-staging/ubuntu](http://ppa.launchpad.net/canonical-x/x-staging/ubuntu) xenial/main amd64 Packages
     2:1.18.4-1ubuntu6.1~16.04.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages

> $ xrandr --verbose
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
eDP-1-1 connected primary 1920x1080+0+0 (0x46) normal (normal left inverted right x axis y axis) 345mm x 194mm
	Identifier: 0x42
	Timestamp:  13325
	Subpixel:   unknown
	Gamma:      1.0:1.0:1.0
	Brightness: 1.0
	Clones:    
	CRTC:       0
	CRTCs:      0 1 2
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
	EDID: 
		00ffffffffffff0030e4d90200000000
		00150103802313780a15d59e59509826
		0e505400000001010101010101010101
		0101010101017e3680b070381f403020
		350059c2100000190000000000000000
		00000000000000000000000000fe004c
		4720446973706c61790a2020000000fe
		004c503135365746312d544c4232004b
	PRIME Synchronization: 1 
		supported: 0, 1

---

### Post by mc4man on 2017-07-10
For visible confirmaton dl, extract & play attached vid while using nvidia drivers thru nvidia-prime (hybrid/optimus machines)
The bar won't break which it would of in the past..

---

### Post by markackerman8@gmail.com on 2017-11-05
Awesome,

Finally a way to stop screen tearing with Optimus Laptops using Nvidia Drivers ... a Long Time Coming! :)

Make sure to redo it whenever you you upgrade to a different Nvidia driver as you will need to change the number in the file to match it.  You will remember this as screen tearing will come right back until you do it!

Thank you so much mc4man - YOU ARE AWESOME! :KS

Cheers, Mark

---

### Post by Bashing-om on 2017-11-27
mc4man; :)

Pass along a "thank you "
> 
< ecv> Bashing-om: I got all the checks positive and though I wouldn't swear by it, I think it worked :)
< ecv> can't check that guy's video since I don't have an account. Also if you could thank him I'd appreciate


[INDENT]add my bit to try and help
[/INDENT]

---

### Post by mari5ha on 2017-12-15
Hi all,
Just to add this solution works perfectly on Ubuntu. Is it applicable for Linux Mint 18.3 Cinnamon?
TY

EDIT: Following the manual, at the end, line  PRIME Synchronization: 1 is not added...

---

### Post by aliuygurerol on 2018-01-07
Hi,

I have a MSI laptop with gtx 950m. I had tearing problem for almost 3 years now and I have posted on every single forum on internet. 

This solution works like a charm for nvidia chip on Ubuntu Mate 17.10. I still have a strong tearing issu with the Intel chip. 

BUT THX A LOT !!!!!!!!!!!!!!!!!

---

### Post by mc4man on 2018-01-08
> **mari5ha said:**
> Hi all,
Just to add this solution works perfectly on Ubuntu. Is it applicable for Linux Mint 18.3 Cinnamon?
TY

EDIT: Following the manual, at the end, line  PRIME Synchronization: 1 is not added...
That's because mint 18.3 has xserver 1.18.x, you need to get on the HWE path to get xserver 1.19.x. See edits in post #2 as how to, also applies to mint 18.3
(the next mint release should be on xserver 1.19.x or better...

---

### Post by xgamerbass on 2018-01-31
Thank you very much, I had been dealing with this problem for months, many reinstallations, headaches and rages. You are a hero. ty.

---

### Post by fallout4all on 2018-02-18
Anyone have a weird lags/freezes when use Chrome and Steam, when Prime Sync enabled?
And anyone have a [COLOR=#333333][FONT=DINWebPro]VGA-0 (CRT-0) display in xrandr?[/FONT][/COLOR]

---

### Post by mc4man on 2018-02-25
Will not set as of kernel 4.15 as is currently in in 18.04, 4.13 is fine..

---

### Post by frnkln on 2018-03-02
Looked for this solution for a long time ! Thx

The only issue i have now is that it takes about 30secs until the shutdown window
appears (if i click in the top right corner at gnome DE).

Can i do something about that?

greets

---

### Post by aliuygurerol on 2018-05-03
> **mc4man said:**
> Will not set as of kernel 4.15 as is currently in in 18.04, 4.13 is fine..

There is a way to make it work on kernel 4.15 with nvidia 390, check the link below for the solution:

[https://www.reddit.com/r/linuxquestions/comments/8fb9oj/how_to_fix_screen_tearing_ubuntu_1804_nvidia_390/](https://www.reddit.com/r/linuxquestions/comments/8fb9oj/how_to_fix_screen_tearing_ubuntu_1804_nvidia_390/)

---

### Post by sylvain77 on 2018-06-19
Hello!

I tried to follow this procedure but sadly it is not working.

OK I have ubuntu 16.04 (kernel 4.4.0-128-generic) and a nvidia 940M on a dell laptop.
Here are the drivers currently installed on my machine:

[ATTACH=CONFIG]280149[/ATTACH]

And here is how I tried to activate modeset:
[ATTACH=CONFIG]280148[/ATTACH]

[ATTACH=CONFIG]280150[/ATTACH]

[ATTACH=CONFIG]280151[/ATTACH]

As you can see it does not activate vsync.

I do not really know what to do if anyone can help thank you!

---

### Post by mc4man on 2019-02-21
As of 18.04 there is no need to do anything as KMS modeset is default enabled now for nvidia drivers.

---

