---
title: "ATI Remote wonder not working after kernel upgrade"
date: 2007-09-08
forum: General Help
---

### Post by markp1989 on 2007-09-08
So i recently upgraded my kernel to  Gutsy's developing kernel using this guide

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

Everything works fine, except my ATI remote Wonder, doesn't work at all.

also i cannot boot with my old kernel, because i had to update the nvidia drivers and the old kernel doesnt seem to like them

Does any one know if there is a way to get the remote to work with this kernel, or will i have to  use my old one, because since upgrading my computer has booted faster, so i would like to keep the new one.

Any help i get will be greatly appreciated , thank you in advanced

---

### Post by JamesHolden on 2007-10-22
i am also running into this, i will be watching this thread.

if i run sudo modprobe ati_usb, its not found.. tried changing USB ports, tried gizmod (what i used with fiesty), ohwell.

---

### Post by Tuxbeej on 2007-10-23
I've just installed Mythbuntu 7.10, and although my ATI Remote Wonder *is* working, most of the keys spelled out in LIRC aren't doing anything in their applications.  MythTV and MPlayer are detecting the keypresses from the remote that correspond to keyboard commands (up, down, left, right, enter, a, b, c, d, e, f).  Other than that, I'm not getting any of the predefined LIRC commands.

I'm assuming this is because the ati_usb module is missing from the modules directory.  Is there a package we can install to sort this out?  Something we can key in ourselves?  I'm trying to keep the install as vanilla as possible, so if I don't have to custom-compile anything, I'd be a happy man.

Thanks much.

---

### Post by ocpaul on 2007-10-23
(ATI remote wonder I)
My remote responds, only few buttons.
But none commands form lirc is working. 
I stoped lirc and my remote still works. i think gutsy default taking over lirc?
Do i need to disable something b4 getting lirc to work?

---

### Post by scoultas on 2007-10-23
My ati remote also stopped working after the upgrade to Gutsy.

