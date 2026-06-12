---
title: "Palm LifeDrive"
date: 2006-11-05
forum: General Help
---

### Post by DagonX on 2006-11-05
I am trying to get my plam lifedrive to sync with Evolution/J-Pilot or anything. The problem is everytime I try to sync an error message: 
"The connection between your device and the desktop could not be be established...". I have also received an error message Ubunto stating that the device is not supported.

Is there any Linux PDA sync software the LifeDrive works with? If there isn't is there some that is comming.](*,)

---

### Post by chriscando on 2006-11-05
I have had the best luck with my TX hotsyncing over the network. If you have wireless availible give that a try, use the program found in System>Prefrences>PalmOS devices to set type of connection to Network.

If you are using the cable try:
```
tail -f /var/log/messages
```
and look where your lifedrive is attached to. Mine changes from ttyUSB0 to ttyUSB4 thats why it doesnt always sync. However if I add all the ports that it may show up on in System>Preferences>PalmOS devices (eg /dev/ttyUSB1) then it will work

good luck

---

### Post by h0mer on 2006-12-04
My lifedrive works flawlessly in Edgy. Followed these steps:

1- Load gpilot-applet into a panel and click it.

2- In the setup wizard, choose 'already synced in other machine' or something like that (instead of 'never synced elsewhere) 

3- Most importantly, set the input device to /dev/ttyUSB0 instead of /dev/pilot.

4- Press hotsync in palm, recognized instantly.

5- Set up conduits for syncing.

---

### Post by RAdams on 2006-12-29
a million thanks to homer, as that was exactly what fixed my problem.

---

### Post by RAdams on 2007-01-02
> **chriscando said:**
> I have had the best luck with my TX hotsyncing over the network. If you have wireless availible give that a try, use the program found in System>Prefrences>PalmOS devices to set type of connection to Network.

If you are using the cable try:
```
tail -f /var/log/messages
```
and look where your lifedrive is attached to. Mine changes from ttyUSB0 to ttyUSB4 thats why it doesnt always sync. However if I add all the ports that it may show up on in System>Preferences>PalmOS devices (eg /dev/ttyUSB1) then it will work

good luck

I tried the network sync, and it never finds the palm. What diagnostics/tips do you suggest?

---

### Post by goteetech on 2007-01-05
> **h0mer said:**
> My lifedrive works flawlessly in Edgy. Followed these steps:

1- Load gpilot-applet into a panel and click it.

2- In the setup wizard, choose 'already synced in other machine' or something like that (instead of 'never synced elsewhere) 

3- Most importantly, set the input device to /dev/ttyUSB0 instead of /dev/pilot.

4- Press hotsync in palm, recognized instantly.

5- Set up conduits for syncing.

Some devices and/or USB ports require /dev/ttyUSB1, try both USB0 and USB1 instead of /dev/pilot

---

### Post by RAdams on 2007-01-05
Yes, definitely try both. You can always use [FONT="Courier New"]tail -f /var/log/messages[/FONT] after attaching your Palm to see where it went off to. (Use [FONT="Courier New"]tail -f /var/log/messages | grep Handheld[/FONT] for a quick search to find the messages related to your Palm).

Also, I got netsync to work. I switched from amd64 to the 32-bit version; that's the only thing I actually changed. There could be an issue with the amd64 version... anyone with amd64 have the gumption to give netsync a go and read the debugging symbols? Or if you get it to work... that would be something. I just know that once I had the 32-bit version installed, it worked right away, no problem.

---

### Post by unclejac on 2008-01-10
Anyone know if this works with the 64 bit version now ?

I'm not having much luck syncing my Lifedrive via USB cable.

---

### Post by RAdams on 2008-01-10
What's the relevant output of messages?

---

### Post by unclejac on 2008-01-10
Hi RAdams, Thanks for replying:

Heres what i get when i use 

```
tail -f /var/log/messages
```

```
Jan 10 14:06:52 beta kernel: [18472.370684] usb 2-10: new high speed USB device using ehci_hcd and address 39
Jan 10 14:06:53 beta kernel: [18472.439153] usb 2-10: configuration #1 chosen from 1 choice
Jan 10 14:07:52 beta kernel: [18502.076255] usb 2-10: USB disconnect, address 39
Jan 10 14:07:52 beta kernel: [18502.216358] usb 2-10: new high speed USB device using ehci_hcd and address 40
Jan 10 14:07:52 beta kernel: [18502.286793] usb 2-10: configuration #1 chosen from 1 choice
Jan 10 14:09:20 beta kernel: [18547.771262] usb 2-10: USB disconnect, address 40
Jan 10 14:09:20 beta kernel: [18547.906932] usb 2-10: new high speed USB device using ehci_hcd and address 41
Jan 10 14:10:24 beta kernel: [18579.701143] usb 2-10: new high speed USB device using ehci_hcd and address 42
Jan 10 14:10:24 beta kernel: [18579.767613] usb 2-10: configuration #1 chosen from 1 choice
Jan 10 14:10:42 beta kernel: [18588.955127] usb 2-10: USB disconnect, address 42
Jan 10 14:10:49 beta kernel: [18592.523551] usb 2-10: new high speed USB device using ehci_hcd and address 43
Jan 10 14:10:49 beta kernel: [18592.590001] usb 2-10: configuration #1 chosen from 1 choice
Jan 10 14:11:16 beta kernel: [18605.744898] usb 2-10: USB disconnect, address 43
Jan 10 14:11:16 beta kernel: [18605.929522] usb 2-10: new high speed USB device using ehci_hcd and address 44
Jan 10 14:11:17 beta kernel: [18606.211311] usb 1-10: new full speed USB device using ohci_hcd and address 4
Jan 10 14:11:17 beta kernel: [18606.311255] usb 1-10: not running at top speed; connect to a high speed hub
Jan 10 14:11:17 beta kernel: [18606.320338] usb 1-10: configuration #1 chosen from 1 choice
Jan 10 14:11:18 beta kernel: [18606.927637] usb 1-10: USB disconnect, address 4
Jan 10 14:11:19 beta kernel: [18607.270516] usb 2-10: new high speed USB device using ehci_hcd and address 45
Jan 10 14:11:19 beta kernel: [18607.336985] usb 2-10: configuration #1 chosen from 1 choice
Jan 10 14:12:59 beta kernel: [18658.831502] usb 2-10: USB disconnect, address 45
Jan 10 14:13:06 beta kernel: [18662.280924] usb 2-10: new high speed USB device using ehci_hcd and address 46
Jan 10 14:13:06 beta kernel: [18662.347405] usb 2-10: configuration #1 chosen from 1 choice
Jan 10 14:26:09 beta kernel: [19335.263089] usb 2-10: USB disconnect, address 46

```

:-?

[IMG]http://img91.imageshack.us/img91/1269/gpilotjy2.png[/IMG]

---

### Post by RAdams on 2008-01-10
Let me see your gPilotD Sync settings screen.

---

### Post by unclejac on 2008-01-10
[IMG]http://img231.imageshack.us/img231/3536/gpilotsettinggo1.png[/IMG]

---

### Post by unclejac on 2008-01-10
Just a quick note to say I managed to Hotsync my Lifedrive over the Network instead of using the USB cable . . . 

The network option worked first time and by comparison seemed a lot easier. :)

I'm still curious though as to what i was doing wrong with the USB settings? If anyone knows please let me know for future reference. 

Thanks for your responses RAdams!

---

### Post by RAdams on 2008-01-10
If you ever get bored, try: [https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

---

### Post by axel112 on 2008-01-15
> **RAdams said:**
> If you ever get bored, try: [https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

I only added visor to the /etc/modules file and restarted. Works great.

---

### Post by RAdams on 2008-01-18
Awesome! Can you update the Wiki?

---

### Post by amiga_os on 2008-04-08
I can't sync my LifeDrive.

I've followed all the instructions, and I've done everything on the wiki.

Hotsyncing with the cable gives me the first hotsync picture on the lifedrive
Newsyncing over wifi doesn't even give me that.

Could someone post the steps of how to netsync?  Does your router need special settings?

---

