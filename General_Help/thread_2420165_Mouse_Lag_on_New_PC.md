---
title: "Mouse Lag on New PC"
date: 2019-05-31
forum: General Help
---

### Post by jeremybearemy on 2019-05-31
Hi all, I hope this is the right place to post this. I have two computers, an eight year old Acer laptop and a new built desktop with Ryzen 5 and RX580, both systems running Xubuntu 18.04.2. I'm using a logitech wireless mouse which I transfer between the two computers. My problem is this, on the laptop, the mouse works fine and dandy, but on the new desktop, it freezes up for a second every now and then. Under normal use, just browsing the internet, installing packages etc, the lag is very rare, but if I'm watching a lot of full screen video, it increases a little. The biggest problem is when playing Minecraft, the lag gets worse over time until, after a couple of hours, the mouse hardly works at all. I then shut down minecraft and the lag continues for a little while until eventually the mouse returns to working semi normally. Does anyone have any idea what might be causing this problem, and how I might go about fixing it? I'm a long-time Ubuntu user, but don't know a great deal of in-depth stuff about what's going on under the hood, so any help at all would be appreciated.

I should add, I've followed the replies in some old "mouse lag" posts here on the forums, but those actions haven't made any difference.

Thanks in advance!

---

### Post by Autodave on 2019-05-31
My first step would be to try with a wired mouse to see what happens.

---

### Post by jeremybearemy on 2019-05-31
Should have thought to try that first, lol. I've spent a few quid on a wired mouse, and I'll check back in once it arrives and I've tried it out. If it's any different, what would that indicate as the problem? I wonder because the same mouse works fine on the older computer, and using a wired mouse isn't a long-term solution for me as the computer is in my living room and about 8 feet away from where I sit.

---

### Post by CatKiller on 2019-05-31
> **jeremybearemy said:**
> If it's any different, what would that indicate as the problem?
It gives you a place to start.

If the new mouse is fine, you can look at how the connection's working, regressions with input, that kind of thing.

If the new mouse is the same, you can look at systemic things: memory usage, cpu usage, I/O, things like that.

There's rarely any magic thing that we can always immediately point at for any problem, it's a case of thinking about ways that things can fail in a particular way, and then trying to find ways that those causes might differ, to distinguish between them.

---

### Post by jeremybearemy on 2019-05-31
Thanks for the info. New mouse arrives tomorrow, so I'll try it then. I've also installed Debian alongside my XUbuntu instance, so I'll try both on there too.

---

### Post by jeremybearemy on 2019-06-01
Okay, after a couple of hours minecrafting with a cheap, wired USB mouse plugged into the same port the wireless mouse was previously in, everything seems fine. Haven't been able to try the mice in Debian because I can't get multimc (minecraft launcher) to work. Wireless mouse still lags as before. Any suggestions as to what I should check to track down the cause of this?
[edit] Just to confirm, the wireless mouse is less than a year old, has a new battery in it, and still works fine on my laptop running xubuntu 18.04.2, same OS on both computers.

---

### Post by CatKiller on 2019-06-01
> **jeremybearemy said:**
> Okay, after a couple of hours minecrafting with a cheap, wired USB mouse plugged into the same port the wireless mouse was previously in, everything seems fine.

OK.

If the old computer started as 18.04 and got upgraded to 18.04.2, and the new computer is a fresh install of 18.04.2, they'll be using different branches of the kernel. The 4.18 branch was initially available as the Hardware Enablement Stack for 18.04, but became the standard version for the 18.04.2 image. 18.04 started with the 4.15 branch.

You could try booting into 4.15 with your new computer, to see if it helps.

Another thing you could do is to check dmesg for messages about your mouse and its transmitter to see if it can help track down the mechanism of the issue.

---

### Post by jeremybearemy on 2019-06-01
Both were given clean installs of 18.04.2; the laptop a few months ago and the desktop when I built it just last week. Both are running kernel 4.18.0-15
Is there a straightforward way of downgrading the kernel to 4.15 (and reverting changes after testing) or do I have to compile and install it myself?

The wired mouse when connected gives the following in dmesg:
```

[ 1799.580615] usb 1-6: new low-speed USB device number 7 using xhci_hcd[ 1799.911256] usb 1-6: New USB device found, idVendor=045e, idProduct=0040, bcdDevice= 3.00
[ 1799.911258] usb 1-6: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[ 1799.911260] usb 1-6: Product: Microsoft 3-Button Mouse with IntelliEye(TM)
[ 1799.911261] usb 1-6: Manufacturer: Microsoft
[ 1799.930602] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:01.3/0000:01:00.0/usb1/1-6/1-6:1.0/0003:045E:0040.0008/input/input28
[ 1799.930716] hid-generic 0003:045E:0040.0008: input,hidraw2: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:01:00.0-6/input0

```