I got it working again by performing the following steps (loosely following the guide at [http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder](http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder), which doesn't specifically cover Ubuntu).

Caveat before I begin - I've upgraded Ubuntu through about the last 4 versions without doing a fresh install at any point, so my state after the upgrade might well be different than anyone else's!

1. Type ```
 lsmod | grep ati
```

I get : 

```
cpufreq_conservative     8072  0 
ati_remote             13064  0 
lirc_atiusb            19360  1 
lirc_dev               15860  1 lirc_atiusb
usbcore               138632  7 ati_remote,lirc_atiusb,usbhid,ehci_hcd,uhci_hcd,ohci_hcd
```


2. blacklist ati_remote : 

Disable it by adding a new line ```
blacklist  ati_remote
``` to /etc/modprobe.d/blacklist

3. remove the ati_remote module : 

```
sudo rmmod ati_remote
```


(guide suggested would have to unplug device - I didn't have to)

4. Added the following to /etc/modprobe.conf (I actually had to create the file first as it didn't exist)

```
alias char-major-61 lirc_atiusb
alias lirc_dev lirc_atiusb

```

At this point, I tried to run lircd, but it was already running.  Then I typed ```
 irw
``` and pressed the buttons on the remote, and could see suitable responses for the key presses on the screen.

Hope this helps anyone still struggling!

---

### Post by sanman951 on 2007-10-23
Just tried your guide and it didn't work for me as I still get no responce at all.  Anyone have any other ideas?

---

### Post by Tuxbeej on 2007-10-24
Aha.  Found it.

My ATI Remote Wonder does not seem to work with the kernel driver.  It does work with the userspace driver, though.  It is model 5000015900A.

Fortunately, Mythbuntu has settings for that model, and it lists it as ATIUSB_5000015900A in its .lircrc.  I modified the lircd.conf and changed the name of the remote that *was* detected (in my case, it thought mine was called "ati_remote_wonder_rf") to ATIUSB_5000015900A and then everything worked just fine.

Except that the buttons were off from what I wanted.  I ended up using an online tool to build my .lircrc, then modified the button names in lircd.conf to correspond with what the online tool used as a guide.  After everything was matched up correctly, I have a near-perfect remote setup (just a couple of things to change in my MythTV settings).

Thanks for the mention of 'irw', BTW.  I'd neglected that tool in the past, but it helped me figure out when my lirc settings were working.

---

### Post by sanman951 on 2007-10-24
When I run lsmod | grip ati I get

```
$ lsmod | grep ati
cpufreq_conservative     8072  0 
lirc_atiusb            19530  1 
lirc_dev               15860  1 lirc_atiusb
usbcore               138632  11 ndiswrapper,lirc_atiusb,hci_usb,xpad,usbhid,lmpcm_usb,usb_storage,libusual,ehci_hcd,uhci_hcd
```

and lirc lists ATIUSB_5000015900A in the conf file but I still get no response from the remote.  I know the remote works cause when i plug it into my Feisty machine it works fine but nothing on my Gusty box.

Any help would be great casue Im kinda a noob @ linux

---

### Post by markp1989 on 2007-10-28
> **scoultas said:**
> My ati remote also stopped working after the upgrade to Gutsy.

I got it working again by performing the following steps (loosely following the guide at [http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder](http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder), which doesn't specifically cover Ubuntu).

Caveat before I begin - I've upgraded Ubuntu through about the last 4 versions without doing a fresh install at any point, so my state after the upgrade might well be different than anyone else's!

1. Type ```
 lsmod | grep ati
```

I get : 

```
cpufreq_conservative     8072  0 
ati_remote             13064  0 
lirc_atiusb            19360  1 
lirc_dev               15860  1 lirc_atiusb
usbcore               138632  7 ati_remote,lirc_atiusb,usbhid,ehci_hcd,uhci_hcd,ohci_hcd
```


2. blacklist ati_remote : 

Disable it by adding a new line ```
blacklist  ati_remote
``` to /etc/modprobe.d/blacklist

3. remove the ati_remote module : 

```
sudo rmmod ati_remote
```


(guide suggested would have to unplug device - I didn't have to)

4. Added the following to /etc/modprobe.conf (I actually had to create the file first as it didn't exist)

```
alias char-major-61 lirc_atiusb
alias lirc_dev lirc_atiusb

```

At this point, I tried to run lircd, but it was already running.  Then I typed ```
 irw
``` and pressed the buttons on the remote, and could see suitable responses for the key presses on the screen.

Hope this helps anyone still struggling!

i tried that, i get loads of text on the terminal every time i press a button on the remote, how do i configure what i want the buttons to do?

see screen shot, it says mouse down, but the mouse stays still

---

### Post by greg963 on 2007-10-28
Markp1989, you'll have to set up a ~/.lircrc file to set up the keys for what you want them to do, see [[COLOR="Blue"]this example[/COLOR]]("http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder#Example_of_a_lircrc_-_works_with_lircd.conf_above")

Mouse functionality requires some additional setup in xorg.conf, there are some guides out there to set it up.

---

### Post by sanman951 on 2007-11-01
I tried a reinstall and now when I do  lsmod | grep ati I get nothing at all except  

cpufreq_conservative     8072  0 
but when I run irw I get a responce on the screen.  Any one have any sugestions cause this is really makeing me want to go back to feisty

---

### Post by RoswellU on 2007-11-05
> **Tuxbeej said:**
> Aha.  Found it.

My ATI Remote Wonder does not seem to work with the kernel driver.  It does work with the userspace driver, though.  It is model 5000015900A.

I think I installed the kernel driver too and that's causing my remote wonder not to work (Part#5000023600), but I can't seem to remember how I installed it... 

So two questions:
- do I have to 'uninstall' the kernel driver somehow
- how can I install the userspace driver

Any help would be appreciated as I've been messing around with it for hours.
Thanks in advance.

---

### Post by jhfry on 2007-11-07
> **scoultas said:**
> 
4. Added the following to /etc/modprobe.conf (I actually had to create the file first as it didn't exist)

```
alias char-major-61 lirc_atiusb
alias lirc_dev lirc_atiusb

```
!

I tried this and it does indeed allow my remote to work... however, whenever I boot I get a ~5 minute pause during hardware initialization:
```

[   42.912943] lirc_dev: IR Remote Control driver registered, at major 61 
[   42.984630] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   43.003853] 
[   43.003857] lirc_atiusb: USB remote driver for LIRC $Revision: 1.61 $
[   43.003974] lirc_atiusb: Paul Miller <pmiller9@users.sourceforge.net>
[  223.093382] lp0: using parport0 (interrupt-driven).
[  223.474675] Adding 465844k swap on /dev/hda5.  Priority:-1 extents:1 across:465844k

```
* Notice the timestamps

Sometimes the ACPI line comes after the lirc_atiusb lines.... but either way, removing /etc/modprobe.conf eliminates the hang during boot... but renders my remote unusable!

Any guidance would be appreciated!

---

