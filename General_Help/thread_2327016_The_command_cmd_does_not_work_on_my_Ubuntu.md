---
title: "The command cmd does not work on my Ubuntu"
date: 2016-06-07
forum: General Help
---

### Post by Gins on 2016-06-07
The command ' cmd ' does not work.
Please help me.

```
ni@Ni:~$ cmd
No command 'cmd' found, did you mean:
 Command 'mmd' from package 'mtools' (main)
 Command 'amd' from package 'am-utils' (universe)
 Command 'tcmd' from package 'tcm' (universe)
 Command 'mcd' from package 'mtools' (main)
 Command 'qcmd' from package 'renameutils' (universe)
 Command 'cmp' from package 'diffutils' (main)
 Command 'vcmd' from package 'core-network-daemon' (universe)
 Command 'icmd' from package 'renameutils' (universe)
 Command 'cm' from package 'config-manager' (universe)
 Command 'wmd' from package 'wml' (universe)
 Command 'cme' from package 'libconfig-model-perl' (universe)
 Command 'dcmd' from package 'devscripts' (main)
 Command 'jcmd' from package 'openjdk-7-jdk' (main)
cmd: command not found
ni@Ni:~$ 
```
..............................................................................................................................

I use Ubuntu 14.04.4 LTS

---

### Post by howefield on 2016-06-07
What are you trying to do ?

---

### Post by Gins on 2016-06-07
I am trying to connect a printer. I want to connect it wireless.
It is a HP Officejet Pro 8100.
The printer has , as usual, a CD for Windows.

During the process, it asks the IP address of the printer and some other details.

---

### Post by yetimon_64 on 2016-06-07
> **Gins said:**
> I am trying to connect a printer. I want to connect it wireless.
It is a HP Officejet Pro 8100.
The printer has , as usual, a CD for Windows.

During the process, it asks the IP address of the printer and some other details.

I just found [[COLOR=#0000ff]--this link--[/COLOR]]("http://hplipopensource.com/hplip-web/models/officejet/officejet_pro_8100.html") for your particular model on the HPLIP site. That will probably be more helpful in getting it working on Ubuntu than a Windows CD or its instructions (if I recall correctly the "cmd" command is for a windows command prompt, similar to a linux terminal, though not 100% sure nowadays).

The linux package that provides your drivers is the "hplip" package. You may need to have a good read of all the notes at the link above to get it working. I can't help much more as it has been many years since I got a HP printer working in Ubuntu (probably Jaunty in 2009 :-)) and I have no idea about your specific model. Good luck, yeti.

---

### Post by mastablasta on 2016-06-07
cmd opens command prompt in Windows. it is useless command in Linux. 

you need ot install the printer drivers (unless they are buil tinto kernel already) and then it should be available.

it might be better to take a step back and explain where exactly you get stuck if you follow the normal printer setup process.

---

### Post by grahammechanical on 2016-06-07
The HP Linux Printing and Imaging System (HPLIP) is installed by default on Ubuntu. At least it is on my system and I do not have a printer. My guess is that you need to make a wireless connection to the router. Look at the instructions under HP Wireless setup wizard.

[http://www8.hp.com/uk/en/campaigns/wireless-printing-center/printer-setup-help.html](http://www8.hp.com/uk/en/campaigns/wireless-printing-center/printer-setup-help.html)

It is all done from the printer in a similar manner to connecting Ubuntu to the router. Ubuntu System Settings>Printers might allow you to set up a printer. This is a bit old but it might still be applicable.

[https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)

> Turn on the printer, and connect to the All-In-One. This may be via USB  (for local and/or network access), ethernet, or wireless. 
[LIST]
[*]For USB, connect the USB cord from the printer to your computer. For sharing the USB printer for network access, please see [here]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu"). 


[*]To connect via ethernet, connect the printer's ethernet port to your router. 
[*]To connect via wireless, use the printers LCD screen to navigate the menu as per the printer's manual.
[/LIST]


Regards.

---

### Post by Gins on 2016-06-07
Thanks everybody

Normal procedure does not work. 
I did everything I could.

I know the printer should be on the segment on the network.

I don't know how to solve this issue.
..................................................................................................................................................................................................
Now I bought another device to fix the problem.

[B]It is TP-LINK tiny pocket router.

SOME OF THE DETAILS ARE AS FOLLOWS:
….......................................................................
Wi-Fi pocket router/AP/ TV Adapter/ Repeater
Model No.  TL – WR710 N
…....................................................................

Ideal for turning any wired Internet into Wi-Fi !
Instantly established a secured Wi-Fi Network for all of your Wi-Fi enabled devices.
…...............................................................................................................................[/B]

The manuals, CD and everything for Windows.



( The printer supports Wi-Fi. I saw 2 MAC addresses on the backside of the printer.
One for wired Internet and the other for wireless Internet.)
.................................................................................................................................
I will write some more details later on. I have to leave for work now.

---

### Post by Gins on 2016-06-09
**Some more details**

I bought a kind of a wireless adapter.

This adapter ought to recognize wireless printer.

I could not fix it. It had a CD. 

In the CD, I found all the drivers for Windows.

I was so desperate. **I threw it away and bought this TP -LINK pocket router.**

..............................................................................................................................................................................
My ISP has given me a router. So I connect to the Internet via this cable router.

I have the Internet via a cable.

It has Wi-Fi too. However, I connect this Desktop computer via a network cable.

I connect my Asus tablet and the old Windows laptop via Wi-Fi.

It is possible to connect another 3 computers to this router.

I have  100 mbps Internet.  It is fast Internet. My ISP says their lowest speed is 100 mbps.

I have an i3 Windows laptop. It is Toshiba.

It works fine. However, I rarely use it.


Your thoughts are very welcome.** I must connect my printer wireless.**

---

### Post by howefield on 2016-06-10
Just to take a step back, have you successfully installed the printer driver yet ?

---

