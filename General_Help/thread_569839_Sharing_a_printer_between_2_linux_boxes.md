---
title: "Sharing a printer between 2 linux boxes"
date: 2007-10-07
forum: General Help
---

### Post by BobvanderPoel on 2007-10-07
This really has to be such an easy thing to do, but for my life I can't get it to work! I have a HP printer connected to my desktop box via a usb port. Works just fine.

Now, I'm trying to connect my laptop to this printer. Yeah, easy :)

Okay, I have CUPS running. First thing I did was to go to the "System Settings" (the kde thing) and enable the Print Server "share printers on network" check box. The printer still works from the desktop, so that's a good sign.

Now, to the laptop. I have a little network running with a Dlink WBR-1310. Mostly the router is using defaults. My laptop manages to connect to the router without problems. 

Now, on the laptop I go to the system configuration and select Add Printer Class and get the KDE printer dialog. My first problem is that I'm not sure which backend to select, but I guess at Remote CUPS server. Now, I need to select "Anonymous" or "Normal". I select "Anon".

Ahh, more info need. It wants to know the HOST. I really have no idea? So I start to GUESS. The desktop is "Mellowood" so I try that. Nope. Ummm, mellowood-server? Nope.

Now, I try some IP addresses. Hmmm, the router is a 192.168.0.* so I try some variants of that ... nothing.

Next I go to my good friends here :) I really am lost.

Thanks.

---

### Post by jimrz on 2007-10-07
> **BobvanderPoel said:**
> This really has to be such an easy thing to do, but for my life I can't get it to work! I have a HP printer connected to my desktop box via a usb port. Works just fine.

Now, I'm trying to connect my laptop to this printer. Yeah, easy :)

Okay, I have CUPS running. First thing I did was to go to the "System Settings" (the kde thing) and enable the Print Server "share printers on network" check box. The printer still works from the desktop, so that's a good sign.

Now, to the laptop. I have a little network running with a Dlink WBR-1310. Mostly the router is using defaults. My laptop manages to connect to the router without problems. 

Now, on the laptop I go to the system configuration and select Add Printer Class and get the KDE printer dialog. My first problem is that I'm not sure which backend to select, but I guess at Remote CUPS server. Now, I need to select "Anonymous" or "Normal". I select "Anon".

Ahh, more info need. It wants to know the HOST. I really have no idea? So I start to GUESS. The desktop is "Mellowood" so I try that. Nope. Ummm, mellowood-server? Nope.

Now, I try some IP addresses. Hmmm, the router is a 192.168.0.* so I try some variants of that ... nothing.

Next I go to my good friends here :) I really am lost.

Thanks.

try 
```
ipp://<ip off your desktop>/printers/<name of your printer>
```
should get you there

---

### Post by BobvanderPoel on 2007-10-07
Thanks, and okay. But this is very odd. I just came back to the computer and read the reply. I think I figured out the ipp and went to the laptop to configure. But, magically, kdeprinter was already configured for a printer ... and it has the correct ipp, etc. I have no idea where it came from ... but I tried a test page and it works.

So, now the laptop is set with a default printer of hp2550 at ipp://192.168.0.100:631/printers/hp2550

Is this going to screw up if I boot my main box with a different ip address? I think it will aways be 192.168.0.100, but the router is doing dhcp. Just wondering about this.

---

### Post by jimrz on 2007-10-07
> **BobvanderPoel said:**
> Thanks, and okay. But this is very odd. I just came back to the computer and read the reply. I think I figured out the ipp and went to the laptop to configure. But, magically, kdeprinter was already configured for a printer ... and it has the correct ipp, etc. I have no idea where it came from ... but I tried a test page and it works.

So, now the laptop is set with a default printer of hp2550 at ipp://192.168.0.100:631/printers/hp2550

Is this going to screw up if I boot my main box with a different ip address? I think it will aways be 192.168.0.100, but the router is doing dhcp. Just wondering about this.

A different ip would likely screw it up. My router has a place to "reserve" a specific ip for specific machines by name/mac address that I use to get "static" ip functionality for my network/printing while still using dhcp. Works very nicely, check to see if your router has a similar feature.

---

### Post by strabes on 2007-10-07
> **jimrz said:**
> try 
```
ipp://<ip off your desktop>/printers/<name of your printer>
```
should get you there

At my house I have to use http and I have to specify the port 631. I believe the line should look like this:```
http://ipofyourdesktop:631/printers/nameofyourprinter
```

To find the ip of your desktop, run "ifconfig" on your desktop box and look for the line that looks like this:[quote]inet addr: xxx.xx.xx.xxx[/code] It will almost certainly be under "eth0" or "eth1"

---

