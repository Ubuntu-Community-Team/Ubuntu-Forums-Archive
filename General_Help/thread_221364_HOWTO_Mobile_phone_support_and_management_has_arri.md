---
title: "HOWTO: Mobile phone support and management has arrived! (CDMA)"
date: 2006-07-23
forum: General Help
---

### Post by fragmented_user on 2006-07-23
Mobile phone support has arrived, in the form of a 13 MB download that includes Serial to USB support and documentation, and information about using your phone via Bluetooth or for Dial up networking. 

What the download pretty much includes, is a script that does the right things, and a couple of html files that provide you with information regarding connecting to your mobile phone.

The file also includes a mobile phone data and media management application(s). You can use the phone management applications to sync your contacts, music, ringers, calendar events, videos, and more.

EDIT: To see release notes and download the full package, visit the following URL [http://ubuntuforums.org/showpost.php?p=1309647&postcount=18](http://ubuntuforums.org/showpost.php?p=1309647&postcount=18)

---

### Post by fragmented_user on 2006-07-23
The setup.sh script includes the URL of a bitpim version that is cofirmed to work with ubuntu.

Although, It turns out, there is a bitpim *.deb package in the debian repositories; I just didnt see it right away. 

[http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=bitpim](http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=bitpim)
This package is know to be problemtic with some versions of ubuntu



If you would like to do other cool stuff with your phone, you can check out some other programs and see if you find anything you like. [http://tuxmobil.org/debian_linux_phones.html](http://tuxmobil.org/debian_linux_phones.html) If you do test and enjoy using one of the programs listed at the above URL, please tell us which program it was, so that others can try the program as well.

---

### Post by twotonz on 2006-07-23
Hallo fragmented_user,
You have got my heart beating fast :) 
I have "moto" here, which is quite difficult to connect to a pc, unless one is running windows & the 50,-€ phone-tools software direct from M. I think this has to do with company policy (I shall choose a better company next time). Anyway, I am gonna check out the stuff you have put here. 
Thanks a lot, for this one, I shall let you know how I got on.

Love & Peace (to all)
anthony

---

### Post by ketsugi on 2006-07-23
Wait, so BitPIM is CDMA only?

Dangnabbit.

---

### Post by foxy123 on 2006-07-23
is there any list of phones which work with this package. I have not seen it in README. I mostly interesting in syncing files and contacts. Thanks.

---

### Post by fragmented_user on 2006-07-23
[QUOTE=twotonz]I have "moto" here, which is quite difficult to connect to a pc, unless one is running windows & the 50,-€ phone-tools software direct from M. I think this has to do with company policy (I shall choose a better company next time). Anyway, I am gonna check out the stuff you have put here.[/QUOTE]

Not sure if moto will work with this. (BitPim does support some motorolas) You can try the following links, and please report your findings.
[http://sourceforge.net/projects/moto4lin/](http://sourceforge.net/projects/moto4lin/)
[http://developer.berlios.de/projects/kmobiletools/](http://developer.berlios.de/projects/kmobiletools/)

[QUOTE=ketsugi]Wait, so BitPIM is CDMA only?[/QUOTE]

[QUOTE=foxy123 ]is there any list of phones which work with this package. I have not seen it in README. I mostly interesting in syncing files and contacts. Thanks.
[/QUOTE]


Right now, to the best of my knowledge, the script I wrote is limited to 5 kinds of phones.
1)All LG phones, using Straight USB Cables
2)All Samsung phones, 
3)All Sanyo phones
4)Some OEM USB to serial cables --
FTDI USB to serial chip is used in some cables 	
5)FutureDial USB to serial --
Prolific PL2303 is used in all FutureDial USB to serial cables.

