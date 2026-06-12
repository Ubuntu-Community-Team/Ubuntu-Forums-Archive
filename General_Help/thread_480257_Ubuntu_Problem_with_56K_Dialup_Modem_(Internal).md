---
title: "Ubuntu: Problem with 56K Dialup Modem (Internal)"
date: 2007-06-21
forum: General Help
---

### Post by deathspell on 2007-06-21
Hi,

I'm a first time user of Linux (Ububtu). I just installed version 7.04 but I can't access the internet with my dialup modem. My version did not come with the KPP dialer so I used "sudo pppconfig" to configure the dialup and try to connect but it gives me the error "unrecognized option /dev/modem". 

Under network, it does show the wired network and the modem so I assumed that the modem is already installed since the wired network is working fine.

I haven't installed any modem driver. I'm not sure if that was needed cause when I went to the hardware list, my modem was listed.. But I couldn't find any option to diagnose or query the modem like there is Windows so I don't know if its working correctly. The dialup modem is all I have so this is the only way I can access the internet. It is an internal PCI modem. I used ListModem in Windows as suggested in another thread and this is the result I got.

=====================================================================
=              SYSTEM INFORMATION                                   =
=====================================================================
Date         : 6/21/2007
ListMdm Ver  : 1.6
Windows OS   : Microsoft Windows XP 
Build Number : 2600 

=====================================================================
=              RESULT OF MODEM QUERY                                =
=====================================================================
NUMBER OF MODEMS FOUND = 1

MODEM #1:
  PCI CONFIGURATION INFORMATION READ:
     VENDOR ID              : 163C
     DEVICE ID              : 3052
     SUBVENDOR ID           : 163C
     SUBDEVICE ID           : 3052
     REVISION ID            : 04

  DEDUCED INFORMATION:
     VENDOR NAME            : UNKNOWN
     DEVICE NAME            : UNKNOWN
     SUBVENDOR NAME         : UNKNOWN
     MODEM TYPE             : UNKNOWN
     WINXP INBUILD SUPPORT  : NO

---

### Post by deathspell on 2007-06-21
I used a Live version of Linspire and my modem worked perfectly fine there and I was able to dial to the internet so there should be no compatibility issues. So I guess its just Ubuntu thats giving me trouble. Still seeking help.

---

### Post by Bartender on 2007-06-21
Folks love to heap abuse on Linspire as a pretender, but if it allows you to go online and Ubuntu doesn't your choice is clear.  For now anyway.  I've also heard it said that Puppy Linux does a better job detecting winmodems.

A running Linux PC without the internet is pointless.  If you're stuck with dial-up then you've gotta go with whatever lets you get online.

---

### Post by Dragonbite on 2007-06-21
Ubuntu detected my Winmodem on one system, but not on the other so I got a USR external and it hasn't failed me yet (well, except when the Cat pissed on it, but after washing it out and letting it dry it worked fine).

