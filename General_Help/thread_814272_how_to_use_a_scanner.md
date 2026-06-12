---
title: "how to use a scanner"
date: 2008-05-31
forum: General Help
---

### Post by kureyamu on 2008-05-31
hello

a newby question - i see there is another question here already with a similar theme, but i didn't understand some of the technicalities, so i am keeping my question simple.

does anyone know how to set up a scanner? :confused:

my operating system is ubuntu hardy heron 8.04

my scanner is Epson GT-8200 flatbed scanner (loaded backend epson:libusb:002, Sane version 1.0.19)

i plugged in the scanner and in Applications/Graphics found and opened XSane Image Scanner

it looks INsane rather than XSane, non user-friendly

(my confidence wasn't inspired by the application XSane)

anyway, i put a colour picture into the scanner and pressed "Acquire preview", and got a black and white scan

in the Xsane Preferences, i had ticked "enable color management"

and i got an Error Message:
Error during CMS conversion. Could not open ICM profile

i don't know what the "I" in "ICM" stands for, the CM must mean Colour Management

in short, the Xsane software does not function correctly

does anyway know how to configure Xsane so that i can scan colour photos?

or better still, does anyone know of clean, user-friendly scanner software?

regards

kureyamu

---

### Post by vvvladut on 2008-06-01
I don't think there is any clean, user friendly scanner software for Linux...or maybe there is, but they all depend on SANE and thus on the driver that SANE installs for your scanner. Scanner driver support is awful in Linux, I would say. For example, my Canon 8600F does not work at all...it's one of the reasons I still keep XP.

I know, I know, it's not Linux's fault, it's the manufacturers who are not open source friendly, blah, blah...I'm just making a observation on the state of things. It doesn't matter who's fault it is, the end result is that for many of us out there XP is still the only hope to scan something.

---

### Post by gypaete09 on 2008-06-01
I use a HP 3055 multifunction printer and scan from Gutsy with the "built-in" Xsane program and have no trouble. It just also sees my webcam as a input device, so I need to choose the printer before I scan a page.

---

### Post by SPr on 2008-06-01
Use scanimage to test the scanner. It *may* give more information into what is going wrong.

```
sudo apt-get install sane-utils
scanimage --list-devices

```
Does the scanner report it's name correctly?
```

scanimage --test

```
Are any errors reported?

See```
man scanimage
``` for more info and a list of other utilities.

---

### Post by kureyamu on 2008-06-01
hello folks

thanks for replying.


**vvvladut said**:>  I know, I know, it's not Linux's fault, it's the manufacturers who are not open source friendly, blah, blah...I'm just making a observation on the state of things. It doesn't matter who's fault it is, the end result is that for many of us out there XP is still the only hope to scan something.

i gave up XP a month ago for ethical reasons 

having paid high prices for my XP, Office and Publishing EULAs at the time

but not wanting to be contaminated any more by that ethos of greed, psychological control and abuse of 3rd world peoples who need a cheap OS in order to network with the world and improve their standards of living and chances of survival

by agreeing to the XP EULA, i was agreeing to bow to a way of thinking and social control

now i have to live with my clean conscience and printing, scanning and sound card recognition become problems, just for starters ... 

yes, i shall try to get xsane to work, gypaete09, i'm just a bit unsure about how to gpo about doing that ... oh, for a hardware wizard ... it ain't  me, babe :-)

at the time of writing this, i am on a Linux Mint machine, but when i get back to Ubuntu this evening, i shall try your suggestions, SPr, and then get back with the results ... thanks very much for that

regards

kureyamu


*[CENTER]microsoft was a famous 20th century software company[/CENTER]*

---

### Post by kureyamu on 2008-06-01
hello SPr

i followed your advice and tried to find information in a terminal and it got me started looking around for more info. :)

so far no success, but this what i have been doing:

(the question, i muse, is linux going to desert me? leave me struggling and unable to do daily tasks? ha ha ha

i was thinking of putting some books on ebay to raise some cash, but i need a scanner because items without photographs don't sell, and some items look best scanned, rather than photographed ... 

if i can learn to do this, then i can advise other beginners when they have a similar problem ...)

anyway, this is the stuff from a terminal - first i tried to locate sane-utils just in case they were already installed, as they weren't, i installed them:

kureyamu@nakadori:~$

sudo updatedb  		(press Enter)

[sudo] password for kureyamu:

........ 	        (press Enter)

kureyamu@nakadori:~$

sudo locate sane-utils	(press Enter)

kureyamu@nakadori:~$

sudo apt-get install sane-utils	(press Enter)

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  unpaper
The following NEW packages will be installed
  sane-utils
0 upgraded, 1 newly installed, 0 to remove and 82 not upgraded.
Need to get 128kB of archives.
After this operation, 344kB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe sane-utils 1.0.19-1ubuntu3 [128kB]
Fetched 128kB in 1s (112kB/s)     
Selecting previously deselected package sane-utils.
(Reading database ... 107101 files and directories currently installed.)
Unpacking sane-utils (from .../sane-utils_1.0.19-1ubuntu3_i386.deb) ...
Setting up sane-utils (1.0.19-1ubuntu3) ...
Adding saned group and user...

kureyamu@nakadori:~$

sudo apt-get autoremove  libboost-thread1.34.1	(press Enter)

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-date-time1.34.1
The following packages will be REMOVED
  libboost-date-time1.34.1 libboost-thread1.34.1
0 upgraded, 0 newly installed, 2 to remove and 82 not upgraded.
After this operation, 385kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 107114 files and directories currently installed.)
Removing libboost-date-time1.34.1 ...
Removing libboost-thread1.34.1 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

kureyamu@nakadori:~$

sudo apt-get autoremove libboost-date-time1.34.1	(press Enter)

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libboost-date-time1.34.1 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 82 not upgraded.

kureyamu@nakadori:~$

scanimage --list -devices			(press Enter)

