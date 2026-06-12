---
title: "Printer doesn't work"
date: 2008-05-01
forum: General Help
---

### Post by Achilles124 on 2008-05-01
I have a Hewelett-Packard Deskjet 825C. Ubuntu recognizes it but produces just empty pages. What can it be?

---

### Post by DrCoolSanta on 2008-05-01
Same for me, just wouldn't print anything . . .

---

### Post by maxdamage2122 on 2008-05-01
I had this problem on gutsy and just got used to not printing from it since i searched but never found a solution.  I now have hardy and just tried again but still prints blank pages.  I would love to b able to print from my linux machine so does anybody have any solutions?

---

### Post by warp99 on 2008-05-02
Actually HP has very good support for printers in Linux with HPLIP. Are you using these drivers?

[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

You don't have to download them since they are available in the repositories:

[http://packages.ubuntu.com/hardy/hplip](http://packages.ubuntu.com/hardy/hplip)

---

### Post by maxdamage2122 on 2008-05-02
I probably should have stated that I am trying to print over a network and apparently hplip does not support that.

---

### Post by Achilles124 on 2008-05-02
I searched with the synaptic manager for hplip and look and behold it is already on my system. Now i have to find out why the printing doesn't work.

---

### Post by warp99 on 2008-05-02
> **maxdamage2122 said:**
> I probably should have stated that I am trying to print over a network and apparently hplip does not support that.

HPLIP does support ipp/jetdirect printing over a network using port 9100. Now if your printing to a stand alone print server and not to the printer directly HPLIP may not support this, but if the print server supports ipp/jetdirect, most of them support this, then you can set the printer up as a socket printer in the device section:

```
socket://<ip_address_of_server>:9100
```
and use the HPIJS drivers which are already installed in the '/usr/share/ppd/hpijs/HP' directory. If they're not installed then install them:
```
sudo apt-get install hpijs hpijs-ppds
```

---

### Post by Achilles124 on 2008-05-03
Okay, warp, found the 825c file in the /usr/share/ppd/hpijs/HP directory you have given me. What to do now. Uninstall and reinstall with the synaptic manager the Hp directory? 
Or use some "force" (i am new with Linux)?

---

### Post by warp99 on 2008-05-03
> **Achilles124 said:**
> Okay, warp, found the 825c file in the /usr/share/ppd/hpijs/HP directory you have given me. What to do now. Uninstall and reinstall with the synaptic manager the Hp directory? 
Or use some "force" (i am new with Linux)?
When you set up the printer in the gnome setup dialog choose 'other' for the driver and use that driver in that directory for your printer. If you want to use the HPLIP printer tools then you need to set up the printer up as 'hp://<location_of_printer>' with CUPS so that the HPLIP program can see the printer. The link I listed previous:

[http://hplip.sourceforge.net/](http://hplip.sourceforge.net/)

has some instructions on how to set up the printer to do this. CUPS is the Common Unix Printer System that Linux, BSD, and OSX uses to print and is already installed on your system.

---

### Post by Achilles124 on 2008-05-04
I found Hplip toolbox on my Ubunty system. I ran that and it seems that there is no ink left in my cartridges. Could be the problem.:lolflag:
Anyway, ty for answering.

Pm: run Hplip toolbox while your printer is on.

---

### Post by frenchn00b on 2008-05-04
> **Achilles124 said:**
> I have a Hewelett-Packard Deskjet 825C. Ubuntu recognizes it but produces just empty pages. What can it be?


is your driver correct?
  
try this:
```
#!/bin/sh
cd /tmp
mkdir /etc/cups
echo "here you need to go on the printer linux site and get HP-DeskJet_8250C-pnm2ppa.ppd something like, to your /etc/cups"
read dsfkjdlfjls
cp /tmp/HP-DeskJet_8250C-pnm2ppa.ppd  /etc/cups/
apt-get -f -y   install   
apt-get -f -y   install    kprinter
apt-get -f -y   install    kprinter
apt-get -f -y   install    kdeprint
apt-get -f -y   install    xmessage
apt-get -f -y   install    gnome-panel
apt-get -f -y   install    cupsys
apt-get -f -y   install     cupsys-bsd
apt-get -f -y   install     cupsys-client
apt-get -f -y   install    
apt-get -f -y   install     gnome-cups-manager
apt-get -f -y   install   
apt-get -f -y   install  kprinter
apt-get -f -y   install    kprinter
apt-get -f -y   install    xmessage
apt-get -f -y   install   gnome-panel
apt-get -f -y   install     cupsys
apt-get -f -y   install     cupsys-bsd
apt-get -f -y   install     cupsys-client
apt-get -f -y   install     foomatic-filters-ppds
apt-get -f -y   install    foomatic-rip
apt-get -f -y   install    cups-pdf
apt-get -f -y   install     pnm2ppa
apt-get -f -y   install     printconf
killall -HUP cupsd
/etc/init.d/cups restart
/etc/software/init.d/cups stop
/etc/software/init.d/cups start
/etc/init.d/cupsys stop
/etc/init.d/cupsys start
```

---

### Post by warp99 on 2008-05-05
> **Achilles124 said:**
> I found Hplip toolbox on my Ubunty system. I ran that and it seems that there is no ink left in my cartridges. Could be the problem.:lolflag:
Anyway, ty for answering.

Pm: run Hplip toolbox while your printer is on.

Yeah, I think that could be a problem. Well at least you got the correct drivers running and the HPLIP Toolbox working. Now some ink and you're ready to ... :guitar:

---

### Post by maxdamage2122 on 2008-05-05
ok so i decided to scratch the network printing for now and try to get it to at least print while directly connect through usb.  I installed the hpijs drivers, ran hp toolbox, added a new printer, used the 825c driver i just installed, and everything went smooth as usual.  I go to print a test page and it sounds as if it is printing (cartridge moves back and forth) but the page is completely blank.

---

### Post by frenchn00b on 2008-07-01
I am not so sure that HPLIP is the right solution. It happen to mess up time to time for some configs and printers. Dont know ... not easy I know   the first time ...

> ### printconf is the greatest for USB printers 
apt-get       install     printconf

---

### Post by dburnett77 on 2008-07-01
> **Achilles124 said:**
> I have a Hewelett-Packard Deskjet 825C. Ubuntu recognizes it but produces just empty pages. What can it be?

Print quality set to text in a grep filter, most likely.

Quit scanning "know it all:

---

### Post by Achilles124 on 2008-07-02
you are not gonna believe this. I have printed the test page. The way I managed to do this, is by selecting a different printer model, namely:

Brother DCP-1200 Foomatic/hl1250 (recommended)

Unbelievable, but he has printed the test page.
So, change the settings in the printer configuration.

:lolflag:

---

### Post by maxdamage2122 on 2008-08-01
> **Achilles124 said:**
> you are not gonna believe this. I have printed the test page. The way I managed to do this, is by selecting a different printer model, namely:

Brother DCP-1200 Foomatic/hl1250 (recommended)

Unbelievable, but he has printed the test page.
So, change the settings in the printer configuration.

:lolflag:

i was able to print a test page as well but the bottem and the right side of the page gets cut off.

---

### Post by hansdown on 2008-08-01
There is a link that might help. hopefully.[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_825C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_825C)

---

### Post by maxdamage2122 on 2008-08-01
Thanks for the link hansdown.  I tried the driver for the deskjet 842c(HP Deskjet 842C Foomatic/hpijs [en] (recommended)) and it seems to be working a lot better if not perfect.  I believe there are just problems with the drivers for the 845C.

---

