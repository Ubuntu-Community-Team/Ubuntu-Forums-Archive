---
title: "Printer in a windows xp server"
date: 2007-12-18
forum: General Help
---

### Post by DreamerHxC on 2007-12-18
Hi:

I have a LAN with a computer with Ubuntu 7.10 and a Windows XP computer with an Epson Stylus DX5000 printer and I want to print from this computer with Ubuntu 7.10, but I cannot add the printer to ubuntu, even with samba or LPD. I have changed the workgroup in smb.conf but it's not still working. I have even used Smb4k, though it doesn't see any computer in my LAN (it just sees this computer with 0.0.0.0 IP).

Thanks in advance.

---

### Post by danwood76 on 2007-12-18
can you ping your XP PC?
if you cant even ping the XP PC then you wont be able to setup samba.

btw you can set the workgroup if you go administration > shared folders. check your settings are correct in there.

---

### Post by .nedberg on 2007-12-18
Is the printer shared on the XP computer? If t isn't Ubuntu wont see it...

---

### Post by DreamerHxC on 2007-12-18
OK, the printer is shared on the WXP computer but I cannot ping any computer in my LAN, so there must be something wrong with my LAN configuration in linux, but I cannot find the wrong thing, because I've checked the subnet mask, the gateway and the IP and everything's correct :confused:

---

### Post by danwood76 on 2007-12-18
Obviously your IP configuration is wrong. Possibly the subnet mask is incorrect.
If you are assigning IPs by DHCP there really shouldnt be a problem  unless you havent set your linux box to correctly aquire the DHCP addressing.

---

### Post by DreamerHxC on 2007-12-18
Ok, my bad, I've just realised that I have moblock, so when I deactivated it and ping the computer, it worked :mad:, because it seems that the lists moblock retrieves from bluetack block some private adrresses, and now the thing is how to configure moblock to let me work with my LAN.
Thank you all for you help with the printer :)

---

### Post by stchman on 2007-12-18
> **DreamerHxC said:**
> Hi:

I have a LAN with a computer with Ubuntu 7.10 and a Windows XP computer with an Epson Stylus DX5000 printer and I want to print from this computer with Ubuntu 7.10, but I cannot add the printer to ubuntu, even with samba or LPD. I have changed the workgroup in smb.conf but it's not still working. I have even used Smb4k, though it doesn't see any computer in my LAN (it just sees this computer with 0.0.0.0 IP).

Thanks in advance.

I have always found it to be a PITA to print from an Ubuntu machine to a Windows XP machine.  The other way around is really very easy.

I recommend you put the printer on the Gutsy machine and share it on the network.  I have a tutorial that will allow you to do it with Feisty:

[http://www.stchman.com/share_printer.html](http://www.stchman.com/share_printer.html)

The only thing is that Gutsy allows the opening of port 631 for an individual printer while Fesity shares ALL the printers.

---

### Post by danwood76 on 2007-12-18
I have never had a problem printing to windows printers from linux, the key thing is to get the smb.conf set properly. once that is done and you can access windows shares windows printing is easy!

---

### Post by stchman on 2007-12-19
> **danwood76 said:**
> I have never had a problem printing to windows printers from linux, the key thing is to get the smb.conf set properly. once that is done and you can access windows shares windows printing is easy!

Could you provide a link for a tutorial to print on a network from an Ubuntu machine to an XP/Vista machine.

Thanks.

---

### Post by jre on 2007-12-21
> **DreamerHxC said:**
> Ok, my bad, I've just realised that I have moblock, so when I deactivated it and ping the computer, it worked :mad:, because it seems that the lists moblock retrieves from bluetack block some private adrresses, and now the thing is how to configure moblock to let me work with my LAN.
Thank you all for you help with the printer :)
Check /var/log/moblock.log to see what is blocked and whitelist the IPs in /etc/moblock/moblock.conf

greets
jre

---

