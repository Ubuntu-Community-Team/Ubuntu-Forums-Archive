---
title: "Freezing mouse"
date: 2007-04-09
forum: General Help
---

### Post by MarcoPau on 2007-04-09
Hello there, my mouse has been freezing pretty often lately, and the only way to wake it up has been the one of simply disconnecting and reconnecting it to the usb port. Lately, I'd say after my last feisty upgrade, I haven't been able to wake it up as usual, thus I really need to solve this problem now.

This is my xorg.conf mouse section:

        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"

I had "ExplorerPS/2" as protocol but I just changed it hoping it'd help, and it didn't.

These two lines come from /var/log/messages when I first disconnect the mouse, then I won't get any lines related to its new reconnection and further disconnections and reconnections:

usb 2-4: USB disconnect, address 2
ohci_hcd 0000:00:02.1: IRQ INTR_SF lossage 

What I can add is that I noticed that the number of opened firefox tabs influences the frequency of these freezes, and that the mouse won't have any problem under windoze, as it used to be till a couple of months ago also here under ubuntu. Debian gives the same problem as well.

Thanks for helping.
Ciao!

---

### Post by mssever on 2007-04-10
> **MarcoPau said:**
> Hello there, my mouse has been freezing pretty often lately, and the only way to wake it up has been the one of simply disconnecting and reconnecting it to the usb port. Lately, I'd say after my last feisty upgrade, I haven't been able to wake it up as usual, thus I really need to solve this problem now.

<snip>

These two lines come from /var/log/messages when I first disconnect the mouse, then I won't get any lines related to its new reconnection and further disconnections and reconnections:

usb 2-4: USB disconnect, address 2
ohci_hcd 0000:00:02.1: IRQ INTR_SF lossage 

What I can add is that I noticed that the number of opened firefox tabs influences the frequency of these freezes, and that the mouse won't have any problem under windoze, as it used to be till a couple of months ago also here under ubuntu. Debian gives the same problem as well.
Based on /var/log/messages, I don't think that your Xorg configuration has anything to do with your problem. It appears that for some reason your system isn't seeing your mouse when you plug it in again. Does this happen with other kinds of USB devices?

I'm not sure what's responsible for detecting new USB devices. hal maybe?

Is the problem in Debian relatively new, as well? Also, do you know if it occurs in any Linux distro that is not based off Debian? My wild guess is that perhaps some hardware developed a minor glitch that is triggering a bug in hal (or some other program).

What I've said is mostly guessing, so please consider this post to be a free bump, and don't put too much stock in what I've said.

---

### Post by CocoAUS on 2007-04-10
I've had my mouse freeze a couple of times on bootup.  Then I just restart the machine and it works fine again.

Also, I have been having problems with Ubuntu thinking I'm double-clicking when I'm single-clicking, or it thinks I'm randomly holding and releasing when I'm really just holding.  Windows doesn't have this problem, and Ubuntu didn't used to.  Any ideas?  It's really annoying when I try to drag a file and Ubuntu instead opens it 4 times.

---

### Post by MarcoPau on 2007-04-11
So, when the mouse freezes all the usb freezes, i.e. if I try to plug in a usb flash drive, that won't work either, after the freezing.

What should I check next time it happens?

---

### Post by andrew.46 on 2007-04-11
Hi,

 Because I am very tired I can suggest an unusual solution to your problem:

> **MarcoPau said:**
> Hello there, my mouse has been freezing pretty often lately...

 Try knitting up a little jacket for it and definitely keep it indoors on really cold days ....

                                 Andrew

---

### Post by Swankyman on 2007-04-11
Hi

Im just wondering what chipset your computer has? Ive had the same problem as you for a while now.  Type in a terminal:
lspci 
and look for the usb lines, mine are like this:

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)

Thanks

Rich

---

### Post by MarcoPau on 2007-04-11
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)

---

### Post by Swankyman on 2007-04-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-kernel-di-i386-2.6/+bug/29994](https://bugs.launchpad.net/ubuntu/+source/linux-kernel-di-i386-2.6/+bug/29994) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi again,

You could try this:

In a terminal type (or copy and paste)

sudo gedit /etc/modprobe.d/blacklist

- and then 

Add a comment symbol (#) to the two lines as below:

#blacklist usbmouse
#blacklist usbkbd

And then add this aditional line:

blacklist usbhid

----

(THIS IS FROM THIS BUG: [https://bugs.launchpad.net/ubuntu/+source/linux-kernel-di-i386-2.6/+bug/29994](https://bugs.launchpad.net/ubuntu/+source/linux-kernel-di-i386-2.6/+bug/29994))

This should change the driver loaded for the mouse and thus may not have the same issues. 
[B]
:) Make sure you post a bug report either way :)  So it gets fixed someday[/B]

Rich

P.S this makes no difference to me. It still dies after a few mins :confused:

---

### Post by Swankyman on 2007-04-11
Another thing to try:

Go into your bios

See if you can find an USB legacy option 

- Change it 

-Save and exit

and hope :popcorn: 

Rich

---

### Post by MarcoPau on 2007-04-12
Thanks! Gonna try tomorrow, will definitely let you know.

---

### Post by mvaranda on 2007-04-14
My Toshiba was working fine with 6.06 but USB started freezing after upgrading to 6.10.

The fix that worked for my machine was the following:

sudo gedit /boot/grub/menu.lst

change boot option (red):

kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash [COLOR="Red"]noapic irqpoll pci=routeirq[/COLOR]

I hope it helps.
Take care

---