The external USR is located at /dev/ttyS0 I believe (it doesn't detect it as /dev/modem).  

I don't know if it was Kubuntu or elsewhere but somebody had an option to "scan for modem".  If it is Kubuntu then you can run it live, try it and see if/where it finds it.  Then in the Ubuntu installation just manually point to it (/dev/modem is a symlink to something under /dev anyway).

You can also look at installing kppp, but I would try a Kubuntu LiveCD first and see if it detects it and where.

---

### Post by deathspell on 2007-06-21
I don't have Kubuntu but I tried Xubuntu and the problem was the same, neither of them have KPP installed. I have to install it from "Add/Remove Programs" and that needs an internet connection so I'm back to square one. How do I scan for the modem? I don't see an option like that anywhere. I hated Linspire, its way too slow and keeps hanging. Maybe I'm not doing something right in Ubuntu. 

The modem is listed in the hardware listed so shouldn't it be working? Maybe its the dialer thats messed up. I don't know what to do.

---

### Post by Dragonbite on 2007-06-21
Xubuntu uses the same Network Manager as Gnome so if it isn't in one it isn't in the other.

You may be able to download the packages here through the Ubuntu website : [[COLOR="Blue"]http://packages.ubuntu.com/feisty/net/kppp[/COLOR]]("http://packages.ubuntu.com/feisty/net/kppp").  Another annoying method is to pick the different locations from the drop-down box (if it has it) and see what happens.

It is probably going to be annoying in download-try-need dependency-download-try-need dependency-...etc.

Have you looked up the [[COLOR="Blue"]LINMODEM[/COLOR]]("http://www.linmodems.org/") website?  They have a scanModem tool which worked for me once a long time ago.

---

### Post by deathspell on 2007-06-22
Exactly which is the file I need to run for the scanmodem tool? I tried running something but it wasn't an executable file.. It just opened a text file..

I also tried installing gnome ppp but it gave me a C compiler error. I don't know what I'm doing wrong..

---

### Post by Dragonbite on 2007-06-22
This is from their website page [[COLOR="Blue"]http://132.68.73.235/linmodems/index.html#scanmodem[/COLOR]]("http://132.68.73.235/linmodems/index.html#scanmodem")
> After decompression (command gunzip scanModem.gz ), do not forget to make it executable with chmod +x scanModem, and then launch the command typing ./scanModem , or trigger it with source scanModem .
scanModem writes files full with information in a new subdirectory named Modem .
Some of the tests may require to run scanModem as a superuser, which you can do as follows:

    * By logging in as root if you are not a Debian/Ubuntu user.
    * By becoming root while already logged in as a regular user, if you are not a Debian/Ubuntu user. The command to achieve that is su (avoid using su - here, just su, or you will need to type the full path to scanModem).
    * If you ARE a Debian/Ubuntu user, use the syntax sudo ./scanModem 

---

### Post by Matchless on 2007-06-22
Just some guidance, the vendor id 163c;3052 on Google shows that it is probably a Smartlink modem. You can download the Astra 32 and/or Aida32 system tools (for windows!) and also get more specific id's in windows as well. Then search for Smartlink in the forums once confirmed and install the drivers and see if you can get it going. If you see your modem recognised in the hardware it does not mean that the drivers are already installed, just that the device is recognised. You can also type lspci and should see the device9modem0 as well. Try Wvdial for dialing out for starters as it is quite good before going to gnome-ppp. Then you can install via Synaptic.

---

### Post by deathspell on 2007-06-22
Okay I'll try this and be back in a few minutes. I had tried installing gnome ppp but it gave me a C compiler error. I don't know why that happened.. Maybe I'm not doing something right.. I saved and extracted them to the desktop and then went to terminal, went to the directory and tried running the commands...

Okay let me see what happens with Wvdial.

And yes, it is a smartlink modem.

---

### Post by deathspell on 2007-06-22
Okay, I'm back. scanModem created a directory with some files. I don't know how to run wvdial.. what commands do I need to type? I tried lspci and the modem is listed there... Where do I go from here? I still don't know what driver I need to install

---

### Post by Matchless on 2007-06-22
Read this: [http://ubuntuforums.org/showthread.php?t=476449](http://ubuntuforums.org/showthread.php?t=476449) Normally you will be able to download the driver from the feisty repositories as well as the daemon, they can be found by searching for sl-modem in synaptic with repositories enabled and when on line. an easy way here is to borrow a serial modem and get on line and then do all via Synaptic, get your drivers going and then switch to your Smartlink.
Now read this on the Smartlink drivers: [http://ubuntuforums.org/showthread.php?t=190728](http://ubuntuforums.org/showthread.php?t=190728) it is abit out of date, but the process helps to explain what to do. the also read this for info:  [http://ubuntuforums.org/showthread.php?t=308098](http://ubuntuforums.org/showthread.php?t=308098) Okay now that you have all the detail, it means you have to do the following:
1) Ensure that you have the necessary programs installed that you need to compile your own drivers, build-essential, headers etc
2) Install the sl-modem-modules driver with synaptic from the repositories or compile your own by downloading and installing slmodem-2-9-11-2007-0505.tar.gz from the linmodems website
3) by downloading and installing the latest ungrab-winmodem.tar.gz from the linmodem website.
4) by downloading and installing the latest daemon: sl-modem-daemon xxxx from the debian website as it seems as if the one in the repositories do not work
Here is the linmodem site: [http://linmodems.technion.ac.il/packages/](http://linmodems.technion.ac.il/packages/)

It may seem daunting, but what really should have happened, is you download and install the two packages, driver and daemon directly with Synaptic, while connected through your ubuntu pc to another PC that is on line, that takes about 10 seconds to install, but it seems as if the sl-modem-daemon version may be outdated by the latest update to the kernel version and the one on the debian site is renewed regularly and aparently works according to the one post I gave you a link for, so that means you can just download, put on your Desktop and double click in Ubuntu or right click in Kubuntu and run the sl-modem-daemon.xxx.deb file and install.
The rest of the post and threads should help you.
Here is the info on WVdial as well:
  	 	 	 	 	 	 	 	 	  [COLOR=#000000][SIZE=3]_**Tried and tested good old wvdial:**_[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]The most reliable way to get dialed up is via [/SIZE][/COLOR][COLOR=#000000][SIZE=3]**wvdial**[/SIZE][/COLOR][COLOR=#000000][SIZE=3] from the konsole, but this means you need to keep the konsole open while you are connected to make sure that you are able to disconnect the modem by typing CTRL+C to disconnect from the telecom line and get back to your normal prompt. If you happen to close the konsole before disconnecting, you may have to reboot your PC to get the modem to disconnect or you may not be aware that you are still connected and run up an account! This can be solved by installing a dial up dialer gui. Some problems may also be picked up when initially configuring wvdial, such as detection of modem.[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]_In the konsole type:_[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]sudo wvdialconf /etc/wvdial.conf[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]If this fails due to not finding a modem, it means the modem drivers are not properly installed, but if you can query the modem successfully in Kppp, then it may mean that wvdial cannot see /dev/modem to set itself up properly. In all cases you may have to open up the file:[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]In Konqueror navigate to /etc/wvdial.conf, Right click, Actions, Edit as root and change or add the following lines so that the file looks like this below and save:[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3][Dialer Defaults][/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Init1 = ATZ[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Modem Type = Analog Modem[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]ISDN = 0[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Phone = xxxxxxxxxxx [/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]New PPPD = yes[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Modem = /dev/modem[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Username = yyyyyyyyyyyyy[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Password = zzzzzzzzz[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Baud = 115200[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Stupid mode = on[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]# Carrier Check = no[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]xxxxxxxxx = the number to dial up your ISP[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]yyyyyyyyy = your username supplied by your ISP[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]zzzzzzzzz = your ISP access password[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]In the last line remove the comment # to enable Carrier Check = no if you are using a Smartlink internal modem.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]You can also add W2 to the Init2 line to show the connection speed if required[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]_Now go to the console and type:_[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]sudo wvdial[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Once connected see if you can open your browser[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Remember to keep the konsole open while you are connected, you can minimise it if it is in your way.[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]_To disconnect line while in konsole type:_[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]CTRL+C to end the connection[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]_Some hints:_[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]If you find that you lose the connection after 30 sec to 3 minutes, then edit pppd.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Right click on /etc/ppp/options, actions, Edit as root[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Find lcp-echo-interval 30 and lcp-echo-failure 4 and comment both out by adding a # at the beginning of the lines.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]If you find that you connect successfully, but cannot open any webpages in Firefox then add line default route to /etc/ppp/peers/wvdial[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]_Adding a gui to wvdial:_[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]The good news is that there is a nice simple gui for wvdial called Gnome-ppp. This is normally only used in Ubuntu and the name Gnome tends to keep KDE die-hards from installing it on Kubuntu, but it installs straight from the repositories. So once you have wvdial working and you can connect to the internet, enable and update your repositories, use your package manager to download and install Gnome-ppp, right click on the menu icon and create an icon on your desktop. Now rename it so as not to embarrass you as Kubuntu user! to e.g. “Dial up ISP” and it should work very nicely and is definitely more bullet proof than Kppp, even on KDE.[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]_**Configuring Gnome-ppp:**_[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]Open Gnome-ppp and click on Setup[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Under Modem tab, Device, you can click detect to have Gnome-ppp detect your modem, but as under the wvdial setup this would maybe not work and you will have to type in your modem device. This could be /dev/modem or /dev/ttyS0 if you have and external modem connected to Com1 or /dev/ttyS1 if on Com2. Here I would suggest using Kppp (the only reliable function that will always work) to Query the modem if you are having problems.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Under Type select Analogue modem[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Under Speed 115200[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Phone line Tone[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Volume Hi (speaker volume)[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Dial attempts 1[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Wait for Dial tone checked[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Initstrings and phone number to dial should be picked up from your wvdial configuration, but if not enter them. (see wvdial)[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Under Networking tab[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Leave Dynamic IP Address and Automatic DNS enabled[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Under Options tab[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Check the following items as on, Abort connecting if no dial tone, Check carrier line, Check default route, Ignore terminal strings(Stupid mode). Leave the rest disabled or change any of the settings as your preferences once all is working.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Close and reopen Gnome-ppp[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Type in your ISP username[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Type in your ISP password[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Check remember password[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Select the number to dial up or type in.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Now click connect and you should be on.[/SIZE][/COLOR]

Hope this makes life more bearable if you are a dialup user.

---

### Post by deathspell on 2007-06-22
Okay I downloaded slmodem-2.9.11-20070505.tar.gz and ungrab-winmodem.tar.gz 


1) Ensure that you have the necessary programs installed that you need to compile your own drivers, build-essential, headers etc <--- what programs are these that I need?
2) Install the sl-modem-modules driver with synaptic from the repositories or compile your own by downloading and installing slmodem-2-9-11-2007-0505.tar.gz from the linmodems website
3) by downloading and installing the latest ungrab-winmodem.tar.gz from the linmodem website.
4) by downloading and installing the latest daemon: sl-modem-daemon xxxx from the debian website as it seems as if the one in the repositories do not work <--- what do I need to download for this?


