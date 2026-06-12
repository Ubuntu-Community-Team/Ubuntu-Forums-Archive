---
title: "[SOLVED] Virtualbox &amp;amp; gutsy"
date: 2007-10-19
forum: General Help
---

### Post by Balazs_noob on 2007-10-19
Hi guys
i just installed Virtual box on gutsy and i get
```

Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
0x80004005
Component: 
Host
Interface: 
IHost {81729c26-1aec-46f5-b7c0-cc7364738fdb}
Callee: 
IMachine {31f7169f-14da-4c55-8cb6-a3665186e35e}

```
so the USB doesn't work , any ideas ?? :)

Balázs

---

### Post by sensimilla on 2007-10-19
I've got the same problem after doing the upgrade.

I've tried with Virtualbox 1.52 and 1.50

Ive added the line to change permisssions for usb devices as recomended here:

[http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04](http://www.virtualbox.org/wiki/USB_on_Ubuntu_7.04)

Also tried completely removing and reinstalling Virtual Box.

---

### Post by tubasoldier on 2007-10-19
I have the same issue. No USB in VirtualBox, which pretty much makes it useless for me since I only use it to deposit checks into my bank account from home.

 I have been using Gutsy since the first beta came out. This issue popped up about two weeks ago after a kernel upgrade.

---

### Post by Balazs_noob on 2007-10-19
lets hope the issue will be solved soon
because i would need usb too on my virtual machine 
:popcorn:
in the virtual box forums i haven't found anything useful :(

---

### Post by dethell on 2007-10-19
I just tried this:

[http://ubuntuforums.org/showthread.php?t=525969](http://ubuntuforums.org/showthread.php?t=525969)

and it works now.

David

---

### Post by FredB on 2007-10-19
Well, for some technical reason (no x86_54 emulation), I am using VMWare Server, and nothing to complain about it. :)

---

### Post by sensimilla on 2007-10-19
I had already set the permisions as described in the other thread.

According to sandervl over at the the Virtualbox forum who works for Innotek:

> Ubuntu removes usbfs in Gutsy. We rely on that for USB, so currently there's no easy solution. Perhaps you can compile it back into the kernel. 

OpenSuse once tried the same thing until they realized it was a very bad idea. (it also breaks VMWare)

anyway, I think I have found the answer here:

[http://www.virtualbox.org/ticket/747]("http://www.virtualbox.org/ticket/747")

I'll reproduce it here.

You need to edit an init script:
```
sudo gedit /etc/init.d/mountdevsubfs.sh
```
Then look for the following:
```
    #
    # Magic to make /proc/bus/usb work
    #
    #mkdir -p /dev/bus/usb/.usbfs
    #domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    #ln -s .usbfs/devices /dev/bus/usb/devices
    #mount --rbind /dev/bus/usb /proc/bus/usb
```
Remove the #'s from the last four lines so it looks like this :
```
    #
    # Magic to make /proc/bus/usb work
    #
    mkdir -p /dev/bus/usb/.usbfs
    domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount --rbind /dev/bus/usb /proc/bus/usb

```
Reboot

This seems to have fixed the issue for me.

---

### Post by Balazs_noob on 2007-10-19
Thanks [sensimilla]("http://ubuntuforums.org/member.php?u=284652")

with your solution it works for me too 
:)

:guitar:

---

### Post by maxseamus on 2007-10-19
This worked for me as well. Thank you!

---

### Post by CaseyR on 2007-10-25
sensimilla's solution worked for me too.

thanks!

---

### Post by GoodPanos on 2007-10-31
=D>Yep!  Another happy camper here!

You might have to take it further though, after you plug in a USB device.  There is a chance you might get an error that you do not have access to the USB device.  If that happens do the following.
```
sudo gedit /etc/udev/rules.d/40-permissions.rules
```
...and change
```
SUBSYSTEM=="usb_device",		MODE="0664"
```
to
```
SUBSYSTEM=="usb_device",		MODE="0666"
```
After that you will be rocking :guitar:

---

