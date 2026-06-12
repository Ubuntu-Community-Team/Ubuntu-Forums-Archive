---
title: "System does not recognize the cell phone as a storage device"
date: 2014-02-10
forum: General Help
---

### Post by offir on 2014-02-10
I have two computers
On the first installed Ubuntu 10.04
and on The second computer installed Ubuntu 12.04

They work right
Except for one annoying problem

I have a Motorola cell phone
Model i9

When I connect it into the computer
The computer recognizes the cell phone

But I do not have access to information that On the memory card
I do not get icon of an external storage device


Here is the output of ```
lsusb
``` command
As you see the computer detects the cell phone

But do not give any access to the memory card



```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0557:2213 ATEN International Co., Ltd 
Bus 002 Device 002: ID 0557:7000 ATEN International Co., Ltd Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0c44:4810 Motorola iDEN 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

What could be the problem
How can I access the memory card




in Windows operating system
It works correctly { in a Rare coincidence of nature :-)}

---

### Post by tomearp on 2014-02-10
Please see [this previous thread]("http://ubuntuforums.org/showthread.php?t=1903254").

---

### Post by offir on 2014-02-10
I thought there might be some change
Two years have passed Since then

Currently bypass solution
I take out the memory card and put it in a device connects to  usb

But it is annoying

---

### Post by tomearp on 2014-02-10
From looking at the user manual for the handset it says to select the following:
Main menu > Settings > Connections > USB > Memory Card Access
Then plug the cable in.

There does not appear to be a technical specification in the manual so it doesn't state anywhere what operating system(s) it is supposed to be compatible with.

---

### Post by offir on 2014-02-11
Cell phone is already in in this state

I tried other options
Modem mode
Network card disconnected

---

### Post by Topsiho on 2014-02-11
> **offir said:**
> I have two computers
On the first installed Ubuntu 10.04
and on The second computer installed Ubuntu 12.04


Please be aware that Ubuntu 10.04 is obsolete now and is not supported anymore.

Topsiho

---

### Post by offir on 2014-02-12
Yes I know
But
No need to fix what is not broken

Maybe
I will upgrade next LTS version
In two months if I'm not mistaken

---

### Post by Topsiho on 2014-02-12
> **offir said:**
> 
No need to fix what is not broken

10.04 might not be broken,  it IS obsolete: you'll not get any security fixes anymore, so, if you are connected to internet, it is unwise to use this version. So a "fix" is necessary here.

Ubuntu 14.04 LTS will be distributed in next April (that is what the .04 means), so you could try that, or if it is too heavy for your computer, you might try the lighter versions, Xubuntu or Lubuntu. But please drop 10.04, thanks to MS the internet is already as dangerous as it is now.

Topsiho

---

### Post by offir on 2014-02-13
>  thanks to MS the internet is already as dangerous as it is now.
:p

Like I said
I probably will upgrade to version 14.04

I still get updates to 10.04
I do not like the unity interface
I prefer the gnome 

That's why I continued with this system

---

### Post by 3rdalbum on 2014-02-13
> **offir said:**
> :p

Like I said
I probably will upgrade to version 14.04

I still get updates to 10.04
I do not like the unity interface
I prefer the gnome 

That's why I continued with this system

You receive updates for anything that's also in Ubuntu Server, but there are no updates for any of the software that's in Ubuntu Desktop.

You can install Gnome on 12.04 and 14.04, so really that's not a reason to stay on 10.04.

Stay on 10.04 if you like, but you'll become increasingly isolated by not being able to use newer devices/hardware, having an old Firefox and gradually not being able to access new websites, not being able to get good support on the forums and not being able to update any software.

---