device `epson:libusb:002:002' is a Epson GT-8200 flatbed scanner


kureyamu@nakadori:~$

scanimage --test				(press Enter)

scanimage: scanning image of size 424x585 pixels at 1 bits/pixel
scanimage: acquiring gray frame, 1 bits/sample
scanimage: reading one scanline, 53 bytes...	PASS
scanimage: reading one byte...		PASS
scanimage: stepped read, 2 bytes... 	PASS
scanimage: stepped read, 4 bytes... 	PASS
scanimage: stepped read, 8 bytes... 	PASS
scanimage: stepped read, 16 bytes... 	PASS
scanimage: stepped read, 32 bytes... 	PASS
scanimage: stepped read, 64 bytes... 	PASS
scanimage: stepped read, 63 bytes... 	PASS
scanimage: stepped read, 31 bytes... 	PASS
scanimage: stepped read, 15 bytes... 	PASS
scanimage: stepped read, 7 bytes... 	PASS
scanimage: stepped read, 3 bytes... 	PASS


So, my scanner does not work; it says "Error during CMS conversion. Could not open scanner ICM profile."
I don't know what ICM means, but what is happening is that the scanner is colour blind, like an ox, it can only see in black and white, or here more precisely shades of grey ... that can't be much fun for the poor machine

it will scan in shades of grey but not in colour

my scanner is an Epson Perfection 1650 flatbed scanner
and X-sane sees it as an Epson GT-8200 flatbed scanner

This could be a major part of the problem.

So my next step is to persuade X-sane to recognise Perfection.


the program "alien" that converts .rpm to .deb files for ubuntu was already installed.
if it hadn't been. i could have installed it through Synaptic Package Manager.

after reading stuff in forums, i found this link to a site where avasys (linked to epson) supplied printer drivers for linux:

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

from there, i downloaded a .rpm file printer driver for the epson 1650 to my desktop:
iscan-2.11.0-i.c2.i386.rpm

i made a folder called "Downloads" and a folder called "scanner" and i cut and pasted the .rpm file into "scanner", so the path is:
/home/kureyamu/Downloads/scanner/iscan-2.11.0-i.c2.i386.rpm

in  the terminal, as root, i changed directory with the command line cd to where the epson driver lay, "press Enter" is used to highlight the lines of code:

cd /home/kureyamu/Downloads/scanner/		(press Enter)

then using the application "alien", i converted the rpm file to a deb file:

kureyamu@nakadori:~/Downloads/scanner$

sudo alien -k iscan-2.11.0-1.c2.i386.rpm	(press Enter)

Warning: Skipping conversion of scripts in package iscan: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.

iscan_2.11.0-1.c2_i386.deb generated

next i installed the deb file; 

kureyamu@nakadori:~/Downloads/scanner$

sudo dpkg -i iscan_2.11.0-1.c2_i386.deb		(press Enter)

Selecting previously deselected package iscan.
(Reading database ... 107099 files and directories currently installed.)
Unpacking iscan (from iscan_2.11.0-1.c2_i386.deb) ...
Setting up iscan (2.11.0-1.c2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

then i exited the terminal and rebooted my system.

the preview screen where i could click "acquire preview" and scan and load a grey image now no longer has error messages if i change the settings to shades of grey.

In brief, i have installed sane-utils and the scanner driver for my scanner and my scanner does not yet recognise colour.

but whenever i try to scan in colour the problem re-occurs:

(1) there is an error message: "Could not open scanner ICM profile."

(2) the scanner will scan in shades of grey and the image can be saved, but i have no colour.

it makes me feel washed-out.

Henri Mattisse would not be satisfied. nor would Beat Takeshi or Haruki Murakami.

(3) i tried "scanimage --list -devices" list devices again, and X-sane still thinks my scanner is a GT-8200,
not a Perfection 1650 ... this means that the printer driver i installed does not connect to X-sane ...

where to go from here ...

i shall have to find out how to make an ICM profile, whatever that is ...

hey, wouldn't it be nice if the developers wrote scanner detection software?

regards

kureyamu


*[CENTER]microsoft was a famous 20th century software company[/CENTER]*

---

### Post by kureyamu on 2008-06-02
hello

i have now got my scanner to work as root.

i had installed a scanner driver but i removed it and used only applications found in Synaptic Packet Manager.

this is what i learned since i last posted, and may be helpful to others:

the installation and use of a scanner comes in two parts:

[B](1) make sure all necessary dependencies are installed and check that you can use the scanner as root;

(2) add your name to the scanner user group and set the scanner permissions as all users.[/B]

----------------

So re part (1): do the following:

(a) go to System/Administration/Synaptic Packet Manager and make sure the following packets are installed; if you add any, reboot after their installation:

libsane 1.0.19-1 ubuntu 3
libsane-extras 1.0.18.12 ubuntu 1
sane-utils 1.0.19-1 ubuntu 3
xsane 0,995-1 ubuntu 1
xsane-common 0.995-1 ubuntu 1
xsane-doc 0.995-1 ubuntu 1
libusb-0.1.14 2:0.1.12-8

(b) make sure that kooka or other scanner software that may cause conflict is not installed.

(c) plug in your scanner and click on Applications/Graphics/XSane Image Scanner ... you will probably get a message that no scanner can be found; this action (c) was included just in case a miracle happened.

(d) open a terminal, become root and nudge your system into wakefulness with the command line:

sudo updatedb  (press Enter and give your password)

(e) run the scanner as root with the command line:

sudo /usr/bin/xsane 	(you will get warning messages suggesting fire, flood, imprisonment and solitary confinement, but ignore them and press Enter)

(f) the scanner will start up; you will see that you can set it to run with colour; scan and save a coloured image to check that it is working correctly, and then close it down. success :-)

----------------------

So now we drop from a sublime high tone to the ridiculous.

i have no idea how to do part 2.

pathetic, huh?

Now that i know that the scanner works well, i have to set it to run for a user, but because i'm still a newbie and don't know the code, i know the target but i don't know how to reach it.

on the Debian forums, experienced users tell newbies to "put your user name in the user group."

does anyone passing by this page know how:

(1) to put my name in the scanner user group? i mean, if the scanner group has a telephone number, can you pass it on so that i can give them a ring and add my name?
where the scanner group is located and how to join their members-only club is a mystery ...

(2) set my scanner permissions so that the scanner can be used by all users ( i presume the code would like: sudo chmod 777 but_what_path_or_application_comes_here ...  i do not know to which usb port my scanner is connected, or how to find its path). 

by the way, when i go into a terminal and use the code: sudo scanimage --list-devices

the response is:

[I]No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).[/I]

and when in the terminal, i make the command:  sudo scanimage --test

the response is: 

*scanimage: no SANE devices found*

yet at the same time the XSane application opens and i can use my scanner, which works to perfection :-)~

there is something badly awry with the XSane detection, coding and permissions ...

but i am hopeful of bounding the last hurdle

Thank you for reading this post.

Regards

Kureyamu


*[CENTER]microsoft was a 20th century operating system[/CENTER]*

---

### Post by SPr on 2008-06-02
I assume you've seen the search results for "[GT-8200 +1650](www.google.co.uk/search?hl=en&q=GT-8200+%2B1650&btnG=Search&meta=)".

To add a user to a group use users-admin or click system>admin>Users and Groups.

HTH

---

### Post by kureyamu on 2008-06-07
thanks for that HTH

(sorry, i wasn't sure ... are those your user initials?).

**SPr said:**>  I assume you've seen the search results for "GT-8200 +1650".

To add a user to a group use users-admin or click system>admin>Users and Groups.

HTH

yes, if you mean search results in google or other browser, i was surprised to find that Epson GT-8200 is Japanese for Epson Epson 1650 - both names refer to the same scanner.

thank for pointing me to System/Administration/Users and Groups.

details are below for other people to see.

continuation of the "trying to scan since 2001" saga (not only me but the poor souls before me, long since dead and gone :( )

so i went to System/Administration/Users and Groups and i gave my password to authenticate.
Thare are 2 categories: (1) name: kureyamu (2) name: root. 
i highlighted "root" and clicked on "Manage Groups" to open a list which includes "scanner."
i clicked on Properties and it showed 2 Group Members: kureyamu and root: the boxes were unchecked so i ticked them and closed the dialog box.
i rebooted and plugged in the scanner.

It's half successful, not fully successful because although according to the online forums, this same problem of scanner installation has been going on since 2001 on Debian based systems, no-one has bothered to correct the bugs and make it work as an office tool on a PC (Personal Computer i.e. it's not national security stuff on a main frame & a home user would expect to be able to use a scanner as a normal office tool on his/her personal computer, not to have to work as root in a terminal in the dead of night, behind blacked out windows...)

So does it work? Yes, after a fashion ("take me for a buggy ride" ... a great old blues song by Bessie Smith hahaha).

The scanner settings box opens at last on the desktop and it's possible to scan and save the picture or whatever from the desktop. :)

but i cannot see what i am scanning or saving because the "scan image" & "preview scan image" box does not open, so i do not know if i have to re-arrange the picture to be scanned, or to change any settings, until i have scanned, saved, and looked at the scanned image in /home/kureyamu/pictures ... i cannot open the preview pane and the reason given is a pop-up error message box which states: > Error during CMS Conversion. Could not open Scanner/CM Profile.

this same error message has been popping up since day 1, probably the same box since 2001.

i thought it was connected with root permissions, but i have just set the permissions for user ...

does anyone know the meaning of that error and how to correct it? being so close to success (the scanner can be used, so it's a kind of success)it would be satisfying to finish, and after that i shall have to try to work out how to file a bug report to Ubuntu about this, although that may be disregarded for another 7 years ...

what puzzles me is that i thought some small companies had switched to Ubuntu ... office workers use scanners regularly ... do they have a different ubuntu from the free version?

regards

kureyamu

---

### Post by kureyamu on 2008-06-07
hello Spr

i installed LipProf and its dependencies and i no longer get any error messages when trying to use the scanner.

now everything is working perfectly.

i didn't need to use LProf to set up a Colour Profile for CMS, the Colour Management System, but perhaps its dependent libraries were of use to XSane, and that's why my error messages stopped ...

thank you for your tips and moral support, SPr. Without you i would still be in the early stages of installation.

i shall now repost a short clear How To so that it may benefit other users. 

take care & best wishes

kureyamu

---

### Post by bayvista on 2008-06-10
I'm trying to use an HP 4185 All-in-one. The printer works fine, but the scanner only scans half an A4 page. Can't find any setup parameters for this. Using "Insane".

David

---

### Post by cariboo on 2008-06-10
I had the same problem with an old Snapscan 600 connected to my Apple G3 running Hardy. All I had to do was add myself to the scanner group and everything worked the way it should.

Good to see you got your scanner working.

Jim

---

### Post by senewag on 2008-06-10
Hi kureyamu,

Interesting to see what you have done there... but it is beyond me.
I notice that in "preferences", if you tick "enable color management" you get that ICM error message popping up straight away, so I untick it but then the white-balance is slightly off and it is hard trying to adjust the colours just right with the colour slide bars.  Which means I can't scan photos :(

---

### Post by kgas on 2008-08-20
I have similar error and installed the xsane application again. Thro' another forum I found a solution. I removed the options in the Preferences Enable Color management and Edit medium definition.Also using hp-check -t command ensure all dependent modules installed. I will dig for the ICM files and come back

---

### Post by edward havrylak on 2008-08-22
> **kureyamu said:**
> hello

a newby question - i see there is another question here already with a similar theme, but i didn't understand some of the technicalities, so i am keeping my question simple.

does anyone know how to set up a scanner? :confused:

my operating system is ubuntu hardy heron 8.04

my scanner is Epson GT-8200 flatbed scanner (loaded backend epson:libusb:002, Sane version 1.0.19)

i plugged in the scanner and in Applications/Graphics found and opened XSane Image Scanner

it looks INsane rather than XSane, non user-friendly

(my confidence wasn't inspired by the application XSane)

anyway, i put a colour picture into the scanner and pressed "Acquire preview", and got a black and white scan

in the Xsane Preferences, i had ticked "enable color management"

and i got an Error Message:
Error during CMS conversion. Could not open ICM profile

i don't know what the "I" in "ICM" stands for, the CM must mean Colour Management

in short, the Xsane software does not function correctly

does anyway know how to configure Xsane so that i can scan colour photos?

or better still, does anyone know of clean, user-friendly scanner software?

regards

kureyamu
try Kooka scanning software or use Gimp to get into xsane this seems to bypass the original setting of Xsane ps in gimp you will see options device options, select this option first. if this dont try drivers from this thread . deb [http://download.tuxfamily.org/arakhne/ubuntu](http://download.tuxfamily.org/arakhne/ubuntu) distname universe

---

### Post by zman58 on 2009-09-27
I was adjusting one of the settings in sane. I think it was the scanmode. After changing it I started getting this message. I tried changing it back, but no matter what I did I kept getting the error message. It seems related to this post:

"Error during CMS Conversion. Could not open Scanner/CM Profile."

I exited xsane and renamed my sane settings folder by opening a command prompt and typing the following.

mv .sane .sane_saved

This basically gets rid of all of the local setting for sane/xsane. Afterwards I started xsane again. This time it started with defaults, rescanned for the scanner device and is no longer complaining about the CMS. I seems to be working perfectly once again.

My scanning device is a HP PSC 1600 all-in-one print scan copy device.

---