PS. I don't have another PC.. If I could have got my ubuntu online then I didn't need to install the modem in the first place

---

### Post by deathspell on 2007-06-22
How do I run those two downloaded files?

---

### Post by deathspell on 2007-06-22
Its giving me several errors when I type **make**...

---

### Post by deathspell on 2007-06-22
I can't install ungrab-winmodem

---

### Post by Matchless on 2007-06-22
> **deathspell said:**
> Okay I downloaded slmodem-2.9.11-20070505.tar.gz and ungrab-winmodem.tar.gz 


1) Ensure that you have the necessary programs installed that you need to compile your own drivers, build-essential, headers etc <--- what programs are these that I need?
2) Install the sl-modem-modules driver with synaptic from the repositories or compile your own by downloading and installing slmodem-2-9-11-2007-0505.tar.gz from the linmodems website
3) by downloading and installing the latest ungrab-winmodem.tar.gz from the linmodem website.
4) by downloading and installing the latest daemon: sl-modem-daemon xxxx from the debian website as it seems as if the one in the repositories do not work <--- what do I need to download for this?


PS. I don't have another PC.. If I could have got my ubuntu online then I didn't need to install the modem in the first place

1) In one of the links a gave above; As you are going to compile your own drivers it is necessary that the required files are installed, check and/or install with Synaptic that the following are there:
build-essential, linux-headers-ARCH, debhelper and fakeroot is installed, ARCH is the result you get if typing uname -r in a terminal – version of kernel.
2)You have a choice, according to one of the links i gave you a poster got his Smartlink working by using the driver in the Feisty repositories, this is a deb file. You can also try the latest slmodem from the linmodem link I gave you and compile your own driver.
3) i think you should rather download the latest ungrab-winmodem, the one you did is a bit old and i know there are some updates in the new one. the daemon uses the ungrab when it runs.
4) Go to the debian website and download the sl-modem-daemon-2.9.9d+e-pre2-7etch2.deb hope this is spelled correctly as this one was found to work rather than the one in the Feisty repos by the poster in the link I gave you above.

