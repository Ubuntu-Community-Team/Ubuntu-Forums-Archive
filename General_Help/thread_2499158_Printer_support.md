---
title: "Printer support?"
date: 2024-07-15
forum: General Help
---

### Post by lawrence-joy on 2024-07-15
Hello, I recently purchased an Epson ET-15000 printer and the only printer drivers they have is for Microsoft Windows. Their advertising does not state this and I would have considered a different manufacturer's printer, but I liked the idea of a super ink tank setup. Does Ubuntu have a driver for this particular printer?

---

### Post by TheFu on 2024-07-15
Drivers come from the printer vendors.  Ubuntu/Canonical doesn't make any printer drivers.  You might be able to find a commercial company that supports it.  I think there's one in Germany that is known to create printer drivers for $50-$100. I don't remember the name, sorry.  I've only looked it up for Canon printers. In the end, we decided to give away the Canon printer (to a grandchild) and buy a new laser printer that was well supported (plug-n-use) under Linux. The laser printer costs 1/10th per page, and has lasted almost 20 problem free years.  I'm sure the Canon was a great printer, but I think life is too short to deal with hardware that doesn't support my OS.

The best supported printers use something called "driverless printing" and most current printers that aren't specialized support it.  [https://openprinting.github.io/driverless/](https://openprinting.github.io/driverless/)

If you are a linux user, you know to always check the Linux support BEFORE buying any hardware. Sometimes we forget that step.

---

### Post by grahammechanical on 2024-07-15
What computer operating systems do you have? If you are dual booting Windows & Ubuntu then you can use that printer with Windows. If you have Ubuntu installed, then connect the printer to the computer and see if Ubuntu detects the printer and if the default Ubuntu utilities can make use of the printer.

Linux developers provide hardware drivers. It is called Linux Firmware. This firmware is part of every Linux installation. The Linux developers may have already worked out drivers for this printer. Or, you may find that only certain basic functions work.

The printer software for Linux is called CUPS (Common UNIX Printing System)

