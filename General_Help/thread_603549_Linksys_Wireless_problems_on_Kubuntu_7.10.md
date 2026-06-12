---
title: "Linksys Wireless problems on Kubuntu 7.10"
date: 2007-11-05
forum: General Help
---

### Post by lord.toan on 2007-11-05
I installed Kubuntu 7.10 a few days ago, and I've been having trouble with the wireless connection.

I'm using a Linksys WUSB11 card.  I'm connected to the ethernet wire right now because I can't get it to connect to my wireless network, but I would prefer to get the wireless working because right now the wire is running all the way from the modem downstairs to my computer upstairs, and that's a bit of a pain in the ***.

I have ndiswrapper (of course)

When I run ndiswrapper -l in the terminal I get:

> lsbcmnds : invalid driver!

iwconfig gets me:

> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"belkin54g"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:50:54:2C:51
          Bit Rate:11 Mb/s   Tx-Power=15 dBm
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B
          Power Management:off
          Link Quality=69/100  Signal level=69/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have no idea how to fix this... If someone could please help me out, I'd appreciate it.  I'm still searching forum sites for help with this, and I'm on the ethernet, so it's not URGENT or anything, but I would like to get this working.  Thanks in advance.

---

### Post by Crafty Kisses on 2007-11-06
> **lord.toan said:**
> I installed Kubuntu 7.10 a few days ago, and I've been having trouble with the wireless connection.

I'm using a Linksys WUSB11 card.  I'm connected to the ethernet wire right now because I can't get it to connect to my wireless network, but I would prefer to get the wireless working because right now the wire is running all the way from the modem downstairs to my computer upstairs, and that's a bit of a pain in the ***.

I have ndiswrapper (of course)

When I run ndiswrapper -l in the terminal I get:



iwconfig gets me:


I have no idea how to fix this... If someone could please help me out, I'd appreciate it.  I'm still searching forum sites for help with this, and I'm on the ethernet, so it's not URGENT or anything, but I would like to get this working.  Thanks in advance.

Sounds to me like you might want to try a NDISwrapper.

---

### Post by wieman01 on 2007-11-06
What file did you deploy through "ndiswrapper" and what's the exact command?

---

### Post by lord.toan on 2007-11-06
code: I have NDISwrapper... It says the sys file is invalid...

wie: i have no idea what any of that means. -noob- T_T

---

### Post by wieman01 on 2007-11-06
> **lord.toan said:**
> code: I have NDISwrapper... It says the sys file is invalid...

wie: i have no idea what any of that means. -noob- T_T
You normally don't deploy the .sys but the .inf file. 

As you plan to use "ndiswrapper" anyway, why don't you follow the instructions in my howto (see signature... Ralink) which should be pretty much the same for your card. I will try to guide you through it, how about that?

Please remove your current driver file by typing:
> sudo ndiswrapper -e <your_file>

---

### Post by lord.toan on 2007-11-06
Alright, I removed the drivers.  I suppose I should redownload the drivers.

Which ones exactly do I need for a WUSB11 2.8?

---

### Post by lord.toan on 2007-11-06
I'm reading through your guide right now, and trying to do stuff.

My computer gives me problems any time i try to install something off the internet, and since it's hooked up to the modem itself, it screws up the modem's ability to load web pages, and I can't figure how to fix that... -_-

---

### Post by wieman01 on 2007-11-06
> **lord.toan said:**
> I'm reading through your guide right now, and trying to do stuff.

My computer gives me problems any time i try to install something off the internet, and since it's hooked up to the modem itself, it screws up the modem's ability to load web pages, and I can't figure how to fix that... -_-
Can't you install ndiswrapper off the CD?

---

### Post by wieman01 on 2007-11-06
> **lord.toan said:**
> Alright, I removed the drivers.  I suppose I should redownload the drivers.

Which ones exactly do I need for a WUSB11 2.8?
I don't which drivers you need... But Linksys' web site should be able to throw some light on the issue.

---

### Post by lord.toan on 2007-11-06
I've got ndiswrapper already.  I had to install gedit according to the guide, and when i tried to install it with apt-get install command, my internet decided it wasn't gonna load sites anymore, so i had to go downstairs to have my stepdad reset the modem, which of course made my mom start bitching at me.  I dunno why my modem does that...

I've got the linksys WUSB11 2.8 files, the only inf file i can find is netusb.inf, and when i run sudo ndiswrapper -i netusb.inf, i get:

