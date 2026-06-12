---
title: "Can't find sdpd"
date: 2007-03-24
forum: General Help
---

### Post by gertoft on 2007-03-24
Hi.

Trying to get a bluetooth dongle working but seems to fail because the sdp daemon isn't running. What's strange is that I don't seem to have an sdp daemon (/usr/sbin/sdpd) installed even though I have the bluez-utils package installed. What package is sdpd located in?

//Nick

---
Running Ubuntu-7.04

---

### Post by LucasLinard on 2007-04-05
Sme problem here.
Do you use kubuntu?
I used ubuntu 70.4 and had no problem. When I switched to Kubuntu his began to happen.

---

### Post by mslonik on 2007-05-07
The same problem here. After upgrade from Edgy (Kubuntu 6.10) to Feisty (Kubuntu 7.10) system complains about lack of sdp connection and sdpd deamon. Any ideas, what is wrong?

Kind regards,
Maciej (mslonik)

---

### Post by blue_shift on 2007-05-20
I'm having the same problem, I've tried sdptool but to no avail. It appears kde cannot recognise the bluetooth hardware in my case. Is this the same for anyone else?

[[QUOTE="Launchpad"]If KDE checks for the sdpd process, then this is a KDE bug. Running "hcid -s" provides the same functionality as "sdpd".[/QUOTE]](https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/96916)

Might be worth re-installing bluetooth framework.

---

### Post by iZm on 2007-08-02
running...

```
> sudo sdptool add <servicehere>
```

will start an sdpd service. The following starts the NAP service..

```
> sudo sdptool add NAP
```

I just need to figure out how to set this to come up automatically when bluetooth does :confused:

---

### Post by iZm on 2007-08-02
Ah, got it. in /etc/default/bluetooth set...

```
SDPTOOL_OPTIONS="add NAP"
```

---

### Post by monojohnny on 2008-06-13
(Partially solved, might help somebody else - I *think* there may be a mistake in the startup/shutdown scripts...not sure, read on...):

I had some issues with getting Bluetooth to work out of the box with the following:

Using 8.0.4 "Hardy Heron" on a Dell Optiplex GX 110 and a USB bluetooth dongle, the dongle ID's itself as (using 'lsusb'):

Bus 001 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

But the bluetooth Applet in the GUI shows no services.

"hcitool dev" shows no devices.

"ps -eaf|grep hcid" shows no daemon started.

Reading through this post gave some clues: the startup script (/etc/init.d/bluetooth) has a couple of lines that read:

SDPD=/usr/sbin/sdpd
...
"test -x $SDPD || exit 0"
...

But my system has no file called '/ust/sbin/sdpd' - hence the script was exiting out.

This is what I did - and got the bluetooth dongle working (at least partially - still having issues connecting TO the machine, but am now OK browsing a Nokia phone):

Editing script /etc/init.d/bluetooth and just commented out the "test -x " line entirely. (this is not good practice, should have edited the 'master' stop/start script and pushed out the changes properly, but hey..)

(Just to mention this, not sure this is actually a required step : sudo apt-install bluetooth as well - this was just a blind step I tried when I hadn't realised probably the thing had been fixed at this point).

Started up bluetooth services again:

"sudo /etc/init.d/bluetooth start"
"sudo hciconfig hci0 up" (Again, can't remember whether this is necessary step after running the full startup script or not...) 
"ps -eaf|grep hcid" - this time 'hcid' shows up.

TIP: When troubleshooting - If you use the bluetooth Applet thing in the KDE and set the option "Only Display When Adapter Present" you can see the little blue icon appear, once things seem to start working - good visual clue.

I also tried the 'sdptool -add NAS' as detailed in this post, didn't seem to need to do this though.

After a reboot , the service starts up OK and I can browse the phone OK; so I think the main thing is to change the startup script. Probably altering the script (going from the previous posting here) to leave the 'test' in there, but create a link 'sdpd' to 'hcid' and change the subsequent call to include the '-s' flag might work better. ? dunno

---

