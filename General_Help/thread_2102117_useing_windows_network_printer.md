---
title: "useing windows network printer?"
date: 2013-01-06
forum: General Help
---

### Post by cabz on 2013-01-06
In my house the wifey has her two pc's  1 laptop and 1 desktop running win 7 ( poor her)
my laptop is dualbooted with win7/12.10 ubuntu. when in windows i use her laser printer wirelessly from my laptop. ( the printer is wired to her desktop) my question is how or can i use my ubuntu os to print on her printer? I cannot figure out how to see what is on the windows network and vs it cannot seem my ubuntu laptop.

P.S sorry if this is not in  the right catagory.

---

### Post by drdos2006 on 2013-01-06
If the Windows printer is shared, then you should be able to connect using Samba from your Ubuntu machine.

I have had problems with Windows 7 sharing with Ubuntu in the past and needed to install Hewlett-Packard drivers for a Canon printer to connect. See [http://blog.amoktech.com/](http://blog.amoktech.com/) for more info.

regards

---

### Post by cabz on 2013-01-06
> **drdos2006 said:**
> If the Windows printer is shared, then you should be able to connect using Samba from your Ubuntu machine.

I have had problems with Windows 7 sharing with Ubuntu in the past and needed to install Hewlett-Packard drivers for a Canon printer to connect. See [http://blog.amoktech.com/](http://blog.amoktech.com/) for more info.

regards
I can find the drivers for my printer in the cupps printer setup. I just cant find the location of the printer/host pc on my wireless network. the pc the printer is hooked to is the main pc wired to the internet through the cable modem and wireless router. is there a program that will allow me to see a map of the windows network? will samba do that?

---

### Post by drdos2006 on 2013-01-07
Yes, you can use nmap. This is the sort of command.
 nmap  -v  -sP  192.168.0.0/24
You may have to install nmap first with : sudo apt-get install nmap.

You may also have to connect your laptop with an ethernet cable to your router first, install the printer using the samba share, then try to connect wirelessly.

regards

---

### Post by jerome1232 on 2013-01-07
You should be able to click the power/cog icon in the top right of your screen, click Printers (I'm on 12.04, it may have moved in 12.10) click the small down arrow next to network printers, it may take a minute to scan the network for printers. Once the printer is found you should be able to select it and follow any onscreen instructions.

edit: You may have to select the Windows Printer via Samba option, and follow what it says. There is a browse button that allows you to browse the network for printers.

---

