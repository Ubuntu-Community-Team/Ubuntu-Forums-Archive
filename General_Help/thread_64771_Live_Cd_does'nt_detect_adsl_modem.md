---
title: "Live Cd does'nt detect adsl modem"
date: 2005-09-12
forum: General Help
---

### Post by tabascal on 2005-09-12
I am an FC4 user. I just tried the Ubuntu 5.04 live Cd and was impressed by the way it detected the Wifi card on my Centrino laptop.

But it could not detect the Adsl modem (Model :  UT-300R2 from UTSTAR) connected on my wired ethernet port.

I tried "pppoeconf" without any effect.

Please help.

---

### Post by Bruce3000 on 2005-09-12
[QUOTE=tabascal]I am an FC4 user. I just tried the Ubuntu 5.04 live Cd and was impressed by the way it detected the Wifi card on my Centrino laptop.

But it could not detect the Adsl modem (Model :  UT-300R2 from UTSTAR) connected on my wired ethernet port.

I tried "pppoeconf" without any effect.

Please help.[/QUOTE]
 Hmmmm... ADSL issues. I'm not familiar with your model of modem. I'm used of routers that using DHCP, assign an address to your lan card. Afterward you configure the router/modem via a brwoser by typing in the IP address of the router. There is usually a port forwarding section in the browser interface as well...

If your modem is like this, then basically it is detected as a computer/gateway on your LAN, not as a piece of hardware as such. Once you have it configured via the browser interface, then you use pppoe to connect to the net...

pppoe isn't for detecting modems as such...

Hope this helps!

---

### Post by Bruce3000 on 2005-09-12
Ohhh... BTW... I was thinking of the instance of a Ubuntu installation, not LiveCD. In principal I think it may be the same issue - DHCP config of your LAN card.

May have to install DHCP-client!

---

### Post by tabascal on 2005-09-12
The ethernet port detects the DHCP settings from the Modem and gets an Ip addr.

In Fedora 4 I used "adsl-setup" and it used to configure the Adsl Modem/Router.

Is there anything equivalent in Ubuntu?

---

### Post by Bruce3000 on 2005-09-12
[QUOTE=tabascal]The ethernet port detects the DHCP settings from the Modem and gets an Ip addr.

In Fedora 4 I used "adsl-setup" and it used to configure the Adsl Modem/Router.

Is there anything equivalent in Ubuntu?[/QUOTE]
 Hmmm... now you have me relatively stumped... it's just the modem config... once that's done pppoe should be happy... but that's not going to help you is it... okay...

My first suggestion is browsing to [http://192.168.1.1](http://192.168.1.1) with your modem on, just to make sure there is no browser based config... with DHCP working, you should see if it is there or not... if there is this option, username is admin, password should be utstar... unless an ISP has fiddled with it.

As far as I can suggest ATM (and I have synaptic running, and I'm on AMD64 - so I can't comment on actual availability 4 u) is globespan-adsl (or eciadsl). Which is kind of a generic ADSL driver... [http://eciadsl.flashtux.org/](http://eciadsl.flashtux.org/) - however it's all in french et Je ne pas comprehende Francais.

Hope I haven't led you up the garden path... why do ADSL modems have to be such a bugger

---

### Post by chinarut on 2005-09-13
Just ran the live CD for the first time just now and after not finding a "adsl-*" scripts it took awhile to figure out that 'pppoeconfig' is the one that did the trick but it did work the first time.

For the record:

While fiddling around trying to figure out how to setup my modem, I did happen to go to System->Administration->Network Settings then changed

Ethernet Settings->Properties->The device is configured->Configuration

to DHCP.

I don't know if this is or is not necessary given I haven't had to reboot yet :)

If this is going to be "Linux for human beings" - configuring an ADSL should be *way* easier like it is in KNOPPIX - it was hard to find documentation as to how to setup my network IMHO and I consider myself a UN*X geek  :roll: 

chinarut

---

### Post by Bruce3000 on 2005-09-13
Such is the way of community based software - find something that can be improved upon, comment and hope for the best. Beats complaining to Microsoft about where Windoze could be better!

---

### Post by tabascal on 2005-09-14
Well you are right.

The ADSL has a browser based config with username "admin" and password "utstar"

But I never had to touch the adsl configuration in Fedora 4. 

The "adsl-setup" script used to do the trick.

I do not know how to do it in Ubuntu.

I have one more query, perhaps digress a bit.

What is the default root password?

How do I see my windows Partitions in my HDD when I run the Live Cd on my Laptop?

---

### Post by drogoh on 2005-09-14
> **tabascal]

What is the default root password?
[/QUOTE]

There is no default root password said:**
> How do I see my windows Partitions in my HDD when I run the Live Cd on my Laptop?

Depends on two things: 1) the file system you used for Windows and 2) kernel support for said file system.  You would either use -t ntfs or -t vfat in your mount command depending on 1 (if you don't have kernel support (which most kernels have vfat but not NTFS support) then you're SOL).  Since the mount command is extensively discussed across the globe, Google will help you find the syntax if you don't know it.

---

### Post by Efialtis on 2005-09-17
Have you activated your ethernet card from the System-->Administration-->Networking menu? Go for DHCP and then run pppoeconf from a command prompt. Worked for me and i'm currently writing from a 5,10 Live CD

---

### Post by Zyphrexi on 2005-09-18
I've been having trouble with my card as well, however mine is wireless. I'm pretty new to using dsl, so it might just be my inexperience with dsl/gnome/ubuntu. My query however is that my card is not configured, and it sounds like it is automatically configured? I know it's based on the atheros chipset, and there are like 3 ath_whatever modules loaded. but when i check out the networks tab, it's all nonsense. I don't know how to explain my issue, i apologize for that.

---