[https://ubuntu.com/server/docs/install-and-configure-a-cups-print-server](https://ubuntu.com/server/docs/install-and-configure-a-cups-print-server)

Check this out

[https://www.epson.co.uk/en_GB/support/sc/epson-ecotank-et-15000/s/s1758?selected-tab=&selected-os=Linux](https://www.epson.co.uk/en_GB/support/sc/epson-ecotank-et-15000/s/s1758?selected-tab=&selected-os=Linux)

[https://help.ubuntu.com/stable/ubuntu-help/printing-setup.html.en](https://help.ubuntu.com/stable/ubuntu-help/printing-setup.html.en)

This will give some idea of what you can try

[https://askubuntu.com/questions/1441868/how-to-setup-epson-ecotank-printer-in-ubuntu-without-driver-available-from-epson](https://askubuntu.com/questions/1441868/how-to-setup-epson-ecotank-printer-in-ubuntu-without-driver-available-from-epson)

Regards

---

### Post by Dennis N on 2024-07-15
It looks like there is one in Epson Support. See screenshot.

---

### Post by Topsiho on 2024-07-16
Hi,

I recently bought a "smart" HP printer, that needed a permanent internet connection for the smart function, which I don't want.
So I tried tot connect it with **USB only** and tried the reported printers one by one, and discovered that a "driverless" printer functioned marvellously. No HP updating the printer so that it doesn't accept non HP inkts anymore, no snooping on the use I make of the printer, no risk of having having private documents being sent to HP, no ... just fill in yourself.

Many thanks to the marvellous people of open printing!

I wish you the same success!

Greetz,

Topsiho

---

### Post by lawrence-joy on 2024-07-22
No, I didn't know about checking for Linux support before ordering this Epson ET-15000 printer. Next time I'll know. However, I wanted the ink tank capability, so I ordered it.

---

### Post by lawrence-joy on 2024-07-22
I have two solid state drives. One has Windows 10 on it and the other has Ubuntu version 22.04, which I use 99% of the time. The Epson ET-15000 printer shows up on available printers and I have it selected as the default printer. I can get 8 1/2" X 11" paper printed from the cassette (front paper tray). The problem is when I try to print 11" X 17" paper from the paper tray (the back paper tray) it won't print. I called the Epson support line and the guy told me that the Epson driver for the Linux OS is basic and i would have to find a driver somewhere else--he couldn't/wouldn't help me.

---

### Post by lawrence-joy on 2024-07-22
Again, the Epson printer driver for Linux is just basic and will not work for printing from the back tray. The guy I talked with at Epson support said I would need to find a driver.

---

### Post by lawrence-joy on 2024-07-22
Okay, it looks like I will try the searching for "Open Printing" or "Ubuntu Printing". There is just too much gobilty (sp) gook for me to understand. I will report back when I find an answer.

---

### Post by TheFu on 2024-07-22
There used to be relatively cheap, tiny, network adapters for non-networked printers that would accept PDF or PS files.  Of course, these were just basic LPR servers.  It is a way to make a printer that doesn't work with Linux work, since you just need to send either a PDF or PS file to that device.

Above, I mentioned a commercial company that did printer drivers for Linux.  I've never used them, but I haven't heard anything bad about them either.
[https://www.turboprint.info/printer_Epson_EcoTank_ET15000.html](https://www.turboprint.info/printer_Epson_EcoTank_ET15000.html)  They say you can use it for 30 days to see if it works for you.  Reputable companies do that when they are small.  
> TurboPrint 2.56-1 (06-May-2024)
(multifunction devices: **only printer unit is supported**, not scanner unit) 

---

### Post by Topsiho on 2024-07-23
Sorry to read that for your printer Linux support is below par  :( . Usually, I understand, most printers, in Linux, just need to be hooked on, no extra software to be installed, and that they then do what they are supposed to do, thanks to people like those of open printing.
My printer is a new HP all-in-one printer, with a not appreciated "smart" service, and after much frustration I found this very simple solution, which I am glad to share with anybody.

What do you think an Epson employee would tell you?

Greetz from Topsiho

---

### Post by oldfred on 2024-07-23
I thought new printers were all "driverless".
Or a Apple standard used by everyone.

What does driverless show in terminal:
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/**[/COLOR][COLOR=#000000]$ driverless [/COLOR]
ipp://Brother%20HL-L2390DW._ipp._tcp.local/ 
ipp://Brother%20HL-L2390DW%20(USB)._ipp._tcp.local/
[/FONT]
```

[https://wiki.debian.org/CUPSDriverlessPrinting](https://wiki.debian.org/CUPSDriverlessPrinting)
[https://wiki.debian.org/CUPSDriverlessPrinting#ippoverusb](https://wiki.debian.org/CUPSDriverlessPrinting#ippoverusb)

---

### Post by Topsiho on 2024-07-23
jaap@tambora:~$ driverless
jaap@tambora:~$ driverless
ipp://HP%20LaserJet%20MFP%20M234dw%20(94A808)%20(USB)._ipp._tcp.local/
jaap@tambora:~$ 

Hello oldfred. 

First was the result if the the printer is not in use (obvious), second after printer is put in use.
It surprised me and I don't know what software is responsible for this (which is correct).

If you can tell more about this I would very much appreciate it.

I used always to go for HP and HPLIP but things have apparently changed, with no HPLIP support and HP forcing you to be always connected even if you print a local file on your local printer.
Specially when you print a private document, of yourself or for someone else, this might go to HP if you are connected, which is very serious indeed.

Greetz from

Topsiho

---

### Post by oldfred on 2024-07-23
I was one if not the first to get a Laserjet I, many Laserjet 2 and used a 3 until I retire even though 4's were the standard by then.
And HP used to be one of the better printers since then, but seems to have lost its way.
After going thru a variety of inkjet and having lots of issues, I did get a HP inkjet. And it just worked but ink was so expensive & my wife starting to print a lot of stuff. So now using Brother laser printer.
HP just announced it was discontinuing the always connected to Internet models.

[h=1]**[SIZE=2][FONT=arial]HP to discontinue online-only e-series LaserJet amid user gripes[/FONT][/SIZE]**[/h]https://www.theregister.com/2024/07/09/hp_to_discontinue_eseries_laserjets/

[https://openprinting.github.io/driverless/01-standards-and-their-pdls/](https://openprinting.github.io/driverless/01-standards-and-their-pdls/)

---

### Post by Topsiho on 2024-07-23
> **oldfred said:**
> I was one if not the first to get a Laserjet I, many Laserjet 2 and used a 3 until I retire even though 4's were the standard by then.
HP just announced it was discontinuing the always connected to Internet models.

[h=1]**[SIZE=2][FONT=arial]HP to discontinue online-only e-series LaserJet amid user gripes[/FONT][/SIZE]**[/h]https://www.theregister.com/2024/07/09/hp_to_discontinue_eseries_laserjets/

[https://openprinting.github.io/driverless/01-standards-and-their-pdls/](https://openprinting.github.io/driverless/01-standards-and-their-pdls/)

Great! Great, and thank you for reporting this.
But I think I don't need HP anymore. Love my present printer, even if it is a HP printer, as driverless.
Only thing I miss is that I have not the HP Toolbox, which was really handy in my previous printer

Topsiho
.

---

### Post by tea for one on 2024-07-23
> **Topsiho said:**
> Only thing I miss is that I have not the HP Toolbox, which was really handy in my previous printer
hplip	3.23.12+dfsg0-0ubuntu5
hplip-data	3.23.12+dfsg0-0ubuntu5
These (cli) packages are included in Ubuntu 24.04

For HP Toolbox, you need [COLOR="#0000FF"]hplip-gui[/COLOR] (universe repo)
> This package contains utilities with graphical user interface (GUI) for
HPLIP: HP Toolbox, HP Fax, .

---

### Post by him610 on 2024-07-23
Talking about printers....

I have two printers,...
One is a Dell 1700N laserjet printer that I bought (refurbished) around 18 years ago. I replaced the toner cartridge 7 or 8 years ago. It has been printing faithfully all those years from LTS to LTS. 

The second one is a Brother MFC-7360N laserjet that I bought (refurbished) around 10 years ago. I bought it for its multi-function capabilities: print, copy, scan, fax. Never had any issues, it just works. I can print to it from any of 5 different computers connected on my LAN. I download the Brother software from the Brother website. 

If I ever need to buy another printer, it will be a Brother machine - they provide software for Linux devices.

---

### Post by csae2608 on 2024-07-24
Epson has very good driver support, you can find Linux Printer driver here

[https://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](https://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

if you have still trouble installing, for example if you want setup the USB printer driver, you can attempt to uninstall "ipp-usb".

---

### Post by Topsiho on 2024-07-24
Hello tea for one,

I know these packages, used them in my previous HP printer.
But: the HP-toolbox reports that my printer is not connected, with only a USB connection.
That's just the trouble: the printer insists on an internet connection, and I insist on not to have it internet connected.
As a driverless printer it functions marvellously, so I am quite happy ... I'll be able to see when the inkt cartridge is empty, I suppose.
At this point in time it is not.

Thanks for your suggestion :)

Topsiho

---

### Post by lawrence-joy on 2024-07-25
TheFu, I think that I have tried so many different things that I have confused my OS. Thanks for the link to the "TurboPrint". Yes, a 30 d free trial to see if it will work, and only printer unit is supported, not scanner, but that is all I am after. I will give it a try and see if I can get 11" X 17" paper printed. Will report back in a few days after trying it.

---

### Post by lawrence-joy on 2024-07-26
Hello (TheFu), I downloaded the trial version of Turboprint and tried to execute it. The first thing that was stated was can not communicate with CUPS. So I did the following: I am trying to download CUPS, which I execute in the terminal with 'sudo apt install cups'. "Once the download and installation have finished, the CUPS server will be started automatically."--NO!, that does not happen. I get the following: $ sudo apt install cups
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
cups is already the newest version (2.4.1op1-1ubuntu4.10).
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
Next: The CUPS server’s behavior is configured through directives found in the /etc/cups/cupsd.conf configuration file. This CUPS configuration file follows the same syntax as the main configuration file for the Apache HTTP server.
"To configure the email address of the designated CUPS server administrator, edit the /etc/cups/cupsd.conf configuration file with your preferred text editor, and add or modify the ServerAdmin line accordingly. I tried using 'cat' to view the file but it seems to be empty. What is going on? I tried to edit the file with nano but the file was empty. So how to get to the ServerAdmin line??

---

### Post by donald187 on 2024-07-27
I'm gonna throw this in in case it helps.  First, I'm no expert.  I have a Brother printer now and before that I had an Epson.  Neither worked out of the box.  i.e. driverless printing didn't work out of the box.  I learned this trick from the following bug report.

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1638395](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/1638395)

I got the printer's ip address and printer name from the display on the front of the printer. In my case the ip address is something like 192.168.1.xyz.  In the case of the Epson the name was something like EPSON123456.  And I don't think it's labeled "printer name" on the display but I forget what it's called.  So in /etc/hosts you add the line

```

192.168.1.xyz   EPSON123456.local

```

changing the ip address and printer name to your ip and printer name.  Make sure you put the .local.  Reboot.  Then my printer works with driverless printing.

This has worked flawlessly on Debian.  It seems to me that in a previous version of Ubuntu that the printer disappeared on occasion.  (EDIT:  This has now happened on Debian as well.  A reboot brought it back.)   Once it also did a weird thing where the printer name (different from what I mentioned above) in the printer settings changed to "printer at 192.168.1.xyz" spontaneously but kept working.  So on Ubuntu I personally use the printer settings to add a printer once I reboot to get one that stays put.  But maybe you won't have to do this and could cross that bridge when you come to it.

(Mine is printing over wifi.  I don't recall if you said how your printer is connected.)

---

### Post by lawrence-joy on 2024-07-29
I was able to view the cupsd.conf file using the cat command but could not find any ServerAdmin line. I was able to get into the cupsd.conf file by code sudo nano cupsd.conf and could do editing, like adding a line for ServerAdmin, but don't know what the coding should be. My Epson ET-15000 printer is connected directly to my PC via USB cable. The PC does not have WiFi. Seems that the invoking of the cups server would automatically connect with the email account? But what do I know? Sorry to say but I need some hand holding to get through this situation. Anybody please help with your expertise.

---

### Post by lawrence-joy on 2024-07-30
Everything I have tried has been a failure. Here is what I did:
larry@larry-MS-7693:~$ sudo apt-get install -reinstall cups
E: Command line option 'r' [from -reinstall] is not understood in combination with the other options.
larry@larry-MS-7693:~$ sudo apt-get install-reinstall cups
E: Invalid operation install-reinstall
larry@larry-MS-7693:~$ sudo systemctl status cups
&#9675; cups.service - CUPS Scheduler
     Loaded: loaded (/lib/systemd/system/cups.service; disabled; vendor preset: enabled)
     Active: inactive (dead) (Result: signal) since Tue 2024-07-30 10:54:50 EDT; 1h 9min ago
TriggeredBy: × cups.socket
       Docs: man:cupsd(8)
    Process: 1261 ExecStart=/usr/sbin/cupsd -l (code=killed, signal=SEGV)
   Main PID: 1261 (code=killed, signal=SEGV)
        CPU: 11ms

Jul 30 10:54:50 larry-MS-7693 systemd[1]: cups.service: Scheduled restart job, restart counter is at 5.
Jul 30 10:54:50 larry-MS-7693 systemd[1]: Stopped CUPS Scheduler.
Jul 30 10:54:50 larry-MS-7693 systemd[1]: Dependency failed for CUPS Scheduler.
Jul 30 10:54:50 larry-MS-7693 systemd[1]: cups.service: Job cups.service/start failed with result 'dependency'.

I tried previously running 'sudo apt-get remove cups -y -s' and then rebooting my Ubuntu 22.04 OS as it is supposed to download CUPS server automatically.
No Joy!

---

### Post by deadflowr on 2024-07-30
reinstall is a double dash like so
```
sudo apt-get install --reinstall cups
```

---

### Post by lawrence-joy on 2024-07-30
I reinstalled Ubuntu 22.04, did the reinstall cups, did a restart of the OS, and did restart cups.service. Still no joy. I went to the settings and checked printers (the system goes there automatically) and states "Sorry! The system printing service doesn't seem to be available". I really need someone to stick with me, even hold my hand, to resolve this. Please, someone help me.

---

### Post by lawrence-joy on 2024-08-03
To: TheFu, Yes I have already asked the folks at TurboPrint for help on this. They have no idea, can't figure it out. I guess I am on my own. What is CUPd? Where do I look for it? How do I "inable" it? The reason I went with the Epson ET-15000 printer is because it can handle wide paper. For me I print out schematic diagrams, and other things, on 11" X 17" (ANSI/ASME size B) paper. I'll see what I can find on the Ubuntu Desktop Guide as you have suggested.--Thanks.

---

### Post by euol on 2024-08-03
CUPS (Common Unix Printing System) is a modular printing system for Unix-like operating systems that allows a computer to act as a print server.

dpkg -l | grep cups
sudo apt update
sudo apt install cups
sudo systemctl start cups
sudo systemctl enable cups

---

### Post by lawrence-joy on 2024-08-03
Okay, I carried out your terminal commands and this is what I got:
larry@larry-MS-7693:~$ dpkg -l | grep cups
ii  bluez-cups                                 5.64-0ubuntu1.3                                   amd64        Bluetooth printer driver for CUPS
ii  cups                                       2.4.1op1-1ubuntu4.10                              amd64        Common UNIX Printing System(tm) - PPD/driver support, web interface
ii  cups-browsed                               1.28.15-0ubuntu1.2                                amd64        OpenPrinting CUPS Filters - cups-browsed
ii  cups-bsd                                   2.4.1op1-1ubuntu4.10                              amd64        Common UNIX Printing System(tm) - BSD commands
ii  cups-client                                2.4.1op1-1ubuntu4.10                              amd64        Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common                                2.4.1op1-1ubuntu4.10                              all          Common UNIX Printing System(tm) - common files
ii  cups-core-drivers                          2.4.1op1-1ubuntu4.10                              amd64        Common UNIX Printing System(tm) - driverless printing
ii  cups-daemon                                2.4.1op1-1ubuntu4.10                              amd64        Common UNIX Printing System(tm) - daemon
ii  cups-filters                               1.28.15-0ubuntu1.2                                amd64        OpenPrinting CUPS Filters - Main Package
ii  cups-filters-core-drivers                  1.28.15-0ubuntu1.2                                amd64        OpenPrinting CUPS Filters - Driverless printing
ii  cups-ipp-utils                             2.4.1op1-1ubuntu4.10                              amd64        Common UNIX Printing System(tm) - IPP developer/admin utilities
ii  cups-pk-helper                             0.2.6-1ubuntu5                                    amd64        PolicyKit helper to configure cups with fine-grained privileges
ii  cups-ppdc                                  2.4.1op1-1ubuntu4.10                              amd64        Common UNIX Printing System(tm) - PPD manipulation utilities
ii  cups-server-common                         2.4.1op1-1ubuntu4.10                              all          Common UNIX Printing System(tm) - server common files
ii  libcups2:amd64                             2.4.1op1-1ubuntu4.10                              amd64        Common UNIX Printing System(tm) - Core library
ii  libcupsfilters1:amd64                      1.28.15-0ubuntu1.2                                amd64        OpenPrinting CUPS Filters - Shared library
ii  libcupsimage2:amd64                        2.4.1op1-1ubuntu4.10                              amd64        Common UNIX Printing System(tm) - Raster image library
ii  printer-driver-hpcups                      3.21.12+dfsg0-1                                   amd64        HP Linux Printing and Imaging - CUPS Raster driver (hpcups)
ii  python3-cups:amd64                         2.0.1-5build1                                     amd64        Python3 bindings for CUPS
ii  python3-cupshelpers                        1.5.16-0ubuntu3                                   all          Python utility modules around the CUPS printing system
larry@larry-MS-7693:~$ sudo apt update
[sudo] password for larry: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease                                                                                                                              
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease                                                                                                                            
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease                                                                                                              
Hit:5 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) jammy InRelease                                                    
Hit:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease                            
Hit:7 [https://packages.mozilla.org/apt](https://packages.mozilla.org/apt) mozilla InRelease                                    
Get:8 [https://dl.packager.io/srv/deb/inventree/InvenTree/stable/ubuntu](https://dl.packager.io/srv/deb/inventree/InvenTree/stable/ubuntu) 20.04 InRelease [1,863 B]
Err:8 [https://dl.packager.io/srv/deb/inventree/InvenTree/stable/ubuntu](https://dl.packager.io/srv/deb/inventree/InvenTree/stable/ubuntu) 20.04 InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B6D583CCBD33EEB8
Reading package lists... Done
W: GPG error: [https://dl.packager.io/srv/deb/inventree/InvenTree/stable/ubuntu](https://dl.packager.io/srv/deb/inventree/InvenTree/stable/ubuntu) 20.04 InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B6D583CCBD33EEB8
E: The repository 'https://dl.packager.io/srv/deb/inventree/InvenTree/stable/ubuntu 20.04 InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
larry@larry-MS-7693:~$ sudo apt install cups
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
cups is already the newest version (2.4.1op1-1ubuntu4.10).
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
larry@larry-MS-7693:~$ sudo systemctl start cups
Job for cups.service failed because a fatal signal was delivered causing the control process to dump core.
See "systemctl status cups.service" and "journalctl -xeu cups.service" for details.
larry@larry-MS-7693:~$ sudo systemctl enable cups
Synchronizing state of cups.service with SysV service script with /lib/systemd/systemd-sysv-install.
Executing: /lib/systemd/systemd-sysv-install enable cups

Note that there are some errors and at least one failure.
I did a restart, my printer is on, and when I go to Settings > Printers the system still says Sorry! The system printing service doesn't seem to be available.
I checked [http://localhost:631](http://localhost:631) and get "Unable to connect".
Where do I go from here?

---

### Post by lawrence-joy on 2024-08-05
It looks like there are two ways to get CUPS, one way is the "normal" way and the other is through SNAP. I have deleted the CUPS service that I downloaded from SNAP and ran "sudo apt install cups". The OS says the CUPS (server?) is already there. I went to the manual "man cupsd.conf". According to the instructions from 
[h=1]Install and configure a CUPS print server[/h]After installing CUPS then:
The CUPS server&#8217;s behavior is configured through directives found in the /etc/cups/cupsd.conf  configuration file. This CUPS configuration file follows the same  syntax as the main configuration file for the Apache HTTP server.--That's nice, but I haven't worked with the Apache HTTP server, so I don't know!
Some examples of commonly-configured settings will be presented here. First thing is to make a copy of the configuration file, which I did.
To configure the email address of the designated CUPS server administrator, edit the /etc/cups/cupsd.conf configuration file with your preferred text editor, and add or modify the **ServerAdmin** line accordingly. For example, if you are the administrator for the CUPS server, and your e-mail address is [email]bjoy@somebigco.com[/email], then you would modify the ServerAdmin line to appear as follows:
 ServerAdmin [email]bjoy@somebigco.com[/email]

There is no ServerAdmin line so I guess I could add my email address, but I am a little confused by the info from the manual that says the ServerAdmin default value is "root@ServerName". And the ServerName default is the value 
reported by the "hostname(1)" command. Neither of which is in the config file.
What should I put in the config file to get this running?
--Thanks.

---

### Post by lawrence-joy on 2024-08-05
Today, 2024-08-05, I looked around some more for CUPS information. I found the following:
larry@larry-MS-7693:~$ sudo systemctl status cups
&#9675; cups.service - CUPS Scheduler
     Loaded: loaded (/lib/systemd/system/cups.service; enabled; vendor preset: enabled)
     Active: inactive (dead) (Result: core-dump) since Mon 2024-08-05 08:57:20 EDT; 8h ago
TriggeredBy: × cups.path
             × cups.socket
       Docs: man:cupsd(8)
    Process: 1621 ExecStart=/usr/sbin/cupsd -l (code=dumped, signal=SEGV)
   Main PID: 1621 (code=dumped, signal=SEGV)
        CPU: 10ms

Aug 05 08:57:20 larry-MS-7693 systemd[1]: cups.service: Scheduled restart job, restart counter is at 5.
Aug 05 08:57:20 larry-MS-7693 systemd[1]: Stopped CUPS Scheduler.
Aug 05 08:57:20 larry-MS-7693 systemd[1]: Dependency failed for CUPS Scheduler.
Aug 05 08:57:20 larry-MS-7693 systemd[1]: cups.service: Job cups.service/start failed with result 'dependency'.

This is disconcerting that it states "Active: inactive (dead) (Result: core-dump). Where did that come from, what caused it, and what to do to make it "active"?
In the Process: line it has (code=dumped, signal=SEGV). What does that mean and how to correct it?
Then in the last four lines the third line says "Dependency failed for CUPS Scheduler", and in the fourth line is "cups.service: Job cups.service/start failed with result 'dependency'" So what is going on with this and how do I fix it?
--Regards, Larry

---

