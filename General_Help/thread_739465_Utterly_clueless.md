---
title: "Utterly clueless"
date: 2008-03-29
forum: General Help
---

### Post by Wingnutt on 2008-03-29
I need some basic help.

Just installed Ubuntu and of course, wireless doesent work.

I dont understand how to move around in terminal.

I have a folder on my desktop I need to get into to do a make/make install on..

but have no idea how to get there via terminal.

directions say I need to "CD to it"

which im guessing is like windows... 

BUT


I dont know WHERE I am (says myname@myname-laptop)

if I type DIR.. all I get is Examples MUSIC PICTURES.. etc etce...
or how to move from DIR to DIR in the terminal..

where can I find some good BASIC help?

---

### Post by Wingnutt on 2008-03-29
> **|{urse said:**
> [www.google.com](www.google.com)

google? no really?

how do you think I found this place.

---

### Post by bapoumba on 2008-03-29
cd /<full_path_where_you_want_to_go>
without <>.
~ is a shortcut for your user /home.
Example:
```
isabella@yeti:~ $ cd /etc
isabella@yeti:/etc $ 
isabella@yeti:/etc $ cd /home/isabella/
isabella@yeti:~ $
```

yourname: your user login
youruser_laptop: your host

---

### Post by willnut on 2008-03-29
if you type "pwd" then [Return] it will give you the directory you are currently in (present working directory).

ls -la

is also handy all it lists all files including hidden/system files in the current directory.

Might be useful to get a basic Linux book. I dont know much and it saves me a lot of time.

---

### Post by HereInOz on 2008-03-29
if you searched on google for something like "linux basic commands" you may get something (like [http://www.comptechdoc.org/os/linux/usersguide/linux_ugbasics.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugbasics.html)).  

The Linux equivalent of dir is ls, copy is cp, cd\ becomes cd /, cd.. becomes cd .. (note the spaces).  So a "cd" would be something like "cd /home/username/music"  or cd /usr/share/firefox/plugins" or something like that.

You really need to get up to speed with the basic command line stuff to do what you want to do, or you will just be tearing your hair out for no reason. 

All quote marks are for illustration only.

---

### Post by Wingnutt on 2008-03-29
Ok, ive got the terminal figured out..

im pretty sure my wireless will never work though.

this is the most annoying piece of software ive ever used.

---

### Post by HereInOz on 2008-03-29
What chip is on your wireless card, or are you using a USB type of thing?

---

### Post by Wingnutt on 2008-03-29
> **HereInOz said:**
> What chip is on your wireless card, or are you using a USB type of thing?

Im using a broadcom card (integrated in laptop)

I click the network manager, no wireless networks show up... despited there being at least  12 in range

---

### Post by The Cog on 2008-03-29
The first step is to run the command 
```
lspci
```
in the terminal, and post the results here. This will let people konw which broadcom chipset you are using. Also the output of 
```
cat /etc/issue
```
which tells us which version of Ubuntu you are using.

---

### Post by ugm6hr on 2008-03-29
Indeed - lspci gives useful info.

Another useful one is (capital C):
```
lshw -C network
```

Broadcom cards generally work if you enable the "Restricted Drivers".

Where did you get the impression you have to make / make install to get it to work?

Unfortunately, it is difficult to help if we have to guess what you are trying to do (or at least guess *how* you are trying to do something).  I suspect that you were initially asking the wrong questions...

---

### Post by Wingnutt on 2008-03-29
> **The Cog said:**
> The first step is to run the command 
```
lspci
```
in the terminal, and post the results here. This will let people konw which broadcom chipset you are using. Also the output of 


jason@jason-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

[/quote]
```
cat /etc/issue
```
which tells us which version of Ubuntu you are using.[/QUOTE]

7.10

---

### Post by Wingnutt on 2008-03-29
> **ugm6hr said:**
> Indeed - lspci gives useful info.

Another useful one is (capital C):
```
lshw -C network
```

Broadcom cards generally work if you enable the "Restricted Drivers".

Where did you get the impression you have to make / make install to get it to work?

Unfortunately, it is difficult to help if we have to guess what you are trying to do (or at least guess *how* you are trying to do something).  I suspect that you were initially asking the wrong questions...

well i though I needed madwifi which is what i was trying to install, but from what i understand I SHOULD NOT need it.

---

### Post by Wingnutt on 2008-03-29
I go into SYS ---> Admin---> Network

select "wireless connection"

properties

deselect roaming

click the dropdown arrow for network name... nothing..

despite there being 12 networks within range..

sooo

I go into terminal

type

iwlist eth0 scan

"no scan results"

---

### Post by Wingnutt on 2008-03-29
Well i just tried something, went off the directions found HERE
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

considering its the same version of Ubuntu and same card im using, that it would work..

spent 45 min doing everything as directed.

after final reboot, no wireless card even found on my system..

reinstalling ubunto now... AGAIN:(

---

### Post by The Cog on 2008-03-30
It's a bummer when a hardware manufacturer refuses to produce Linux drivers.

I don't have a broadcom, I have intel wifi in my laptop, which Just Works. Good for intel - my next lappy will likely be intel throughout. Obviously when you already own a laptop, you can't just swap the wifi out.

I found this though, by googling for "ubuntu bcm94311". I cab't vouch for it of course. I do notice that they blacklist the normal broadcom driver that comes with Ubuntu. I've seen that a lot, so I guess the default Ubuntu drivers are not all they could be.

---

### Post by strabes on 2008-03-30
> **Wingnutt said:**
> Im using a broadcom card (integrated in laptop)

There's your first problem. It is not ubuntu's fault that this card does not work. It is broadcom's fault for not providing linux drivers. Everything intel makes works perfectly in linux simply because they provide proper drivers. I will **never** purchase anything made by broadcom or ATI for the rest of my life, and I encourage you and anyone else reading this thread to do the same.

---

### Post by ugm6hr on 2008-03-30
> **The Cog said:**
>  Obviously when you already own a laptop, you can't just swap the wifi out.

Actually, you can.

Intel and Atheros mini-PCI cards are available on ebay for £10-15 (in UK).

As long as you don't have a Compaq/HP laptop (which appear to have BIOS restrictions on compatible hardware), that will work very well.  Some of the newer budget laptops also seem to have "internal USB" wifi cards, which are troublesome too.

Anyway, it looks like the fw-cutter driver doesn't support your card.

Not sure why the link you have given didn't work.  But perhaps this is worth trying...

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

In summary (for ndiswrapper):
```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```
Install *ndisgtk* in Synaptic Package Manager
Use "Windows Wireless Drivers" to select the bcmwl5.inf driver (ensuring the associated .sys file is also present)

Then..
```
sudo ndiswrapper -m
```
```
gksudo gedit /etc/modules
```
And add the word *ndiswrapper* to the bottom of the file.

Then keep your fingers crossed ;)

---

### Post by diablo75 on 2008-03-30
If you've just done a fresh install of Ubuntu with NO internet connection, I recommend you hook that thing up to a hard line and download as many updates as you can.  I had a broadcom card that didn't work until I installed all my updates.

Tip:  If this is on a laptop, make sure you're bios settings allow for the card to be completely controlled by the operating system, instead of the BIOS or any special switches/function-keys on the keyboard.  The same laptop mentioned above "stopped working" because he accidentally hit FN-F4.

---

### Post by Wingnutt on 2008-03-30
just for chuckles in installed kubuntu, whill hooked to the internet, let it install all updates etc etc..

im using restricted drivers.. but now the card can see wireless networks.. but not connect... and if i try to change anything in the manual settings.,.. it goes bonkers, gets stuck on auto/dhcp.. with a 255.255.0.0 subnet, some wierd IP and cannot be changed back..  so that a fail.

---