You should not get any errors when installing the sl-modem-source-2.9.10+2.9.9d+e-pre2-5ubuntu1.deb file from the Fiesty repositories and need to have module-assistant installed to run this. This is the actual driver. if this driver does not work then you have to try the latest one from linmodems website an compile your own.

To run .deb files you double click on them in Ubuntu or Kubuntu Right click and install package.

---

### Post by Matchless on 2007-06-22
> **deathspell said:**
> I can't install ungrab-winmodem

OK, you probably have the wrong version, the latest version makes provision for the kernel versions above 2.6.18 which includes Feisty. You could just change the following:

In the folder there is a file ungrab-winmodem.c
find line
#include <linux/config.h>
and change to
#include <linux/tipc_config.h>

or download the new version

---

### Post by deathspell on 2007-06-22
Can you tell me the exact url of the files I need to download? I don't understand all this... I'm using Linux the first time...

I installed the build-essentials from the CD.. got help from the IRC channel.. I don't know how to install the rest of them

where do I get the deb files?


So far I installed the slmodem thingy... I haven't been able to do anything else.. and wvdial says I need wvstreams.. even the readme says so.. I went to the url and got lost.. don't know what I need from there

---

### Post by deathspell on 2007-06-22
I already installed **slmodem-2-9-11-2007-0505.tar.gz **... I need to install the .deb file too? Or is it the same? I don't want to mess up my Ubuntu :S Do any one of you guys have any IM or something?