It is limited to these because it is all I have information for (PID/VID) see 
Linux-ISSUES
[http://www.bitpim.org/help/trouble-linux-issues.htm](http://www.bitpim.org/help/trouble-linux-issues.htm)

and Vendor/Product IDs
[http://www.bitpim.org/help/ref-usbids.htm](http://www.bitpim.org/help/ref-usbids.htm)

[QUOTE=http://www.bitpim.org/help/phones-other.htm]BitPim is intended to support multiple phones, but the main authors only have a limited subset of phones. Support for other phones depends on others contributing.

I believe that most recent CDMA phones will work for the filesystem view, but none of the other features will. [/QUOTE]

I do not know whether BitPim and/or the udev access enabling script are limited to CDMA phones. It is simply what I assumed. People should try out their GSM or other non CDMA phones and see if it works. If it doesnt work dont try to force it to , just report your findings here so that others will know which phones dont work, and will perhaps find a fix. Those of you who were lucky enough to have this package work for you should post your phones model number along with information about how you got your phone to work.(which install file did you use? ie install_LG, did you need to do any extra tweaking?)

BitPim itself will support any of the following phones listed at the following URL [http://www.bitpim.org/help/phones.htm](http://www.bitpim.org/help/phones.htm). Even if your phone is not listed there, you still may be able to access your phones file system and modify the contents (at your own risk of course).

---

### Post by fragmented_user on 2006-07-23
OK, I'll be the first one. 

Phone Model: LG VX8300
Current Status: Works
Status Description: use the install_LG script. reboot the computer. works immediately after.

---

### Post by twotonz on 2006-07-24
Hi all,
Ok, I have checked out all these wonderfull links, and d/l'ed a few things.
Firstly looking at the devices supported by bitpim, v220 is there, and should work. Another possibility I found and looks quite attractive is  moto4lin.

So first thing is to get bitpim installed, and here I have my first hurdle....in my package list I have only python-support 0.1, apparently bitpim needs version>0.2 I have read that python-support is also in the gimp-python packet, funny, after checking out what I have here installed, I see that gimp-python is allready installed. So why is bitpim breaking at "cannot find python-support"? Any ideas anybody?

Thought I would then have a go at moto4lin. This packet depends on p2kmoto.
Ohoh, again a big list of stuff that is missing, among others, aclocal & automake. Automake is there under /usr/bin as the version 1.9, so I do not quite understand how come p2kmoto is not finding it.

Now to a few positive developments. I now have a device called /dev/ttyACM0 which was not present yesterday. When running "Phone Manager"  instead of errors, I now get "Connected", still cannot send sms's though.
With "Kmobile-Tools" a bit more success, it is showing signal strenth, & batterie status, yipee. I shall now fiddle around a bit more, and give another report later this evening.

Thanks again to fragmented_user for the inspiration. Looks like I shall be striking another device off my problem-list!

Love & Peace (to all)
anthony

---

### Post by foxy123 on 2006-07-24
> **twotonz said:**
> Thought I would then have a go at moto4lin. This packet depends on p2kmoto.
Ohoh, again a big list of stuff that is missing, among others, aclocal & automake. Automake is there under /usr/bin as the version 1.9, so I do not quite understand how come p2kmoto is not finding it.

try other versions of automake. sometimes you need to downgrade it to make it work with some source codes.

---

### Post by fragmented_user on 2006-07-24
Hi twotonz,

I'm working on getting a version of bitpim that is confirmed to work perfectly or almost perfectly, into an ubuntu repository (offers welcomed). the package is now hosted on my site. [http://www.vibrantdesign.swizi.com/mobile](http://www.vibrantdesign.swizi.com/mobile). If you run into problems installing bitpim with that deb, or just want desktop icons for bitpim, then you should run the bash script (setup.sh) included in the tar.gz file attached to the following post. 
[http://ubuntuforums.org/showpost.php?p=1309647&postcount=18](http://ubuntuforums.org/showpost.php?p=1309647&postcount=18)

EDIT: I removed the package from my site since bitpim is now offered in the Universe repositories if I am not mistaken.

---

### Post by twotonz on 2006-07-24
Hidihi again,
 Naja, "Bitpim" is installed, just don't ask me how :oops: Whilst trying to compile the packet, as I said before, I was getting a whole load of errors, so I cannot figure out how come it is now sitting in the menu. Am I correct in assuming that "bitpim" is responsible for setting up the /dev/ttyACMO?

 KMobileTools is a right result! I can browse my Telephone Nr's and send SMS's (the SMS'es must first be saved, and then sent, somehow sending directly does not work) from the PC. This is all I was looking for, so I am very pleased so far. 

 Sooo, considering that this thread is dealling with fragmented-user's great efforts, enough of "kmobiletools". I figured that as "bitpim" was obviously installed, I could have a go with frag's scripts. I thought that the generic_OEM_USB script was the right one to use. Firstly I had to make it executable as only the install_LG script was runnable. So that done, and rubbing my hands in anticipation, fired it up.....
```

tonyd@redrum:~/hotplug$ ./install_OEM_USB
This script will configure your computer to recognize your OEM_USB mobile phone
(via udev hotplug).

Authenticating User

Enable Phone Hotplugging

„/home/tonyd/hotplug/.install_files/OEM_USB/60-cell.rules“ -> „/etc/udev/rules.d/60-cell.rules“

./install_OEM_USB: line 22: unexpected EOF while looking for matching `"'
./install_OEM_USB: line 25: syntax error: unexpected end of file
tonyd@redrum:~/hotplug$
```

and that was the output that I am getting. While we are on this subject, firstly I was trying sudo ./generic_oem_usb and was getting "password incorrect" errors, so in case anybody is having authentification troubles just run the script without the sudo, the script will then automatically ask you for the sudo password. Anyway back to my errors, I have looked at the script with texteditor and line 22 is.....
echo "Reboot your computer to finalize the installation"
and line 25 does not exist, which could explain the unexpected end of file thing. So, fragmented-user, any idea's, I am afraid I am no Linux-Guru, and without a pointer here I am stuck.
 I know for a fact that there are very many v220 users that would premote you to guru-status if you manage to figure it out.

Love and Peace (to all)
anthony

EDIT**********
Oh, and thanks to foxy123 for the tip, but I think that unless I can get the hotplug scripts to work I shall stick with mobiletools, both proggys do the same thing I think.

---

### Post by foxy123 on 2006-07-24
btw I had no problem with connecting my wife's v220 via moto4lin.

---

### Post by fragmented_user on 2006-07-25
Hi. 

Thanks for taking the time to report the bugs.

> **twotonz said:**
> Hidihi again,
. Am I correct in assuming that "bitpim" is responsible for setting up the /dev/ttyACMO? 

/dev/ttyACMO is the port for your cell phones dial up modem

EDIT:I don't think Bitpim is responsible for setting up   /dev/ttyACMO.
I think your computer will automatically do that.

```

tonyd@redrum:~/hotplug$ ./install_OEM_USB
This script will configure your computer to recognize your OEM_USB mobile phone
(via udev hotplug).

Authenticating User

Enable Phone Hotplugging

„/home/tonyd/hotplug/.install_files/OEM_USB/60-cell.rules“ -> „/etc/udev/rules.d/60-cell.rules“

./install_OEM_USB: line 22: unexpected EOF while looking for matching `"'
./install_OEM_USB: line 25: syntax error: unexpected end of file
tonyd@redrum:~/hotplug$
```"

The file seems to have beens installed. If you reboot your computer and from the command line enter "sudo bitpim" bitpim should recognize your phone. I am working on getting this fixed so that you do not have to do sudo for bitpim to recognize your phone. 

I have attached a new version of the install package that fixes a few of the errors, and includes improved error handling.

However, be mindful of the following two things.
1. as you have noticed, it is not neccessary to type sudo
2. if there is a file name in your path that contains a space (ie."My
Documents") the script may not work correctly. fix this problem by temporarily replacing the spaces with "_" (underscore) or executing the script from a directory who's path contains no spaces.  

try installing again using the new package I have attached.

> I am afraid I am no Linux-Guru, and without a pointer here I am stuck.
 I know for a fact that there are very many v220 users that would premote you to guru-status if you manage to figure it out."

hehe. tempting thought. not really looking for fame though. :neutral:  I Promise 8).


--Joseph

---

### Post by JSVH on 2006-07-26
This is great! I tried to get my phone to sync a month or so ago. No luck. After I get moved and relocate my USB cable I will get out my phone and try to help.

-John

---

### Post by Blobba on 2006-07-27
Hi

Is it possible to connect a 3G phona and use it as a modem?

My father lives far away from all good internet connections :) and a 3G phone at 384k/sec would do just fine for him...

// Blobba

---

### Post by twotonz on 2006-07-27
Hallo fragmented_user,
 I have just grabed the new script, & will give it a spin. One thing that I had noticed though, is that the "install_oem_usb" script is meant for handy's using a special usb->serial->usb cable. I am using a normal usb cable, maybee I should try another script, what do you think?
 I was in the same position as JSVH, I had also tried a few months ago, to connect the handy with pc, after much reading & experimenting I had to give up. So despite your modisty, you are allready my hero, grovel, grovel. Anyway thanks again for all your efforts, it is much appreciated.
 Sooo, I shall post again later this evening, & let you know what has happened.

Love & Peace (to all)
anthony

---

### Post by twotonz on 2006-07-28
Hallo again,
OK, it looks like the script now runs fine, now I see that bitpim has dissapeared again, so I shall be looking into that today, what was that about downgrading?...........

Love & Peace
anthony

---

### Post by fragmented_user on 2006-07-28
EDIT: Second version is now available at the following URL:[http://ubuntuforums.org/showpost.php?p=1317977&postcount=24](http://ubuntuforums.org/showpost.php?p=1317977&postcount=24)

First Official Release.

And now, the moment you've all been waiting for. I present you: The first release of Mobile-Phones-on-Linux.  The package is available as a *.tar.gz download attached below. 

Release Goals

This release focuses on getting a basic package out in the open, so that people can actually start managing their phones on linux. Its primary functions are to enable Hotplugging for your mobile device, and to install the excellent BitPim phone manager.[http://wwww.bitpim.org](http://wwww.bitpim.org) which will allow you to do such things as sync contacts and edit ringers.

Project Naming

Finally,in line with the established tradition of giving incredibly funky names to incredibly useful products, I hereby name this project MoPOL(Mobile Phones on Linux)

Bug Reports

Report all bugs you find, in this thread. 

Trouble-shooting

Tip 1: If you have a different version of BitPim installed, it might help to remove it before executing the "bitpim" script. ```
sudo apt-get remove bitpim
```

Licensing

BitPim is the intellectual property of its original authors. Everything else is being distributed under the GNU-GPL license.

README - Full text of included README document provided below for your convenience.


[HTML]
   __  ___     __   _ __      ___  __                   
  /  |/  /__  / /  (_) /__   / _ \/ /  ___  ___  ___ ___
 / /|_/ / _ \/ _ \/ / / -_) / ___/ _ \/ _ \/ _ \/ -_|_-<
/_/  /_/\___/_.__/_/_/\__/ /_/  /_//_/\___/_//_/\__/___/
              __   _               
 ___  ___    / /  (_)__  __ ____ __
/ _ \/ _ \  / /__/ / _ \/ // /\ \ /
\___/_//_/ /____/_/_//_/\_,_//_\_\                    

>

Setup Hot-plugging for, and manage contacts and media on CDMA phones 

PURPOSE

to enable import/export support for USB to serial mobile phone cables and mobile phones
 in Dapper Drake - 6.06 LTS - Ubuntu Linux (Debian based).
This script assumes that you use udev for hotplugging (like Dapper does). If this is not
 the case please visit http://www.bitpim.org/help/howto-linuxusb.htm or open the following
 file with your webbrowser hotplug/documentation/howto-linuxusb.htm.

HOW ITS DONE

Importing and exporting to the phone is accomplished using a program called Bitpim 
(http://www.bitpim.org)

WHAT ABOUT DIAL-UP NETWORKING?

To the best of my knowledge, you do not need to execute any of these scripts in order to 
use your phone as a dial-up modem. In many cases the phone will be automatically recognized 
as a modem and will be accessible at the /dev/ttyACM0 port. You can even use the built in
 Network manager (System>>Administration>>Networking) or (user@domain$ gksu network-admin)
 to configure your dial-up connection.

BUT, I USE BLUE TOOTH

If you use blue tooth and you have already successfuly established a bluetooth connection
 between your phone and your computer, then you can probably skip ahead to part 2. SETUP
 THE BITPIM PHONE MANAGER.u

If you have not yet successfully configured your bluetooth connection, I recommend that you 
first purchase a bluetooth dongle (a device that plugs into your computers usb port.). Make
 sure you buy a dongle tha is compatible with linux (search http://linuxcompatible.org/ or 
http://www.linuxquestions.org/hcl/) 

Next, you will need to setup a bluetooth connection on your computer. I personally do not 
know how to do this, but apparently other people do. Here is a great example of a tutorial 
that someone wrote to help you configure your blue tooth:
 http://www.ubuntuforums.org/showthread.php?t=75978. If you still are unable to setup your
 blue tooth using that tutorial, try searching http://www.ubuntuforums.org or 
http://www.linuxquestions.org for more info on setting up bluetooth.
 example query: bluetooth phone.

WHATS INCLUDED

Included in this archive (in the "install_files" folder) are five configuration files, one 
for each kind of phone supported (LG,Sanyo,Samsung,OEM_USB,FutureDial). There are also five 
installation scripts, one for each kind of phone. And lastly, there is one Bitpim Setup
 script for downloading and installing the BitPim, data and media management program.

All right then. Lets get started.

1. ENABLE PHONE HOTPLUGGING
open up an terminal of your choice (xterm/gterm/aterm)
change to the directory in which you unpacked the archive.
change to the "hotplug" directory and list the files. (user@domain$ cd hotplug;ls)
execute the bash script with the name that best corresponds to your phone model. This is 
done by placing "./" directly infron of the install scripts name and pressing enter.

TIP: Do not use sudo. The script will automatically request the root password.

For example: If I own an LG VX8300 phone, then I need to do the following:

I look for a file with the name LG in it, since LG is my manufacturer. I find that there is a
 file called "install_LG", so I execute the "install_ LG" script by typing "./install_LG" in
 the terminal. if I am not logged in as root, the script will request my root password.
Following authentication, the script will finish executing, output some text and exit.
I will then need to reboot my computer in order for changes to take affect.

Once I have rebooted my computer I will be able to access all my contacts, calendar events,
 pictures, ringers, music, and more, by installing bitpim and setting up my phone.

2. SETUP THE BITPIM PHONE MANAGER

open up an terminal of your choice (xterm/gterm/aterm)
change to the directory in which you unpacked the archive.
change to the "bitpim" directory (user@domain$ cd bitpim)
 install bitpim by executing the "install_bitpim" script (user@domain$ .\install_bitpim)
Enter the root password when prompted.
 
This script utilizes the gdebi-gtk Package-Installer (a graphical front-end for installing 
packages). When the Package-Installer program opens, click the "Install Package", "Reinstall 
Package" or "Upgrade Package" button in the upper right hand corner of the window. Once the 
program has finished installing, close the "Package-Installer". If everything is done
 correctly you will see "BitPim Setup Completed" displayed in the terminal.

3. CONFIGURE YOUR PHONE 

Start "Bitpim Detect Phone"  by either clicking the "Bitpim" shortcut on your desktop or by 
opening a terminal and typing "bitpim" and pressing enter. Bitpim should automatically detect
 your phone upon loading. If your phone is not automatically detected(mine was detected as 
being located on the "usb::001::004::2" port), you can either select "Edit>Detect Phone" or 
"Edit>Settings" from the top-level menu in BitPim.

Thats' it. Congratulations. Your phone should now be able to edit and manage your phones'
 data and media using Bitpim. 

For further trouble-shooting please visit "http://www.bitpim.org/help"

Credits:
The bitpim program itself is the the product of bitpim programmers and engineers. This script
 is the product of my spending a few hours writing, organizing, and compiling. The configuration
 files referenced in the hotplug scripts were built using information from the following URLS
(1) http://www.bitpim.org/help/ref-usbids.htm (included in hotplug/documentation)
(2) http://www.bitpim.org/help/howto-linuxusb.htm (included in hotplug/documentation)

The BitPim Setup script was built using information from the following URL
(1) http://www.bitpim.org/help/trouble-linux-issues.htm (included in bitpim/documentation)


About the author:
The author's name is Joseph. He is a freelance artist and Linux enthusiast/amateur programmer.
 He can be reached for criticism, comments, and/or suggestions at 
<yharrow[at]yahoo.com>
[/HTML]

---

### Post by fragmented_user on 2006-07-28
> **twotonz said:**
> Hallo again,
OK, it looks like the script now runs fine, now I see that bitpim has dissapeared again, so I shall be looking into that today, what was that about downgrading?...........

Love & Peace
anthony

I recommend downloading the full package and executing the bitpim script. I am not sure what you mean by downgrading.

---

### Post by fragmented_user on 2006-07-28
> **Blobba said:**
> Hi

Is it possible to connect a 3G phona and use it as a modem?

My father lives far away from all good internet connections :) and a 3G phone at 384k/sec would do just fine for him...

// Blobba

Excerpt from README file.

> 
WHAT ABOUT DIAL-UP NETWORKING?

To the best of my knowledge, you do not need to execute any of these scripts in order to 
use your phone as a dial-up modem. In many cases the phone will be automatically recognized 
as a modem and will be accessible at the /dev/ttyACM0 port. You can even use the built in
 Network manager (System>>Administration>>Networking) or (user@domain$ gksu network-admin)
 to configure your dial-up connection.

 If you require more control over your Dial Up Network or if Network manager is not working for you, you can try Kpp (requires KDE base)

As for "3G" speed, that is all dependent upon your phone and service provider.

---

### Post by twotonz on 2006-07-29
hallo again,
#fragmented_user
> I am not sure what you mean by downgrading.
sorry, my twisted humour, it was a reference to foxy123's tip to downgrade the python in order to get bitpim installed. I have now moved over to another of my pc's and decided to start again on a fresh dapper. Kmobiletools still work, but  maybee it is getting in the way. Anyway this pc has hardly anything installed (software-wise) so I think I shall have better luck. I have just grabbed the complete tar from your site, I have just gotta play with the xbox for a few hours first though :rolleyes: 

Love & Peace (to all)
anthony

---

### Post by freshanointing on 2006-07-29
How come your wife can sync here motorola contacts with linux?  I've looked up in google but no luck.  Please let me know how to do it!  Thanks!

---

### Post by FurryNemesis on 2006-07-30
Has anyone tested this lovely-looking script with Nokia Nseries phones (Specifically N70)?

Ok,Nokia phones don't seem to be supported. My mistake.

---

### Post by fragmented_user on 2006-07-30
MoPOL (Mobile Phones on Linux) Version 0.0.2

Change Log 

*Combined Hotplugging and "BitPim Install" script. 
*Improved UI.
*Updated README
*Included additional Documentation.



README - Full text of included README document provided below for your convenience.

[HTML]

   __  ___     __   _ __      ___  __                   
  /  |/  /__  / /  (_) /__   / _ \/ /  ___  ___  ___ ___
 / /|_/ / _ \/ _ \/ / / -_) / ___/ _ \/ _ \/ _ \/ -_|_-<
/_/  /_/\___/_.__/_/_/\__/ /_/  /_//_/\___/_//_/\__/___/
              __   _               
 ___  ___    / /  (_)__  __ ____ __
/ _ \/ _ \  / /__/ / _ \/ // /\ \ /
\___/_//_/ /____/_/_//_/\_,_//_\_\  

>

Version 0.0.2                  


PROJECT AIM

To enable anyone to Setup Hot-plugging for, and manage contacts and media on their CDMA 
Mobile phones.


WHAT'S INCLUDED

Included in this archive (in the "install_files" folder) are five configuration files, one 
for each kind of phone supported (LG,Sanyo,Samsung,OEM_USB,FutureDial) and one Setup
script that you can use to configures phone hot-plugging and/or download and install BitPim.

HOW ITS DONE

Phone hot-plugging is enabled by copying a udev entry file "60-cell.rules" into the 
/etc/udev/rules.d/ directory.

Importing and exporting to the phone is accomplished using a program called Bitpim 
(http://www.bitpim.org)


WHAT ABOUT DIAL-UP NETWORKING?

To the best of my knowledge, you do not need to execute any of these scripts in order to 
use your phone as a dial-up modem. In many cases the phone will be automatically recognized 
as a modem and will be accessible at the /dev/ttyACM0 port. You can even use the built in
Network manager (System>>Administration>>Networking) or (user@domain$ gksu network-admin)
to configure your dial-up connection. If you require more control over your Dial Up Network
 or if Network manager is not working for you, try Kppp (requires KDE base).



Credits:
The bitpim program itself is the the product of bitpim programmers and engineers. This script
is the product of my spending a few hours writing, organizing, and compiling. The configuration
files referenced in the hot-plug scripts were built using information from the following URLS
(1) http://www.bitpim.org/help/ref-usbids.htm (included in /documentation)
(2) http://www.bitpim.org/help/howto-linuxusb.htm (included /documentation)

The BitPim Setup script was built using information from the following URL
(1) http://www.bitpim.org/help/trouble-linux-issues.htm (included in /documentation)


About the author:
The author's name is Joseph. He is a freelance artist and Linux enthusiast/amateur programmer.
He can be reached for criticism, comments, and/or suggestions at 
<yharrow[at]yahoo.com>

 [/HTML]

INSTALL - Full text of included INSTALL document provided below for your convenience.

[HTML]

Version 0.0.2                 

SYSTEM REQUIREMENTS 

Required:

Debian based Operating system with support for Udev hot-plugging
USB port and/or blue-tooth dongle

Recommended:

CDMA Mobile Phone
Serial to USB cable for Mobile Phone

Tips:

If you do not use udev hot-plugging and are still interested in gaining access to your
 phone, visit http://www.bitpim.org/help/howto-linuxusb.htm or open the following
included file with your web-browser /documentation/howto-linuxusb.htm.


USING BLUETOOTH

If you use blue tooth and you have already successfully established a blue-tooth connection
between your phone and your computer, then you can probably skip ahead to part 2. -
INSTALL BITPIM

If you have not yet successfully configured your blue-tooth connection, I recommend that you 
first purchase a blue-tooth dongle (a device that plugs into your computers usb port.). Make
sure you buy a dongle that is compatible with linux (search http://linuxcompatible.org/ or 
http://www.linuxquestions.org/hcl/) 

Next, you will need to setup a blue-tooth connection on your computer. I personally do not 
know how to do this, but apparently other people do. Here is a great example of a tutorial 
that someone wrote to help you configure your blue tooth:
http://www.ubuntuforums.org/showthread.php?t=75978 . If you still are unable to setup your
blue tooth using that tutorial, try searching http://www.ubuntuforums.org or 
http://www.linuxquestions.org for more info on setting up blue-tooth.
example query: bluetooth phone.

HOW LONG WILL THIS TAKE?

Installation time can take anywhere from 1 minute to 30 minutes. it really depends on whether
or not you choose to install BitPim, and what your connection speed is (The BitPim file is 
approximately 13 Megabytes in size) Although, the actual install procedure consists of just three easy
steps.
 
All right then. Lets get started.


BEGIN SETUP
	
open up an terminal of your choice (xterm/aterm/gnome-terminal)
change to the directory in which you unpacked the archive.
execute the "setup.sh" bash script. (user@domain$ ./setup.sh)
Do not use sudo. The script will automatically request the root password. 

Choose an option from the main menu

	-Partial Install-
	1 - Setup Hot-plugging for your mobile phone
	2 - Install the BitPim Phone management application

	-Full Install-
	3 - Setup Hot-plugging and Install BitPim.

	4 - Display README

	0 - Exit Setup

1. SETUP HOT-PLUGGING

You will be requested to choose a phone to provide udev hot-plug support for. 
Choose a phone based upon the following table: 

OEM USB.................................Some OEM USB to serial cables
					FTDI USB to serial chip is used in some cables 

Future Dial.............................FutureDial USB to serial
					Prolific PL2303 is used in all FutureDial USB to serial cables.

LG......................................LG - All straight USB
					
Samsung.................................Samsung - All USB 

Sanyo...................................Sanyo - All USB 

Reboot your computer for hot-plug changes to take effect. 

2. INSTALL BITPIM

This script utilizes the gdebi-gtk Package-Installer (a graphical front-end for installing 
packages). When the Package-Installer program opens, click the "Install Package", "Reinstall 
Package" or "Upgrade Package" button in the upper right hand corner of the window. Once the 
program has finished installing, close the "Package-Installer". If everything is done
correctly you will see "BitPim Setup Completed" displayed in the terminal.

3. CONFIGURE YOUR PHONE 

Start "Bitpim"  by either clicking the "Bitpim" shortcut on your desktop or by 
opening a terminal, typing "bitpim" and pressing enter. Bitpim should automatically detect
your phone upon loading. If your phone is not automatically detected (mine was detected as 
being located on the "usb::001::004::2" port), you can either select "Edit>Detect Phone" or 
"Edit>Settings" from the top-level menu in BitPim.

That's it. Congratulations. Your phone should now be able to edit and manage your phones'
data and media using Bitpim. 

For further trouble-shooting please read the README file or  visit "http://www.bitpim.org/help"



[/HTML]

---

### Post by fragmented_user on 2006-07-30
> **FurryNemesis said:**
> Has anyone tested this lovely-looking script with Nokia Nseries phones (Specifically N70)?

Ok,Nokia phones don't seem to be supported. My mistake.


Nokia support has just been added (via gnokii and gnocky), but not released yet. Motorola support coming soon. Hang in there people. I am trying my best with the time I have. :)

PS. To add nokia support yourself, do the following:
sudo apt-get install gnokii

go to [http://rpm.pbone.net/index.php3/stat/4/idpl/1653834/com/gnocky-0.0.3-2.i386.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/1653834/com/gnocky-0.0.3-2.i386.rpm.html)
and download the Gnocky RPM

convert it to deb with alien.
sudo alien -i "RPM file goes here" /home/Desktop

that above command should install gnocky as well

If alien returns "command not found" install alien using the following command: sudo apt-get install alien. 

-Joseph

---

### Post by twotonz on 2006-08-01
Hallo Fragmented_user,
Ok, firstly the installer is much nicer, thanks. Still having problems though. Firstly in the install instructions maybee you should add a line....
> open up an terminal of your choice (xterm/aterm/gnome-terminal)
change to the directory in which you unpacked the archive.
my suggestion.......
Make the setup file executable by running
```
chmod a+rx setup.sh
``` 

Secondly I am still getting errors whilst tring to run Bitpim.......
> Traceback (most recent call last):
  File "/opt/cx_Freeze-3.0.2/initscripts/ConsoleSetLibPath.py", line 30, in ?
  File "src/bp.py", line 90, in ?
  File "src/gui.py", line 30, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", li ne 42, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in ?
  File "ExtensionLoader.py", line 12, in ?
ImportError: libtiff.so.3: cannot open shared object file: No such file or direc tory
As the installer was running I had noticed that there were a few errors concerning not enough privlages to set system links.
Keep up the good work
Love & Peace (to all)
anthony

---

### Post by fragmented_user on 2006-08-01
> **twotonz said:**
> Hallo Fragmented_user,
Ok, firstly the installer is much nicer, thanks. Still having problems though. Firstly in the install instructions maybee you should add a line....

my suggestion.......
Make the setup file executable by running
```
chmod a+rx setup.sh
``` 

Secondly I am still getting errors whilst tring to run Bitpim.......

As the installer was running I had noticed that there were a few errors concerning not enough privlages to set system links.
Keep up the good work
Love & Peace (to all)
anthony

Hi, thanks for taking the time to report this error.

It seems that like you suggested, there is a problem with permissions.
If this is the case, running "sudo bitpim" should not return any errors.
Please enter "sudo bitpim" into the terminal, and report any errors you encounter.

In the future, setup.sh will be made executable before it is included in the package.
However, I will include your suggestion to "chmod" setup.sh in the "Trouble-shooting"
section of the documentation.
 
P.S. I appreciate your compliments. :)

Best Regards,
Joseph.

---

### Post by twotonz on 2006-08-02
Hidihi,
Okey doky, done that (sudo bitpim), still getting those errors......
Traceback (most recent call last):
  File "/opt/cx_Freeze-3.0.2/initscripts/ConsoleSetLibPath.py", line 30, in ?
  File "src/bp.py", line 90, in ?
  File "src/gui.py", line 30, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in ?
  File "ExtensionLoader.py", line 12, in ?
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory

libtiff.so.3, was one of the data that couldn't set the symbolic link, what command do I have to enter to set the symbolic links manually? (sorry if this was a dumb question)

Love & Peace (to all)
anthony

---

### Post by fragmented_user on 2006-08-02
> **twotonz said:**
> Hidihi,
Okey doky, done that (sudo bitpim), still getting those errors......
Traceback (most recent call last):
  File "/opt/cx_Freeze-3.0.2/initscripts/ConsoleSetLibPath.py", line 30, in ?
  File "src/bp.py", line 90, in ?
  File "src/gui.py", line 30, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in ?
  File "ExtensionLoader.py", line 12, in ?
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory

libtiff.so.3, was one of the data that couldn't set the symbolic link, what command do I have to enter to set the symbolic links manually? (sorry if this was a dumb question)

Love & Peace (to all)
anthony

Hi. sounds like you need to open a terminal and type the following:

cd /usr/lib
sudo ln -s libtiff.so.4 libtiff.so.3
sudo ln -s libtiff.so.4.1.4 libtiff.so.3
 
This problem will probably be fixed in the next version.

-Joseph

---

### Post by OffHand on 2006-08-03
I get this error when I try to run bitpim:

$ bitpim
Traceback (most recent call last):
  File "/opt/cx_Freeze-3.0.2/initscripts/ConsoleSetLibPath.py", line 30, in ?
  File "src/bp.py", line 90, in ?
  File "src/gui.py", line 30, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in ?
  File "ExtensionLoader.py", line 12, in ?
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory


Does anyone know how to fix this?

EDIT: 

cd /usr/lib
ln -s libtiff.so.4 libtiff.so.3

fixed this issue.

Bummer... my phone isn't recognized  :( I got a Samsung D600

---

### Post by OffHand on 2006-08-03
Two Screenshots

This is what is in my /etc/udev/rules.d/60-cell.rules :

#udev entry
#Manufacturer: Samsung
#Models: All USB cables
#Vendor ID: 0x04e8
#Product ID: 0x6601

SUBSYSTEM!="usb_device", ACTION!="add", GOTO="cell_rules_end"
SYSFS{idVendor}=="0x04e8", SYSFS{idProduct}=="0x6601", MODE="0666"
LABEL="cell_rules_end"

---

### Post by fragmented_user on 2006-08-03
> **subsonic_shadow said:**
> Two Screenshots

This is what is in my /etc/udev/rules.d/60-cell.rules :

#udev entry
#Manufacturer: Samsung
#Models: All USB cables
#Vendor ID: 0x04e8
#Product ID: 0x6601

SUBSYSTEM!="usb_device", ACTION!="add", GOTO="cell_rules_end"
SYSFS{idVendor}=="0x04e8", SYSFS{idProduct}=="0x6601", MODE="0666"
LABEL="cell_rules_end"


You're phone is probably recognized by your computer via udev. However, bitpim does not support your phone model "Samsung D600".

TODO: Integrate better Samsung support options, into MOPOL package.

---

### Post by OffHand on 2006-08-03
> **fragmented_user said:**
> You're phone is probably recognized by your computer via udev. However, bitpim does not support your phone model "Samsung D600".

TODO: Integrate better Samsung support options, into MOPOL package.

Alright, thnx for your reply. Too bad it doesn't work with my phone.

---

### Post by fragmented_user on 2006-08-03
[QUOTE=subsonic_shadow]
Alright, thnx for your reply. Too bad it doesn't work with my phone.

[/QUOTE]Hey whatsup.

Today must be your lucky day. I ran across something just now that works with
your phone located here: [http://sourceforge.net/projects/comsams](http://sourceforge.net/projects/comsams),
 Unfortunately though, if you are not able to find a deb, you will have to 
complile the program from source. Not a big deal, but possibly time 
consuming. 

Anyhow, let me know how it all works out. If you feel lost, or are just 
looking for more options regarding programs for Samsung phones, you can check
 out this web page: [http://tuxmobil.org/phones_survey_samsung.html](http://tuxmobil.org/phones_survey_samsung.html)
 
Regards, Joseph

---

### Post by OffHand on 2006-08-03
I have installed comsams but when I try to connect I het this error:

 comsams -i
Cannot open port, connection failed!
Try to connect to phone...
write() of 4 bytes failed!
No Connection, waiting for phone ready...
Try to connect to phone...
write() of 4 bytes failed!
No Connection, waiting for phone ready...
Try to connect to phone...
write() of 4 bytes failed!
No Connection, waiting for phone ready...
Try to connect to phone...
write() of 4 bytes failed!
No Connection, waiting for phone ready...
Try to connect to phone...
write() of 4 bytes failed!
No Connection, waiting for phone ready...
Tried to connect 5 times. (timeout)


Is there any way to find out why it cannot connect?

---

### Post by twotonz on 2006-08-04
Hidihi,
Ok, bitpim running after also changing into the dir /usr/lib, and then setting the symbolic-link. I am also not getting the handy recognised, :sad:  . the device is listed as a motorola e398 gsm phone, oh well never mind, I guess it is a matter of waiting untill bitpim offers support for this phone. 

# fragmented_user
I must say, for people that have phones that are supported, your script is a fine thing, allowing people to easilly set up thier mobiles

Thanks to all
anthony

---

### Post by skipo on 2006-08-07
> **subsonic_shadow said:**
> I have installed comsams but when I try to connect I het this error:


Did you find a deb file or did you have to compile it?

---

### Post by OffHand on 2006-08-08
> **skipo said:**
> Did you find a deb file or did you have to compile it?

I do not remember, sorry.

---

### Post by bomanizer on 2006-08-10
janne@matolaatikko:~$ bitpim
Traceback (most recent call last):
  File "/opt/cx_Freeze-3.0.2/initscripts/ConsoleSetLibPath.py", line 30, in ?
  File "src/bp.py", line 90, in ?
  File "src/gui.py", line 30, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in ?
  File "/usr/lib/python2.3/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in ?
  File "ExtensionLoader.py", line 12, in ?
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory

---

### Post by bomanizer on 2006-08-10
ln -s libtiff.so.4 libtiff.so.3

Got it. ;)

---

### Post by bomanizer on 2006-08-10
My Samsung SGH-Z540, not working with BitPim.. probably 'cause it's an European model...

---

### Post by JairunCaloth on 2006-08-16
LG-VX8500 Working!

Working great, only one problem. I can't get the script to run getting a 403 forbidden on the graphical installer thingy. so I just installed it myself. Problem fixed :-p

Bigger problem. I can only get it to access the phone when I run the app as sudo. I know this is a users problem but I really suck at this whole fixing user problems thing and usually when I try I end up breaking something...

---

### Post by skipo on 2006-08-16
Does anyone know how to get Samsung z500 to work with linux?

---

### Post by bomanizer on 2006-08-16
> **skipo said:**
> Does anyone know how to get Samsung z500 to work with linux?

Heh, it was simply a matter of time before a Finn stumbled here ;)

This could become a topic of great intrest, because an operator here in Finland has launched a major campaign to promote the sales of 3g phones.

---

### Post by Ben Jansen on 2006-09-22
I'm very new in the wonderfull world of ubuntu but I would like to be able to sync my 9300 with evolution.... Is that possible. What I read thusfar I tried but didn't succeed... HELP!!!

---

### Post by virtual_reality on 2007-03-19
> **OffHand said:**
> I have installed comsams but when I try to connect I het this error:

 comsams -i
Cannot open port, connection failed!
Try to connect to phone...
write() of 4 bytes failed!
No Connection, waiting for phone ready...
Try to connect to phone...
write() of 4 bytes failed!
No Connection, waiting for phone ready...
Try to connect to phone...
write() of 4 bytes failed!
No Connection, waiting for phone ready...
Try to connect to phone...
write() of 4 bytes failed!
No Connection, waiting for phone ready...
Try to connect to phone...
write() of 4 bytes failed!
No Connection, waiting for phone ready...
Tried to connect 5 times. (timeout)


Is there any way to find out why it cannot connect?

I got the same problem, what should I do?:(

---

### Post by fragmented_user on 2007-03-20
If you get a permissions error while running as  regular user ,make sure that permissions in  the 60-cell.rules file is set to 0666

ie

[I]#udev entry
#Manufacturer: LG
#Models: All straight USB cables
#Vendor ID: 0x1004
#Product ID: 0x6000

SUBSYSTEM!="usb_device", ACTION!="add", GOTO="cell_rules_end"
SYSFS{idVendor}=="1004", SYSFS{idProduct}=="6000", **MODE="0666"**
LABEL="cell_rules_end"[/I]

If that still doesnt work then try replacing 0666 with 0755

---

### Post by virtual_reality on 2007-03-20
> **fragmented_user said:**
> If you get a permissions error while running as  regular user ,make sure that permissions in  the 60-cell.rules file is set to 0666

ie

[I]#udev entry
#Manufacturer: LG
#Models: All straight USB cables
#Vendor ID: 0x1004
#Product ID: 0x6000

SUBSYSTEM!="usb_device", ACTION!="add", GOTO="cell_rules_end"
SYSFS{idVendor}=="1004", SYSFS{idProduct}=="6000", **MODE="0666"**
LABEL="cell_rules_end"[/I]

If that still doesnt work then try replacing 0666 with 0755

in what file should I set 0666?

---

### Post by fragmented_user on 2007-03-20
/etc/udev/rules.d/60-cell.rules :

---

### Post by rggavubt on 2007-04-04
I keep getting an error saying to try again later?  Is the repository busy?  I used the following :

chmod a+rx setup.sh 

and then entered :

./setup.sh

I then made all of the selections and got the error message.

---

### Post by rggavubt on 2007-04-04
I keep getting an error saying to try again later? Is the repository busy? I used the following :

chmod a+rx setup.sh

and then entered :

./setup.sh

I then made all of the selections and got the error message.
Edit/Delete Message

---

### Post by butterman on 2007-09-03
> **fragmented_user said:**
> OK, I'll be the first one. 

Phone Model: LG VX8300
Current Status: Works
Status Description: use the install_LG script. reboot the computer. works immediately after.

I have an 8300 too, but I'm getting these errors on installation:

```
BitPim Install

Installing Dependencies

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libstdc++5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ln: creating symbolic link `/usr/lib/libtiff.so.3' to `/usr/lib/libtiff.so.4.1.4': Permission denied
ln: creating symbolic link `/usr/lib/libtiff.so.3' to `/usr/lib/libtiff.so.4': Permission denied

Downloading Install files


--13:22:39--  http://ketsugi.com/ubuntu/dists/dapper/main/binary-i386/bitpim_0.9.05-1_i386.deb
           => `bitpim_0.9.05-1_i386.deb'
Resolving ketsugi.com... 74.220.202.16
Connecting to ketsugi.com|74.220.202.16|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://ketsugi.com/software/dapper-and-drowsy/ [following]
--13:22:40--  http://ketsugi.com/software/dapper-and-drowsy/
           => `index.html.7'
Connecting to ketsugi.com|74.220.202.16|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [   <=>                                                        ] 36,708        76.29K/s             

13:22:41 (76.12 KB/s) - `index.html.7' saved [36708]



Installing Main Package

/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.5/site-packages/GDebi/GDebi.py:95: GtkWarning: gdk_window_set_cursor: assertion `GDK_IS_WINDOW (window)' failed
  self.window_main.set_sensitive(False)


```

I tried manually linking (see below), but I continue to get the same error.  Anything you can recommend?

```
cd /usr/lib
ln -s libtiff.so.4 libtiff.so.3

```

---

