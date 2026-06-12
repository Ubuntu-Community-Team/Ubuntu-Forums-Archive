---
title: "display latency"
date: 2019-02-03
forum: General Help
---

### Post by christon74 on 2019-02-03
Good evening fellow Ubunters _ I'm faced with a new problem. It started yesterday. Everything now takes much longer to display. Be it clicking on a new tab (Firefox) or opening any text document saved to my hard disk, it takes quite some tab now to be displayed on the screen. This is what I call "display latency". Even scrolling down my favourites in the left panel (Firefox) takes more time now. 
Hardware: Fujitsu-Siemens Esprimo E-5731- E-Stars
The display is an Orion TV
Ubuntu Flavour : Ubuntu 18.04 which I try my best to keep up to date.
Thanks in advance for any tip.

---

### Post by Frogs Hair on 2019-02-04
There is a terminal based program in the repository named latencytop which is designed for developers. I haven't used it nor would I know how to interpret or use the data displayed . Some research and study would be needed before considering its use. How are you connecting to the TV?

---

### Post by christon74 on 2019-02-05
Good morning Frogs Hair:) This old Orion TV set is connected with a VGA cable. I am still wondering where does this problem come from. At some point, I thought it had something to do with swappiness and I have changed the value (from 0 to 10)_ I have already done both apt-update and apt-upgrade, not to much avail; this did not solve the problem. I have also tried clearing the cache (Firefox) but I am rather loath to do that, for the reason I then have to retype all my passwords for different web sites. I am thinking I should go for a Lubuntu desktop instead of Gnome? Two other important pieces of info: RAM is 7 Go and the version of Firefox appears to be the latest. Yet perhaps it is a question of RAM, because it seems other applications are slowed down too. I understand downloading and then using the lubuntu desktop could help. But I'm afraid of compounding the problems even further. After all, downloading lubuntu desktop might well bring some packages that are already present, together with other apps and software I do not need or want. Another idea is to buy another 4 Go RAM ?

---

### Post by Frogs Hair on 2019-02-05
The program I mentioned will display latency for various processes in milliseconds, but what to do with the information is another matter. To display memory info use the following command. ```
 cat /proc/meminfo
``` You can add information about your system with the following command  ```
lspci 
```

---

### Post by christon74 on 2019-02-06
Good morning again Frogs Hair :)  _ This PC is still playing up a bit. I have tried several things like revealing the hidden startup apps and unclicking or stopping some of them. It seems this has somewhat improved speed, and I have also downloaded Opera, since they say it is lighter on CPU and memory, but again the selfsame phenomenon with it. I believe I should seriously consider buying more RAM. Thanks anyway. Have a nice Wednesday. Ooops, I almost forgot to post the lspci : 

```
christophe@christophe-ESPRIMO-E5731:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LF-3 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JD (ICH10D) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 4-port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 2-port SATA IDE Controller (rev 02)
```

---

### Post by HermanAB on 2019-02-06
Well, you could run the good old utility 'top' to see what is really sapping your CPU cycles.

Note that on old hardware, you really should rather use XFCE4 or LXDE, not the default Gnome.  If you are not too paranoid about security, then disabling AppArmor will also speed things up tremendously on an old machine.

---

### Post by christon74 on 2019-02-06
Hello Herman  _  :) _ Thanks for all this. I do not know how old is my PC. It is a second hand Fujistu-Siemens Esprimo 5731 E stars I have bought from "PlusdePc.com" When I bought it, the RAM was not enough to install Ubuntu, so I bought an additional 4 Gb RAM stick which puts it at 7Gb. Now about swappiness, I remember forgetting to create a swap partition during install, so I then created a Swap file. It is still sitting there. 2Gb with a -2 priority but does not seem to do its job at all. It is not just web pages which often are torn and displayed with lines, but the launch of some other applications is slower too. This is becoming not exactly a headache but a long dark narrow tunnel. I am thinking there might be some issues with the graphics drivers. That's why I have downloaded the intel graphics update. But it won't install. 

                          christophe@christophe-ESPRIMO-E5731:~$ sudo su

 [sudo] password for christophe:  
 root@christophe-ESPRIMO-E5731:/home/christophe# sudo gdebi /home/christophe/Downloads/intel-graphics-update-tool_2.0.2_amd64.deb
 Reading package lists... Done
 Building dependency tree         
 Reading state information... Done
 Reading state information... Done
 This package is uninstallable
 Dependency is not satisfiable: libpackagekit-glib2-16 (>= 0.8.10)
 
 
 root@christophe-ESPRIMO-E5731:/home/christophe# sudo apt-get installibpackagekit-glib2-16 (>= 0.8.10)
 bash: syntax error near unexpected token `('
 root@christophe-ESPRIMO-E5731:/home/christophe# sudo apt-get instal libpackagekit-glib2-16 (>= 0.8.10)
 bash: syntax error near unexpected token `('
 root@christophe-ESPRIMO-E5731:/home/christophe# sudo apt-get instal libpackagekit-glib2-16
 E: Invalid operation instal
 root@christophe-ESPRIMO-E5731:/home/christophe# 

Drat! And 7 billions drat! I have just found this! [https://www.omgubuntu.co.uk/2018/03/intel-graphics-update-tool-discontinued](https://www.omgubuntu.co.uk/2018/03/intel-graphics-update-tool-discontinued)
  
Again, thanks for all help and trouble.

---