---

### Post by deathspell on 2007-06-22
I edited the file and this time I was able to make and make install... but when I typed modprobe ungrab-winmodem .. it gave me some error.. operation not allowed.. or something like that..

Is there a way I can query the modem to see if its installed correctly?

---

### Post by Bachstelze on 2007-06-22
You know what ? You don't need to go through all of that ;) Precompiled drivers for your modem exist (I know it, I'm the one doing them). Just go to

[http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/](http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/)

Pick the one matching your kernel, extract, and voilà, you have a nice setup script in there :)

---

### Post by deathspell on 2007-06-22
Okay..

So what about ungrab-winmodem.. Do I need that too or will just the precompiled driver do the job? How do I know if its installed correctly? I don't know how to query the modem..

Could you tell me EXACTLY what all I need to do? I hope I'm not messing up my Unbuntu doing all unwanted things with wrong drivers and other files..

---

### Post by Matchless on 2007-06-23
HymnToLife,
                  Thanks this process works, all files are in the package and I quickly installed the modem as to test for deathspell. I will put together a brief howto from your procees for deathspell later today.
Thanks again.

---

### Post by Matchless on 2007-06-23
Hi,
    As this was just going in circles, I installed my Smartmodem and using Marv's advice and drivers did  the installation and it works perfectly. I am actually on line now on the Smartlink at 44000 and have been on for more than an hour. Using Kppp which is also behaving very well.