And the wireless mouse gives:
```

[10669.750914] usb 1-6: new full-speed USB device number 8 using xhci_hcd
[10670.094119] usb 1-6: New USB device found, idVendor=046d, idProduct=c534, bcdDevice=29.01
[10670.094123] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[10670.094126] usb 1-6: Product: USB Receiver
[10670.094128] usb 1-6: Manufacturer: Logitech
[10670.123586] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:01.3/0000:01:00.0/usb1/1-6/1-6:1.0/0003:046D:C534.0009/input/input29
[10670.183226] hid-generic 0003:046D:C534.0009: input,hidraw2: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:01:00.0-6/input0
[10670.209812] input: Logitech USB Receiver Mouse as /devices/pci0000:00/0000:00:01.3/0000:01:00.0/usb1/1-6/1-6:1.1/0003:046D:C534.000A/input/input30
[10670.209975] input: Logitech USB Receiver Consumer Control as /devices/pci0000:00/0000:00:01.3/0000:01:00.0/usb1/1-6/1-6:1.1/0003:046D:C534.000A/input/input31
[10670.267081] input: Logitech USB Receiver System Control as /devices/pci0000:00/0000:00:01.3/0000:01:00.0/usb1/1-6/1-6:1.1/0003:046D:C534.000A/input/input32
[10670.267236] hid-generic 0003:046D:C534.000A: input,hiddev1,hidraw3: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:01:00.0-6/input1

```
The only possible issue I can see here is that the wireless mouse seems to be identified twice and is labelled as both usb 0000:01:00.0-6/input 0 and /input1
I don't know if that fact will cause problems. If so, how might I go about fixing it?

A little aside, and possibly the answer to my own problem:
To get the wired mouse to the PC, I used a 3 meter USB2 extension cable, all well and good.
To save a little effort, when I switched the mice back, I plugged the receiver into the extension cable.
After a few minutes of use, no lag.
Then I plugged the receiver directly into the computer, immediate lag
It would appear that this is a signal interference issue. The laptop is below the TV and has line of sight to where I'm sitting with my mouse and keyboard, while the new PC is behind the TV and about 2 feet higher up. My conclusion is that the signal is being partially blocked by the TV. I can probably fix this by using the extension cable to simply move the receiver away from the TV.
Thanks for your help, guys. If the problem recurs, I'll pop back into this thread and post again, but for now this seems likely solved. Should I mark it as such?

---

### Post by CatKiller on 2019-06-01
> **jeremybearemy said:**
> Both were given clean installs of 18.04.2; the laptop a few months ago and the desktop when I built it just last week. Both are running kernel 4.18.0-15 
Ah, well, that would have been a straightforward solution if they'd been running different kernels. 
> Is there a straightforward way of downgrading the kernel to 4.15 (and reverting changes after testing) or do I have to compile and install it myself? 
Nah, it would have been really simple: both kernel trees are in the repository, so it would have been just installing linux-415, or whatever the metapackage is called, and then booting into that from the Grub menu. It doesn't look like that's the issue, anyway, though. 
>  A little aside, and possibly the answer to my own problem:
To get the wired mouse to the PC, I used a 3 meter USB2 extension cable, all well and good.
To save a little effort, when I switched the mice back, I plugged the receiver into the extension cable.
After a few minutes of use, no lag.
Then I plugged the receiver directly into the computer, immediate lag
I think we might have a winner. I suspect that when you aren't using the extension cable, your receiver is plugged into a USB 3 port. When you use the extension, it sets itself up as USB 2.

Input devices, like keyboards and mice, that are designed for USB 2 often go peculiar when plugged into a USB 3 port. I don't know exactly why. If you have a USB 2 port available, you could try that one instead.

---

### Post by jeremybearemy on 2019-06-01
Interesting, but I'm plugged into a USB 2 port on the computer. The device doesn't work at all in the USB 3 ports.
Whatever the root cause, having the receiver below the TV is working smoothly for me now, so I'm a happy camper!

---

### Post by CatKiller on 2019-06-01
> **jeremybearemy said:**
> Interesting, but I'm plugged into a USB 2 port on the computer. The device doesn't work at all in the USB 3 ports.
Whatever the root cause, having the receiver below the TV is working smoothly for me now, so I'm a happy camper!

Ah, OK. Glad it's working for you, anyway.

---

