---
title: "Need HOW-TO on Bluetooth, WM5 and Internet Sharing"
date: 2007-04-04
forum: General Help
---

### Post by edmondt on 2007-04-04
I have done my search and I have not found a solution which allows me to access the internet over bluetooth with my Pocket PC so that I do not have to turn WIFI on my WM5 device.

The closest thing I found was this:

[http://www.howtoforge.com/bluetooth_pand_debian_etch](http://www.howtoforge.com/bluetooth_pand_debian_etch)

But it doesn't work for WM5 :S

Does anyone have a solution? I could install the bluetooth into a XP machine, but that's not a real linux solution right? :KS

---

### Post by bdogg64 on 2007-04-07
I managed to get my internet over bluetooth, with wm5 and internet sharing. Here is what I did. I'm using t-mobile internet with a T-Mobile MDA that has internet sharing.  

Part of this guide is from [http://news.softpedia.com/news/Connect-to-the-Internet-from-Anywhere-Using-a-GPRS-Connection-50670.shtml](http://news.softpedia.com/news/Connect-to-the-Internet-from-Anywhere-Using-a-GPRS-Connection-50670.shtml)

If your laptop has an incorporated bluetooth adaptor and so does your phone, you could try the following to connect your computer to the Internet through the phone's GPRS connection:

1. Open Synaptic and install the following packages:
&#8226; bluez-utils
&#8226; bluez-passkey-gnome
&#8226; gnome-bluetooth
&#8226; bluez-pin*

2. Turn your phone's BT connection and set its visibility to 'Show to all' or equivalent.

3. Open a terminal and type:

```
hcitool scan
```

You should see something like: 

```
Scanning ...
00:0E:07:37:7C:BD 6230i

```
(Your device identification will be different)

4. Open /etc/bluetooth/hcid.conf in a text editor and set:
autoinit yes
security auto
pairing multi
passkey whatever-you-want

5. Press ALT+F2 and run the 

```
bluetooth-applet
```

6.  On your mobile phone, go to bluetooth settings, search for a new device and add your computer and pair it using the passkey you set up before

7.  On your mobile phone to Start->Programs->Internet Sharing, choose Bluetooth PAN, and your NetworkConnection (Mine is T-Mobile GRPS/EDGE), and choose Connect

Open a terminal:

8.  sudo modprobe bnep

9.  sudo pand --connect 00:0E:07:37:7C:BD

10.  sudo ifconfig bnep0

11.  sudo ifup bnep0

It should assign you an IP address automatically. And thats it!

I'm actually writing this guide using my internet over bluetooth, so I know it works for sure!

I hope this helps

---

### Post by Maestro23 on 2007-04-07
Another log on the fire here: [https://help.ubuntu.com/community/FrostWire?action=fullsearch&context=180&value=bluetooth&titlesearch=Titles](https://help.ubuntu.com/community/FrostWire?action=fullsearch&context=180&value=bluetooth&titlesearch=Titles)

Good luck.

---

### Post by edmondt on 2007-04-10
I'm using Edgy and this is how far I got...

root@edmond-laptop:/home/edmondt# hcitool scan
Scanning ...
        00:12:37:9D:BD:17       Edmond Tong (My Pocket PC)
root@edmond-laptop:/home/edmondt# sudo pand --connect 00:12:37:9D:BD:17
root@edmond-laptop:/home/edmondt# sudo ifconfig bnep0
bnep0: error fetching interface information: Device not found

I did :hidd --connect 00:12:37:9D:BD:17" 

and got:
Can't get device information: Success

lsusb returns the following:

root@edmond-laptop:/home/edmondt# lsusb
Bus 004 Device 012: ID 1131:1001 **Integrated System Solution Corp. KY-BT100 Bluetooth Adapter**
Bus 004 Device 011: ID 0bb4:0bce High Tech Computer Corp. 
Bus 004 Device 007: ID 046d:08b3 Logitech, Inc. QuickCam Zoom
Bus 004 Device 006: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 004 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 004 Device 005: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 004 Device 004: ID 03f0:1411 Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c70a Logitech, Inc. 
Bus 002 Device 003: ID 046d:c70e Logitech, Inc. 
Bus 002 Device 002: ID 046d:0b02 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  



I have a logitech bluetooth mouse and keyboard installed by the way... please help :)

---

### Post by bdogg64 on 2007-04-11
> **edmondt said:**
> I'm using Edgy and this is how far I got...

root@edmond-laptop:/home/edmondt# hcitool scan
Scanning ...
        00:12:37:9D:BD:17       Edmond Tong (My Pocket PC)
root@edmond-laptop:/home/edmondt# sudo pand --connect 00:12:37:9D:BD:17
root@edmond-laptop:/home/edmondt# sudo ifconfig bnep0
bnep0: error fetching interface information: Device not found

I did :hidd --connect 00:12:37:9D:BD:17" 

and got:
Can't get device information: Success

lsusb returns the following:

root@edmond-laptop:/home/edmondt# lsusb
Bus 004 Device 012: ID 1131:1001 **Integrated System Solution Corp. KY-BT100 Bluetooth Adapter**
Bus 004 Device 011: ID 0bb4:0bce High Tech Computer Corp. 
Bus 004 Device 007: ID 046d:08b3 Logitech, Inc. QuickCam Zoom
Bus 004 Device 006: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 004 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 004 Device 005: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 004 Device 004: ID 03f0:1411 Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c70a Logitech, Inc. 
Bus 002 Device 003: ID 046d:c70e Logitech, Inc. 
Bus 002 Device 002: ID 046d:0b02 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  



I have a logitech bluetooth mouse and keyboard installed by the way... please help :)

Did you get any output from 

```
sudo modprobe bnep
```

---

### Post by edmondt on 2007-04-11
No output or errors with sudo modprobe bnep

---

### Post by bdogg64 on 2007-04-11
> **edmondt said:**
> No output or errors with sudo modprobe bnep

Do you have a bnep adapter when you run 

```
iwconfig
```

bnep0 may be different since you have multiple adapters installed

---

### Post by edmondt on 2007-04-12
edmondt@edmond-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

---

### Post by bdogg64 on 2007-04-12
Look at your logs after you plug in your bluetooth adapter and see if it detects it correctly and post it if you can

---

### Post by bimmerd00d on 2007-04-19
I'm having issues on my Inspiron E1705 with bluetoof!

here's my lsusb.

bimmerd00d@bhlaptop:~$ lsusb
Bus 005 Device 011: ID 0a5c:4503 Broadcom Corp. 
Bus 005 Device 010: ID 0a5c:4502 Broadcom Corp. 
Bus 005 Device 009: ID 413c:8126 Dell Computer Corp. 
Bus 005 Device 008: ID 0a5c:4500 Broadcom Corp. 
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000

---

### Post by MauroKTM on 2007-06-24
Dear bdogg64

It works fine on my Dell d620 and HTC TyTN with WM5. But Is there a way to launch a single "script" that connect my laptop to the WM5  device (after connect it to internet) and start to browse Internet?... 

Thnx a lot

Mauro

---

### Post by bdogg64 on 2007-06-25
> **MauroKTM said:**
> Dear bdogg64

It works fine on my Dell d620 and HTC TyTN with WM5. But Is there a way to launch a single "script" that connect my laptop to the WM5  device (after connect it to internet) and start to browse Internet?... 

Thnx a lot

Mauro

You could make a script that does the commands for you e.g.

```

#!/bin/bash

modprobe bnep

pand --connect your_phone_bluetooth_address

ifconfig bnep0

ifup bnep0

```

and save it as /usr/bin/bluenet.sh (or whatever name you want), then

```
sudo chmod +x /usr/bin/bluenet.sh
```

to run it, just run

```
sudo bluenet.sh
```

hopefully this gets ya started

---

### Post by tmortn on 2007-07-03
Dude... YOU ROCK!

Dell D820 with 8525/Hermes posting through bluetooh PAN connection.

---

### Post by dsanders79 on 2007-07-11
My solution was slightly different.  I am using 6.06 (Dapper Drake) so that may be the difference.  

First I used the following to get my MAC address:
```
hcitool scan
```

Use that MAC address on the second line of the following code.

```
sudo modprobe bnep
sudo pand –role PANU –connect 00:12:D2:02:69:0F
sudo dhclient bnep0
```

If you would like to see my slightly longer writeup please go here:
[http://www.vmcolonel.net/?p=16]("http://www.vmcolonel.net/?p=16")

---

### Post by puyi on 2007-07-17
> **bdogg64 said:**
> I managed to get my internet over bluetooth, with wm5 and internet sharing. Here is what I did. I'm using t-mobile internet with a T-Mobile MDA that has internet sharing.  

Part of this guide is from [http://news.softpedia.com/news/Connect-to-the-Internet-from-Anywhere-Using-a-GPRS-Connection-50670.shtml](http://news.softpedia.com/news/Connect-to-the-Internet-from-Anywhere-Using-a-GPRS-Connection-50670.shtml)

If your laptop has an incorporated bluetooth adaptor and so does your phone, you could try the following to connect your computer to the Internet through the phone's GPRS connection:

1. Open Synaptic and install the following packages:
• bluez-utils
• bluez-passkey-gnome
• gnome-bluetooth
• bluez-pin*

2. Turn your phone's BT connection and set its visibility to 'Show to all' or equivalent.

3. Open a terminal and type:

```
hcitool scan
```

You should see something like: 

```
Scanning ...
00:0E:07:37:7C:BD 6230i

```
(Your device identification will be different)

4. Open /etc/bluetooth/hcid.conf in a text editor and set:
autoinit yes
security auto
pairing multi
passkey whatever-you-want

5. Press ALT+F2 and run the 

```
bluetooth-applet
```

....

Open a terminal:

8.  sudo modprobe bnep



I'm connecting my WM6 8525 to my IBM R40 with Feisty. I can complete all through number 4, then run I try to run "bluetooth-applet" I get the error "Could not open location file:///bluetooth-applet, The location or file could not be found".

Just in case the applet actually did start, I try point 8 and get error "FATAL: Module bnep0 not found."

Any insight please? Thank you.

---

### Post by KozzioU on 2007-07-20
When executing:
```
sudo ifconfig bnep0
```I get this error:
```
bnep0: error fetching interface information: Device not found
```

I'm lost here :(

Edit: I'm using Feisty.

Edit2: I checked the syslog and found this after trying to connect via pand:
```
Jul 20 13:30:35 Filip pand[8594]: Connecting to 00:12:D2:AC:F7:14
Jul 20 13:30:35 Filip NetworkManager: <debug info>^I[1184931035.062425] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_2001_f111_noserial_if0_bluetooth_hci_bluetooth_hci'). 
Jul 20 13:30:37 Filip pand[8594]: Connect to 00:12:D2:AC:F7:14 failed. Connection refused(111)
Jul 20 13:30:39 Filip NetworkManager: <debug info>^I[1184931039.982787] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_2001_f111_noserial_if0_bluetooth_hci_bluetooth_hci'). 
```
Seems that this is the problem... although when I initiated bluetooth pairing from the WM5 device it went just fine.

---

### Post by GoodPanos on 2007-08-31
Thank you dsanders79  that worked for me =D>.  How did you find that out?

Anyways for those of you who are wondering, this is the set up I have:
[LIST]
[*]Dell Latitude D420
[*]Internal Bluetooth Dell 350 Device
[*]T-Mobile Dash (HTC S620)
[*]T-Mobile USA Data Plan
[/LIST]
...and to summarize this is what I did
Go through steps 1 to 8 as bdogg64 has outlined (second post) and then...
9.  sudo pand --role PANU --connect <your device ID (MAC address)>
10. sudo dhclient bnep0

You are done!

I also put this in a script as outlined by bdogg64 but I have to run the script twice in order to make the connection.  No big deal at least I get connected.

---

### Post by alex_mayorga on 2007-10-13
Guys,

Any chance you know how to go the other way around, so the laptop provides connectivity to the PDA so I can browse in the PDA using the laptop ethernet via bluetoot.

Something like:
Internet==>laptop==>bluetooth==>PDA

Hope I made sense.

Thanks in advance.

---

### Post by one_ro on 2007-10-31
Joining the happy crowd :D

Kubuntu Gutsy on HP 8710w
with
HTC P3600 WM5

Thanks guys!
Is there a similar HOW-TO for Wi-Fi?
Cheers,
Adrian

---

### Post by antoniuk on 2007-12-08
I am so happy right now!

I did a fresh install of gutsy and all I had to do here was create a bash script to run pand --connect <MAC> then I simply selected the connection in the nm-applet once i enabled internet sharing on my phone. Works great and I am in the love part of my love hate relationship with Ubuntu 

Here is what I have:

Dell Inspiron 8600
HTC TYTN II Windows Mobile 6
Dell Truemobile 300 built in wireless
not enough sense to quit

Now if only hell froze over and they made a linux itunes...

---

### Post by MTZeon on 2007-12-22
> **alex_mayorga said:**
> Guys,

Any chance you know how to go the other way around, so the laptop provides connectivity to the PDA so I can browse in the PDA using the laptop ethernet via bluetoot.

Something like:
Internet==>laptop==>bluetooth==>PDA

Hope I made sense.

Thanks in advance.
I would like to know this too :)

---

### Post by jermch on 2008-01-08
The howto you provided was extremely helpful...Thanks!  
The only issues I had were:

Needed to wait a bit before running:

$ sudo ifconfig bnep0
$ sudo ifup bnep0

- Maybe a timing thing.

Also, needed to add a step in order to obtain IP Address, Default Gateway, and Name Server via DHCP
$ sudo dhclient bnep0

Thanks again

Sony Vaio VGN-SZ-360P/C running Ubuntu 7.10 (Gutsy Gibbon)(dual boot with XP Pro) paired with a Cingular 8525 originally with Windows Mobile 5 (WM5) upgraded to WM6 that does not have Dial Up Networking (DUN) available at this time.  This  was the compelling reason to get a connection working via Internet Connection Sharing (ICS).

---

### Post by tetsuo-shima on 2008-01-16
I have been trying make this connection occasionally for a few months to no avail. I'd be grateful for anyone's assistance in doing this. I have tried a few different threads regarding this issue and have found bdogg64's post to offer the best results thus far. 

The instructions generally work for me. My phone and my computer are connecting. However, I cannot get IP addresses when I type "sudo ifconfig bnep0" (Step 10). I typically get something like this:

bnep0     Link encap:Ethernet  HWaddr 00:18:F8:89:95:96  
          inet6 addr: fe80::218:f8ff:fe89:9596/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:472 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:79642 (77.7 KB)  TX bytes:69906 (68.2 KB)


Also, when I enter "sudo ifup bnep0", I get the something to the effect of "Ignoring interface bnep0=bnep0" or "ifup: interface bnep0 already configured".

I've tried "sudo dhclient bnep0". I get an ongoing scroll in my terminal like this:

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/bnep0/00:18:f8:89:95:96
Sending on   LPF/bnep0/00:18:f8:89:95:96
Sending on   Socket/fallback
DHCPDISCOVER on bnep0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.0.1
DHCPREQUEST on bnep0 to 255.255.255.255 port 67
DHCPNAK from 192.168.0.1

The last four lines continue to repeat until I disconnect via the phone (if someone knows the script to do it via the terminal, please share).


Specs:
Dell Inspiron 1000
HTC TyTn/Hermes/8525 with WM5
Ubuntu 7.10
Linksys Bluetooth adapter USBBT100

Any help is appreciated. Thank you.

---

### Post by luke-windsor on 2008-03-01
This worked first time with Gutsy and a Belkin dongle for me. Had the same phone...

Thanks!

Luke




> **bdogg64 said:**
> I managed to get my internet over bluetooth, with wm5 and internet sharing. Here is what I did. I'm using t-mobile internet with a T-Mobile MDA that has internet sharing.  

Part of this guide is from [http://news.softpedia.com/news/Connect-to-the-Internet-from-Anywhere-Using-a-GPRS-Connection-50670.shtml](http://news.softpedia.com/news/Connect-to-the-Internet-from-Anywhere-Using-a-GPRS-Connection-50670.shtml)

If your laptop has an incorporated bluetooth adaptor and so does your phone, you could try the following to connect your computer to the Internet through the phone's GPRS connection:

1. Open Synaptic and install the following packages:
• bluez-utils
• bluez-passkey-gnome
• gnome-bluetooth
• bluez-pin*

2. Turn your phone's BT connection and set its visibility to 'Show to all' or equivalent.

3. Open a terminal and type:

```
hcitool scan
```

You should see something like: 

```
Scanning ...
00:0E:07:37:7C:BD 6230i

```
(Your device identification will be different)

4. Open /etc/bluetooth/hcid.conf in a text editor and set:
autoinit yes
security auto
pairing multi
passkey whatever-you-want

5. Press ALT+F2 and run the 

```
bluetooth-applet
```

6.  On your mobile phone, go to bluetooth settings, search for a new device and add your computer and pair it using the passkey you set up before

7.  On your mobile phone to Start->Programs->Internet Sharing, choose Bluetooth PAN, and your NetworkConnection (Mine is T-Mobile GRPS/EDGE), and choose Connect

Open a terminal:

8.  sudo modprobe bnep

9.  sudo pand --connect 00:0E:07:37:7C:BD

10.  sudo ifconfig bnep0

11.  sudo ifup bnep0

It should assign you an IP address automatically. And thats it!

I'm actually writing this guide using my internet over bluetooth, so I know it works for sure!

I hope this helps

---

### Post by tagabukid on 2008-04-22
thanks!

i finally got ubuntu to connect through bluetooth and my sony-ericsson k610i! i'm so happy! thank you very much! it wasn't easy, innumerable how-to's and finally this! you guys (and gals) really rock! i'm a real believer now! woohoo! :) :guitar:

---

### Post by alex_mayorga on 2008-05-08
> **MTZeon said:**
> I would like to know this too :)
Did you have any success on figuring it out? Shall we start a new thread for it?

---