I have updated my old howto as promised and will post it later as a new thread for feisty only, so as not to bloat the older one more:
Be the first to try it and let me know please:
  	 	 	 	 	 	 	 	 	  [COLOR=#000000][SIZE=2]_**Howto get Smartlink winmodem working in Feisty**_[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]These drivers have been tested on a LG modem which is a Smartlink modem using a Netodragon chip with device number 2003:8800. It has also been tested on a LG modem with a Netodragon chip MDV92XP that has a device number 10b9:5459 and acually shows it to be Acer Labs Incorporated Ali/Uli.[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]Just some recognition to linmodems and specifically Marv Stodolsky – I hope someone is cloning you and making sure there are many around! Your work is much appreciated![/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]Marv's documentation states: The slamr-KernelVersion. Files provide drivers supporting Smartlink PCI card modems and USB modems sold under a variety of brand names.[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]Soft modems requiring ALSA modem drivers cannot be supported by the included slamr.ko driver. However the slamr.ko does provide a usefull diagnostic readout by:[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]sudo modprobe slamr[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]demsg | grep slamr[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2](A)First - Before starting identify your modem properly. Use lspci or lsusb and/or scan-modem at [/SIZE][/COLOR][COLOR=#000080]_[[SIZE=2]http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/scanModem.gz[/SIZE]]("http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/scanModem.gz")_[/COLOR][COLOR=#000000][SIZE=2] You can also identify it in windows with windows modem diagnostics or any windows program such as Astra32 or Aida32, even test your modem to make sure it is working.[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2](B) Second - Clean out your pc - If you have been experimenting with drivers, rather clean out all the dreggs and changes to configs you may have made or rather start with a new and clean Ubuntu install, otherwise you may get stuck with weird results that take longer to fix than a new reinstall.[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]Smartlink soft modems work very well in Ubuntu, the slamr-KernelVersion.tar.gz files have been specifically compiled for Ubuntu by Marv Stodolsy at Linmodem [/SIZE][/COLOR][COLOR=#000080]_[[SIZE=2]http://linmodems.technion.ac.il/[/SIZE]]("http://linmodems.technion.ac.il/")_[/COLOR][COLOR=#000000][SIZE=2] and can be found at [/SIZE][/COLOR][COLOR=#000080]_[[SIZE=2]http://linmodems.technion.ac.il/packages/[/SIZE]]("http://linmodems.technion.ac.il/packages/")_[/COLOR][COLOR=#000000][SIZE=2] you can use these but can also compile your own from the latest source files also found there.[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]If you intend compiling your own drivers then use Synaptic or Adept to ensure that you have all the necessary packages installed for compiling your drivers. This includes build-essential, linux-headers-ARCH (where ARCH is your kernel version  and can be found with uname -r in the terminal), fakeroot, module-assistant and debhelper.[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]Basically the sl-modem-source has to be installed first and then the sl-modem-daemon. The latest daemon also looks for ungrab-winmodem so download and install this from the linmodem website.[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]Please note that you may have to do this(recompile) after every update of your kernel if your modem stops working after an update.[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2][U][B]Method A:

[/B][/U][/SIZE][/COLOR][COLOR=#000000][SIZE=2]This method is the easiest and uses the latest packages from linmodems which are complete and contain all the files you may need.[/SIZE][/COLOR]
 [LIST=1]
[*][COLOR=#000000][SIZE=2]Determine 	you kernel version by typing uname -r in a terminal[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Go 	to [http://phep2.technion.ac.il/linmodems/packages/smartlink/Ubuntu/](http://phep2.technion.ac.il/linmodems/packages/smartlink/Ubuntu/) 	and download the latest package that has already been compiled for 	your kernel version i.e. [/SIZE][/COLOR][COLOR=#000080]_[[SIZE=2]slamr-2.6.20-16-generic.tar.gz 	[/SIZE]]("http://phep2.technion.ac.il/linmodems/packages/smartlink/Ubuntu/slamr-2.6.20-16-generic.tar.gz")_[/COLOR] 	
[*][COLOR=#000080][COLOR=#000000][SIZE=2]This 	package contains all the files you will need for installing the 	driver.[/SIZE][/COLOR][/COLOR]
[*][COLOR=#000000][SIZE=2]Copy 	the slamr-2.6.20-16-generic.tar.gz to your Desktop and right click 	on it and select “Extract here” and a folder wth a similar name 	will be created with the extracted files on your Desktop.[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Now 	rename the folder to an easier name such as “slmodem”[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Open 	a terminal and cd in to the slmodem folder[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]For 	details you can read the file 1st_Read.txt for more insight[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Type 	sudo ./setup and the install should start and complete successfully[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Type 	sudo modprobe ungrab_winmodem no results given shows success[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Type 	sudo modprobe slamr no results given shows success[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Type 	sudo /etc/init.d/sl-modem-daemon restart    to restart modem ot just 	reboot[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Type 	dmesg | grep slamr[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Use 	Kppp to query the modem on /dev/modem, if this works you are there! 	If you are not using Kubuntu then just see if it works from 	Gnome-ppp (wvdial must first be set up)[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]If not reboot first and check again.
[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Edit 	 /etc/default/sl-modem-daemon to change the line SLMODEMD_COUNTRY= 	USA to i.e SOUTHAFRICA or your country[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]If 	you do a Query modem in Kppp you will see that your country has 	changed[/SIZE][/COLOR]
[/LIST] [COLOR=#000080]_[]("http://ubuntuforums.org/#http://phep2.technion.ac.il/linmodems/packages/smartlink/")_[/COLOR]

 

 [COLOR=#000000][SIZE=2]_**Method B:**_[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]This is the ideal way if you feel stronly about using linux go to the linmodem sites shown above and download the latest .[/SIZE][/COLOR][COLOR=#000080]_[[SIZE=2]http://linmodems.technion.ac.il/packages/smartlink/slmodem-2.9.11-20070505.tar.gz[/SIZE]]("http://linmodems.technion.ac.il/packages/smartlink/slmodem-2.9.11-20070505.tar.gz")_[/COLOR][COLOR=#000000][SIZE=2] and  [/SIZE][/COLOR][COLOR=#000080]_[[SIZE=2]http://linmodems.technion.ac.il/packages/smartlink/ungrab-winmodem-20070505.tar.gz[/SIZE]]("http://linmodems.technion.ac.il/packages/smartlink/ungrab-winmodem-20070505.tar.gz")_[/COLOR][COLOR=#000000][SIZE=2]  and then the ubuntu file above [/SIZE][/COLOR][COLOR=#000080]_[[SIZE=2]http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/slamr-2.6.20-16-generic.tar.gz[/SIZE]]("http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/slamr-2.6.20-16-generic.tar.gz")_[/COLOR][COLOR=#000000][SIZE=2] that contains a working copy of the daemon. You can also try using Synaptic or adept to install sl-modem daemon and sl-modem-source as well as ungrab-winmodem(from linmodem website) as a dependancy from the repositories [/SIZE][/COLOR] 
 

 [LIST=1]
[*][COLOR=#000000][SIZE=2]Also 	download and install the ungrab-winmodem from the [/SIZE][/COLOR][COLOR=#000000][SIZE=2] 	linmodem website. Install with, extract, make, sudo make install.[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Download 	slmodem-2.9.11-20070505.tar.gz from the linmodem website. Install 	with extract, make, sudo make install.[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Download 	and open  slamr-2.6.20-16-generic.tar.gz. Extract and install the 	sl-modem-daemon xxx.deb file you find in there.[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Now 	go to /etc/default/sl-modem-daemon, right click, Action, Edit as 	Root, find the line SLMODEMD_COUNTRY=USA and change the USA to 	SOUTHAFRICA or your country name.[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Go 	to the konsole: [/SIZE][/COLOR] 	
[*][COLOR=#000000][SIZE=2]sudo 	 modprobe slamr[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]sudo 	 /etc/init.d/sl-modem-daemon  restart[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Now 	go to Kppp and select /dev/modem and use the Query Modem to test you 	modem. Now setup Kppp and go on line![/SIZE][/COLOR]
[/LIST] 

 [COLOR=#000000][SIZE=2]_**Note:**_[/SIZE][/COLOR][COLOR=#000000][SIZE=2] If you are going to use Kppp it is advisable that you check that the line noauth is not commented out with a # in  /etc/ppp/peers/kppp-options this may only be in older versions than Feisty.[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]To[/SIZE][/COLOR][COLOR=#000000][SIZE=2]** release a locked up Smartlink modem**[/SIZE][/COLOR][COLOR=#000000][SIZE=2] use  sudo modprobe ungrab-winmodem, then sudo modprobe slamr, then restart the daemon with sudo /etc/init.d/sl-modem-daemon restart. This may help you from rebooting.[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]_**Footnote:**_[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]There are packages in the Ubuntu Feisty repository that can be tried, but they may be outdated in reference to the kernel version. We actually need Marv's version as well as ungrab-winmodem to be put in the repos.[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]To remove any installation go to Synaptic, search for sl-modem, slmodem and  uninstall completely. Then use Krusader in root mode to search for sl-modem and slmodem. Double click on any found (except those in your repository or download folder) and right click for delete. Usually the date created should give you an indication. This clears all dreggs and leftovers of a previous installation that may be causing a problem with a new sl-modem install. Be very carefull before you delete anything in this way. Remember to reboot if you are picking up problems and also to re-extract a new folder of files if a compilation failed, as there are changes made during compilation that may cause issues if you just compile again with the failed one.[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]Final note:  when adding your init string i.e.  [/SIZE][/COLOR][COLOR=#000000][SIZE=3]Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 do not include W2 in the line for a Smartlink modem, only include to show connection speed for a Conexant modem![/SIZE][/COLOR]

---

### Post by deathspell on 2007-06-23
Thanks.. I'll try this now after a fresh install... But I don't have Kppp nor gnome-ppp in my Ubuntu.. I have kernel 2.6.20-15-generic

and the last time i tried to install wvdial, it gave me an error when i tried to compile it.. so in that case, what do i do after installing slamr-2.6.20-15-generic.tar.gz 

is there a precompiled version of wvdial too?

---

### Post by deathspell on 2007-06-23
Okay I installed the driver...


When I type wvdial, it says sending ATX, ATX OK, Modem initialized.. Does that mean I did everything correctly?

It says phone number, username and password is not specified.. I don't know where the configuration file is, to do that.. How do I go about doing that? also, I didn't understand from the instructions about changing the country.. where do I do that?

---

### Post by deathspell on 2007-06-23
/etc/wvdial.conf is read only.. there was no option to edit it as root

---

### Post by Matchless on 2007-06-23
See one of my ealier posts in setting up wvdial. You can edit wvdial 
[COLOR=#000000][SIZE=3]sudo gedit /etc/wvdial.conf
You should get it working now!!!!
[/SIZE][/COLOR]

---

### Post by deathspell on 2007-06-23
Okay... Its dialing now.. but there's a problem... I'm not getting connected to the internet properly.. This is what happens.. I wrote the following on a CD and am pasting it from windows..

Why is the connection dropping? And why is it asking for a login and password again? 

Its already specified in wvdial.conf

I typed the password, and nothing happens.. I tried again, and this time typed my ubuntu user password, still no luck.. I don't know what password its asking.. but it just seems to be stuck there...

Also the country is changed from USA to INDIA

death@Renderman:~$ wvdial
--> WvDial: Internet dialer version 1.56
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT172306
--> Waiting for carrier.
ATDT172306
CONNECT 44000
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT172306
--> Waiting for carrier.
Welcome to 3Com Total Control HiPer ARC (TM) Networks That Go The Distance (TM)
login: 
ATDT172306
Password:

---

### Post by deathspell on 2007-06-23
I used Carrier check = off and Stupid mode = on and this time it connects... but I can't access any websites or do anything on the internet..

---

### Post by Matchless on 2007-06-23
Hi it seems as if you are 99% there. Ok a silly question: Did you edit the WVdial exactly as to the example given in my earlier post? And did you change the county from its default as stated in method A point 15 of the howto? Have you tried to dial without waiting for dialtone - remember your modem is now defaulting to India and i do not know what country you are in and maybe the dialtone there is different.
The password requested by your ISP will only be the password they gave you to access them and is what you put in the wvdial file.
How are you running wvdial  - sudo wvdial or just wvdial?
If you still have a problem then I suggest you try and dial using pon and poff, but you will have to search a bit as to setting this up.
Thereafter all I can think is that you are being rejected by your ISP for some reason and you may have to google a bit.
Good luck.

---

### Post by Matchless on 2007-06-23
g resolved> **deathspell said:**
> I used Carrier check = off and Stupid mode = on and this time it connects... but I can't access any websites or do anything on the internet..

OK you are 99.999% there. This is usually coupled to DNS not being resolved. Make sure you have a file /etc/resolv with the DNS that your ISP gave you or use open dns. This file/folder is sometimes not created by default, so you can just do it and put the two dns ip's below each other and try to open your browser again.

---

### Post by deathspell on 2007-06-23
It worked. It was indeed a DNS issue but I wasn't sure since it was working fine in Windows. The DNS servers were supposed to be assigned automatically but I don't know why it didn't happen here. I'm now typing this message from Ubuntu. I finally made it! Thanks a lot guys!

And yeah, I was dialing as wvdial, not sudo wvdial.. Is there a difference between the two?

---

### Post by Matchless on 2007-06-23
Hi,
    Congratulations! Now you have one last commitment to make. You must help at least one newbie (or more) on this forum......I hereby commit.....

Enjoy Ubuntu and get the gnome-ppp dialer installed then have a look at Kubuntu.

---

### Post by deathspell on 2007-06-24
Will do :)

---