> installing netusb ...
couldn't open netusb.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 181.


So I'm assuming either that's not the right file, or something's wrong with linux.  Hopefully, It's just the file...

---

### Post by lord.toan on 2007-11-06
Never mind, it was case sensitive. >_<

Continuing the guide -reads on-

---

### Post by wieman01 on 2007-11-06
> **lord.toan said:**
> I've got ndiswrapper already.  I had to install gedit according to the guide, and when i tried to install it with apt-get install command, my internet decided it wasn't gonna load sites anymore, so i had to go downstairs to have my stepdad reset the modem, which of course made my mom start bitching at me.  I dunno why my modem does that...

I've got the linksys WUSB11 2.8 files, the only inf file i can find is netusb.inf, and when i run sudo ndiswrapper -i netusb.inf, i get:



So I'm assuming either that's not the right file, or something's wrong with linux.  Hopefully, It's just the file...
When you install the .inf file, are there any other files in the same folder? Which ones?

---

### Post by wieman01 on 2007-11-06
> **lord.toan said:**
> Never mind, it was case sensitive. >_<

Continuing the guide -reads on-
Alright, mate. :-)

---

### Post by lord.toan on 2007-11-06
Alright I can't get KNetworkManager to even pick up that I have a wireless plugged in anymore...

As opposed to when I first got on here it said I had a wireless network but refused to connect...

This is probably a much simpler problem than the last one... 

I'm gonna try to figure it out.  Any pointers would be helpful.

---

### Post by wieman01 on 2007-11-06
What does this yield:
> ndsiwrapper -l
Please restart the computer and do a scan:
> sudo iwlist scan

---

### Post by lord.toan on 2007-11-06
iwlist scan:

> auto wlan0
iface wlan0 inet dhcp

ndiswrapper -l isn't working for some reason... It just stops up the terminal...

---

### Post by wieman01 on 2007-11-06
Does your PC freeze? If so, your version of ndiswrapper is faulty. You would need to compile it from source...

Please do another scan, the output is not right (that's more part of your "interfaces" file I suppose):
> sudo iwlist scan

---

### Post by lord.toan on 2007-11-06
OH, I didn't copy the info right LOL sorry! >_<

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.




It's not freezing up my pc, the terminal just doesn't do anything when i type it.  I have to restart the terminal or open up a new shell in order to do anything.

---

### Post by wieman01 on 2007-11-06
> **lord.toan said:**
> It's not freezing up my pc, the terminal just doesn't do anything when i type it.  I have to restart the terminal or open up a new shell in order to do anything.
Ok, you might have to restart the PC.

Please also post:
> sudo gedit /etc/network/interfaces

---

### Post by lord.toan on 2007-11-06
> auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface wlan0 inet dhcp

auto wlan0

I'm not picking up wlan0 in my knetworkmanager...

---

### Post by wieman01 on 2007-11-06
> **lord.toan said:**
> I'm not picking up wlan0 in my knetworkmanager...
Then comment these lines for a moment and restart the PC:
> auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#auto wlan0
#iface wlan0 inet dhcp
This sometimes helps. NM actually does not need them anyway... at least not always.

---

### Post by lord.toan on 2007-11-06
Wow.  It works now.  Thanks! ^__^

Now whenever my computer does it's stupid idea of killing my internet, I'll only have to unplug my wireless and plug it back in! >:D

A MAJOR help.  Thank you very much. ^_^

---

### Post by wieman01 on 2007-11-06
> **lord.toan said:**
> Wow.  It works now.  Thanks! ^__^

Now whenever my computer does it's stupid idea of killing my internet, I'll only have to unplug my wireless and plug it back in! >:D

A MAJOR help.  Thank you very much. ^_^
No problem. Did commenting the 2 lines solve the problem? If yes, I have to update the guide, mate. Would appreciate if you let me know.

---

### Post by lord.toan on 2007-11-06
I commented the last two lines and restarted, and it worked.  So unless whatever was making ndiswrapper -l not work did that, then yeah, the comments helped.

also:

ndiswrapper -l:

> netusb : driver installed
        device (1915:2233) present (alternate driver: at76_usb)


---

### Post by wieman01 on 2007-11-06
> **lord.toan said:**
> I commented the last two lines and restarted, and it worked.  So unless whatever was making ndiswrapper -l not work did that, then yeah, the comments helped.

also:

ndiswrapper -l:
Excellent. Thank you & have fun with your adapter!

---

