---
title: "Nice but!"
date: 2005-03-31
forum: General Help
---

### Post by Beardy on 2005-03-31
Nice looking distro(Kubuntu), but DHCP and automounting not working on all three machines in my network. All different specs so probably not a hardware problem unless it's the switch and/or router. Not a problem, but would be nice not to do all that typng in. One machine has 4 partitions so a pain in the butt. Just something you expect to work on a live CD.

Real surprise was Synce-Kde working fine, with rapip, sychronising with AvantGo and KCeMirror running perfectly. Only thing missing is internet connection on the PDA through Synce-Kde but I'm sure I can live without that. Might have to RTFM, I 'm useless at doing that. In one eye and out the other. 

I'm hoping to try it out with the  Mac version. I'll let you know how it goes, if it goes at all.

---

### Post by kiddo on 2005-03-31
Just so you know, these work perfectly under the normal Ubuntu (gnome). Don't know if they work or not in Kubuntu, but I have KDE and XCFE installed, there seems to be no problem...

---

### Post by Beardy on 2005-03-31
I've tried Gnoppix  hoary_0.9.99b1-i386 and exactly the same problems with DHCP and automount but not tried Ubuntu but can't see there would be any difference. Feel free to put me right.  

Maybe the router's not IPv6 compatible. Would that make a difference? I havn't a clue.

---

### Post by alpa on 2006-06-06
I am using Kubuntu 6.06 from 2 weeks.
I was using Mandriva2006 before my new kubuntu.
I like it but I have problem with connection with my PDA.
I was using synce-kde with Mandriva2006 and it was working perfectly.
Today I installed synce-kde using this command:

*sudo apt-get install synce-kde synce-dccm librapi2-tools synce-multisync-plugin librra0-tools kcemirror*

and

*apt-get install synce-serial*

After I tried put my PDA on the cradle and I see that it is trying to connect automatically, without manual command like in Mandriva (i.e. first 'dccm' and after 'synce-serial-start').
But after 2 or 3 second connection is lost !
I tried to use manual command like ' synce-serial-start' but nothing happened.
I tried to check config using 'synce-serial-config ttyUSB0' and I received this prompt:

[I]alpa@alpa-desktop:~$ sudo synce-serial-config ttyUSB0

You can now run synce-serial-start to start a serial connection.[/I]

So I tried again connection with RAKI but nothing is running.
What is wrong ? With Mandriva it was a second to setup all things...
It is a problem of firewall ? I have no idea how to setup the firewall with Kubuntu.
It is a wrong configuration of my installation ?
Please help me.

Alpa
:???:

---

### Post by Lord Illidan on 2006-06-06
You have a usb modem?

---

### Post by alpa on 2006-06-17
[QUOTE=Lord Illidan]You have a usb modem?[/QUOTE]

No I have no usb modem, only a scanner and printer all-in-one Epson DX3800
Modem is serial, connected on Com1, while access to internet is done using a eth0 modem.

I am in troubles. I can not understand why Synce-kde is so hard to make running with Kubuntu 6.06 LTS.

Anybody is using Synce on Kubuntu 6.06 ?
Anybody else found same problems to run Synce on Kubuntu.
Any new idea will be very appreciated.

Alpa

---

### Post by alpa on 2006-06-18
[QUOTE=alpa]No I have no usb modem, only a scanner and printer all-in-one Epson DX3800
Modem is serial, connected on Com1, while access to internet is done using a eth0 modem.

I am in troubles. I can not understand why Synce-kde is so hard to make running with Kubuntu 6.06 LTS.

Anybody is using Synce on Kubuntu 6.06 ?
Anybody else found same problems to run Synce on Kubuntu.
Any new idea will be very appreciated.

PROBLEM solved !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

I found that file called '60-ipaq.rules' wasn't present ! It must be located at '/etc/udev/rules.d'.
I installed from ubuntu repository but this file didn't come !
Here what is written inside :

# udev rules file for SynCE
BUS!="usb", ACTION!="add", KERNEL!="ttyUSB*", GOTO="synce_rules_end"
# Establish the connection
RUN+="/usr/bin/synce-serial-start"
LABEL="synce_rules_end"

I have a PDA Asus A716 and this file works perfectly !

I spent 2 weeks to solve , but now I am happy like nobody else !

Alpa
:D :D :D :D :D

---

