---
title: "[SOLVED] Cannot install nvidia gforce 7950gx please help"
date: 2007-10-30
forum: General Help
---

### Post by bhencetotozo on 2007-10-30
My system Hardware:
CPU : Amd Athlon Fx32 Dual Core 2.8ghz
Memory 4 GB ddr2 800mhz
Video card Nvidia Gforce 7950gx pcie
700 WATT power supply

Question 1:
How to install Nvidia Driver? ...
----- What i've done so far... NO SUCSESS
-- downloaded the .run file from nvidia.com ,
-- i went to console, AS ROOT i typed shutdown now, in maintence mode, i loged as root, typed init 3 , then i did the sh on the .run driver file ....
-- It said i was running on level 1 , then i ignored error and procedded.. then i got an error about couldnt download something from nvidia.com ...

Question 2 , I how can i get permission to EDIT the main.lst file?
question 3 , what is the command to copy a file from the desktop to the /home directory?
question 4 - how do i install beryl ?? before i do it i need to install the nvidia driver first.

Thank you for the help
Im sorri for being such a linux newbie,
I had alot of trouble to get where i am now. Linux ubuntu 7.10 Running finally.
Took me 8 hours to findout i had to edit the kernell line ( NOAPIC ) in order to boot.
I have a few questions i'd to know if someone can help me.

---

### Post by cwj88 on 2007-10-30
Idk Maybe U Need A New Computer

It Sounds Like Your Hardware Is Really Old And Out Of Date

Have You Tried Windows Update?!?!?!

---

### Post by carlinuxlearner on 2007-10-30
1.Download this program called "envy"
[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu10_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.8-0ubuntu10_all.deb)
2. Install (in terminal type "sudo dpkg -i envy_0.9.8-0ubuntu10_all.deb" (make sure you are in the directory you saved it in, if in Desktop then "sudo dpkg -i Desktop/envy_0.9.8-0ubuntu10_all.deb" make sure you capitalize the "D" in "Desktop")
3. open up a terminal and type "sudo apt-get install -f"
4. Run "envy" (select from menu, or run from terminal "envy -t")
5. the rest you should be able to figure out on your own.


The "( )" are for seperation and example ONLY real commands would be "sudo gedit /etc/X11/xorg.conf" or "cp help.txt /home/carl/stuff/"

"Question 2 , I how can i get permission to EDIT the main.lst file?" 
"sudo gedit (file path and name)"

"question 3 , what is the command to copy a file from the desktop to the /home directory?"
"cp (file) (path to go)"

"question 4 - how do i install beryl ?? before i do it i need to install the nvidia driver first." 
If you have the latest version of Ubuntu (7.10) there is no need for beryl, it has "compiz-fusion" preinstalled!

C@RL

---

### Post by thelocust on 2007-10-31
> **bhencetotozo said:**
> My system Hardware:
CPU : Amd Athlon Fx32 Dual Core 2.8ghz
Memory 4 GB ddr2 800mhz
Video card Nvidia Gforce 7950gx pcie
700 WATT power supply.
How many time are you going to post this?
 
[http://ubuntuforums.org/showthread.php?t=597969](http://ubuntuforums.org/showthread.php?t=597969)
 
[http://ubuntuforums.org/showthread.php?t=596664](http://ubuntuforums.org/showthread.php?t=596664)

---

### Post by bhencetotozo on 2007-10-31
YO Thank You Very Much, I will be more than happy to give u 10$ on paypal... I really appreciate your help. Thank you

---

### Post by bhencetotozo on 2007-10-31
Car linux learner.. i got an error message

When i typed 'sudo dpkg -i envy_0.9.8-0ubuntu10_all.deb'
(Reading database ... 88932 files and directories currently installed.)
Unpacking envy (from envy_0.9.8-0ubuntu10_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on build-essential; however:
  Package build-essential is not installed.
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on fakeroot; however:
  Package fakeroot is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on libstdc++5; however:
  Package libstdc++5 is not installed.
 envy depends on dpkg-dev; however:
  Package dpkg-dev is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy

---

### Post by bhencetotozo on 2007-10-31
thiago@thiago-desktop:~/Desktop$ envy -t
ENVY: The following packages are not installed:
xserver-xorg-dev
module-assistant
dh-make
debhelper
libstdc++5
dpatch

ENVY: attempting to install the packages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xorg-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xserver-xorg-dev has no installation candidate

ENVY ERROR: The following packages cannot be installed:
xserver-xorg-dev
module-assistant
dh-make
debhelper
libstdc++5
dpatch

---

### Post by bhencetotozo on 2007-10-31
Please help me im stuck

---

### Post by Maestro23 on 2007-10-31
> **bhencetotozo said:**
> Please help me im stuck

You have dependency issues. Install build-essential 1st.

> sudo apt-get install build-essential

Try installing the Envy package again.

---

### Post by bhencetotozo on 2007-10-31
THank you very much maestro, when i get home ill try that...

if any1 has more sujestions, i will be more than happy to read it.. thank you all in advance to your help and time ..

---

### Post by bhencetotozo on 2007-10-31
root@thiago-desktop:/home/thiago# sudo dpkg -i Desktop/envy_0.9.8-0ubuntu10_all.deb
Selecting previously deselected package envy.
(Reading database ... 90746 files and directories currently installed.)
Unpacking envy (from .../envy_0.9.8-0ubuntu10_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on libstdc++5; however:
  Package libstdc++5 is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy

---

### Post by carlinuxlearner on 2007-10-31
"Car linux learner.. i got an error message

When i typed 'sudo dpkg -i envy_0.9.8-0ubuntu10_all.deb'
(Reading database ... 88932 files and directories currently installed.)
Unpacking envy (from envy_0.9.8-0ubuntu10_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
envy depends on build-essential; however:
Package build-essential is not installed.
envy depends on xserver-xorg-dev; however:
Package xserver-xorg-dev is not installed.
envy depends on module-assistant; however:
Package module-assistant is not installed.
envy depends on fakeroot; however:
Package fakeroot is not installed.
envy depends on dh-make; however:
Package dh-make is not installed.
envy depends on debhelper; however:
Package debhelper is not installed.
envy depends on libstdc++5; however:
Package libstdc++5 is not installed.
envy depends on dpkg-dev; however:
Package dpkg-dev is not installed.
envy depends on dpatch; however:
Package dpatch is not installed.
dpkg: error processing envy (--install):
dependency problems - leaving unconfigured
Errors were encountered while processing:
envy"

Didn't you type in the next command I gave you, it will fix all the dependece errors "3. open up a terminal and type "sudo apt-get install -f""


This will fix it.

C@RL

---

### Post by carlinuxlearner on 2007-10-31
Ok we'll try this again.
Type this in "sudo dpkg -i envy_0.9.8-0ubuntu10_all.deb"
then type "open up a terminal and type "sudo apt-get install -f"

And see what is does, ok, and DON'T give up!!!

There IS another way if this doesn't work.

C@RL

---

### Post by bhencetotozo on 2007-10-31
Still did not work

---

### Post by carlinuxlearner on 2007-10-31
In a terminal window type in "lspci" and post out put here.
(this is to find out exactly what graphics card you have)

C@RL

---

### Post by bhencetotozo on 2007-10-31
well i typed this :

root@thiago-desktop:/home/thiago/Desktop# lspci

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:08.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:09.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:09.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:09.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0a.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0c.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0d.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0d.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0e.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:10.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:15.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
02:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
02:01.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
03:00.0 3D controller: nVidia Corporation G71 [GeForce 7950 GX2] (rev a1)
04:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GX2] (rev a1)
05:08.0 Network controller: RaLink RT2561/RT61 802.11g PCI
05:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
06:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
06:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
root@thiago-desktop:/home/thiago/Desktop#

what do i do now?

---

### Post by carlinuxlearner on 2007-10-31
OK you need this driver [http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run)

download it to your Desktop, then restart your computer and in the boot menu select (recovery mode)
once booted type in this "sh /home/YOURUSERNAME/DesktopNVIDIA-Linux-x86-100.14.19-pkg1.run"
replace YOURUSERNAME with your user name.
answer all questions so it will install it (don't worry about it if it tells you that your are in runlevel 1, it doesn't matter)

once it's done restart your computer with Ctrl+Alt+Del see what happens, 

If you get a black screen proceed with these instructions press Alt+F2 and type "startx" post out put here (if possible). If you don't have another computer to post on, then do this "nano -w /etc/X11/xorg.conf" (make sure make those ONE'S "1" instead of "L's" ok)
Find the section in the file that says "Device" in in that section find the part that says "driver " change it's content to "nv"  so it says " Driver         "nv"
save it with Ctrl+X
,then restart your computer,

C@RL

---

### Post by carlinuxlearner on 2007-10-31
Oh wait before you do that try this (I am soooooo stupid) in the GUI just double click on "envy" file, and tell it to install it should ALL work! Like I said I'm stupid!

C@RL

---

### Post by bhencetotozo on 2007-10-31
What is GUI ??? how do i open GUI .. and NO you are not stupid

---

### Post by carlinuxlearner on 2007-10-31
The GUI is the "Graphic User Interface" AKA your desktop.
So just open up your file manager ("Places" menu "Home Folder") find where you downloaded your "envy" file, double click on it and tell it to install.

C@RL

---

### Post by bhencetotozo on 2007-10-31
OK I FOUND IT... !!!!!!!!!!! :)

when i open ENVY, a nice scrreen comes on .. 
THEN, it says its missing some dependencies..
 it says ENVY wont work without them

It asks:
would like envy to try to install missing dependencies.. i clicked YES

It says downloading 31 of 31 .. then it downloads and says:

YOU HAVE ONE BROKENPACKAGE ON YOUR SYSTEM
use the "broken" filter to locate it

---

### Post by carlinuxlearner on 2007-10-31
All right!!! Run this in the terminal "sudo apt-get install -f" this should fix it (I think)

If something doesn't work just post here.

I am working on a guide for installing Nvidia drivers.

C@RL

---

### Post by Maestro23 on 2007-10-31
> **bhencetotozo said:**
> OK I FOUND IT... !!!!!!!!!!! :)

when i open ENVY, a nice scrreen comes on .. 
THEN, it says its missing some dependencies..
 it says ENVY wont work without them

It asks:
would like envy to try to install missing dependencies.. i clicked YES

It says downloading 31 of 31 .. then it downloads and says:

YOU HAVE ONE BROKENPACKAGE ON YOUR SYSTEM
use the "broken" filter to locate it

System>>Admin>>Synpatic

In Synaptic, you will find "Fix Broken Packages" under Edit.

If that doesn't work, the** Filters **Optons is under **Settings** in Synaptic.

---

### Post by bhencetotozo on 2007-10-31
ok this is what i did..

typed the command u just told me to,

opened envy, and it said

Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.

before it was saying soemthing different.. about 1 broken pagkage..

by the way, eventime i get an error from ENVY it desapears from GUI ..
then,  everytime i try to run envy i need to type  

sudo dpkg -i envy_0.9.8-0ubuntu10_all.deb

otherwise it wont show in the GUI

---

### Post by carlinuxlearner on 2007-10-31
Install Envy again the GUI way and then do as "Maestro23" suggested.

C@RL

You have a weird broken package problem, have you tried to install something and messed it up?

---

### Post by bhencetotozo on 2007-10-31
Hmmmm im not sure honestelly ... the only thing i sucessfully installed so far was

Adobe Flash Player so i could view youtube videos..

NOTHING ELSE has been installed by me but the FLASH plugin LOL.. < << im a windows user but im sick of it so now i want LINUX...and you motivated me so I will follow your advice.. I will never give up

---

### Post by bhencetotozo on 2007-10-31
BIT ERRORS 

1st error

thiago@thiago-desktop:~/Desktop$ sudo dpkg -i envy_0.9.8-0ubuntu10_all.deb
[sudo] password for thiago:
Selecting previously deselected package envy.
(Reading database ... 90741 files and directories currently installed.)
Unpacking envy (from envy_0.9.8-0ubuntu10_all.deb) ...
dpkg: dependency problems prevent configuration of envy:
 envy depends on xserver-xorg-dev; however:
  Package xserver-xorg-dev is not installed.
 envy depends on module-assistant; however:
  Package module-assistant is not installed.
 envy depends on dh-make; however:
  Package dh-make is not installed.
 envy depends on debhelper; however:
  Package debhelper is not installed.
 envy depends on libstdc++5; however:
  Package libstdc++5 is not installed.
 envy depends on dpatch; however:
  Package dpatch is not installed.
dpkg: error processing envy (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 envy




2nd error::

xserver-xorg-devEnvy is unable to run because of the lack of the following packages:


module-assistantEnvy is unable to run because of the lack of the following packages:


dh-makeEnvy is unable to run because of the lack of the following packages:


debhelperEnvy is unable to run because of the lack of the following packages:


libstdc++5Envy is unable to run because of the lack of the following packages:


dpatch

Please install them manually and launch Envy again

---

### Post by carlinuxlearner on 2007-10-31
I SAID INSTALL IT THE "GUI" WAY!!!!! AKA "So just open up your file manager ("Places" menu "Home Folder") find where you downloaded your "envy" file, Double click on it and tell it to install." THEN do as "Maestro23" suggested.

C@RL

I've got to go (getting late here) I will post my guide tomorrow so you will be able to do it the other way, (I don't think (in this case) Envy is worth messing with). I'll be on tomorrow. Keep trying though! DO WHAT "Maestro23" suggests.

---

### Post by bhencetotozo on 2007-10-31
OK i tryed it that way.. look i got a window saying: 

I got an error when i doubleclicked on the package .. look at this:


Package installer - envy

Error - Depenmdencie is not satisfiable xserver-xorg-dev

Description
install the ATI or the NVIDIA driver
Envy is an application written in Python which will download the latest Nvidia driver or the Legacy driver (for older cards) (according to the model of your card) from Nvidia's website and set it up for you handling dependencies (compilers, OpenGL, etc.) which are required in order to build and use the driver.

---

### Post by Maestro23 on 2007-10-31
> **bhencetotozo said:**
> OK i tryed it that way.. look i got a window saying: 

I got an error when i doubleclicked on the package .. look at this:


Package installer - envy

Error - Depenmdencie is not satisfiable xserver-xorg-dev

Description
install the ATI or the NVIDIA driver
Envy is an application written in Python which will download the latest Nvidia driver or the Legacy driver (for older cards) (according to the model of your card) from Nvidia's website and set it up for you handling dependencies (compilers, OpenGL, etc.) which are required in order to build and use the driver.

> sudo apt-get install xserver-xorg-dev

Then try your Envy again.

---

### Post by bhencetotozo on 2007-10-31
Maestro , i tryed that commandI got an error 

thiago@thiago-desktop:~$ sudo apt-get install xserver-xorg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xorg-dev
thiago@thiago-desktop:~$

---

### Post by Maestro23 on 2007-10-31
> **bhencetotozo said:**
> Maestro , i tryed that commandI got an error 

thiago@thiago-desktop:~$ sudo apt-get install xserver-xorg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xorg-dev
thiago@thiago-desktop:~$

It should be there.  Make sure you have all your Repositories enabled, Universe/Multiverse, 3rd-Party, etc..  System>>Admin>>Software Sources.

---

### Post by bhencetotozo on 2007-10-31
!!!!!!!!!!!!! CHEEEEEEEERSssssss !!!!!!!!!!!!!!!!!!!

the Multiverse thingys are all checked.. all the check boxes ...

now envy is there but one error message displays :

Envy has detected that one of the following applications is running: dpkg, apt-get,synaptic,update-manager, adept, adept-notifier. Make sure that they are not running and launch Envy again.


The only button to click is the "OK buttom.. i have a feeling that we're really close

---

### Post by Maestro23 on 2007-10-31
> **bhencetotozo said:**
> !!!!!!!!!!!!! CHEEEEEEEERSssssss !!!!!!!!!!!!!!!!!!!

the Multiverse thingys are all checked.. all the check boxes ...

now envy is there but one error message displays :

Envy has detected that one of the following applications is running: dpkg, apt-get,synaptic,update-manager, adept, adept-notifier. Make sure that they are not running and launch Envy again.


The only button to click is the "OK buttom.. i have a feeling that we're really close

Shutdown any window/program you have open.  Especially Synaptic, Software sources, etc..  Envy should be the only program you're trying to run.

---

### Post by bhencetotozo on 2007-10-31
WOW  !!!!!!!!!!!!!!

I have something to say ....

Maestro and carlinuxlearner ....

Special thanks to them ... I will be posting a video o myself saying thankyou and showing to the world that you are both  verygood on linux...

[www.youtube.com/thiagocosta85](www.youtube.com/thiagocosta85) .. those are my videos that i made ...

Now i am so happy...

I have a question...

when you go to youtube.com ... if u type LINUX ... the first video found is Linux Ubuntu with beryl vs windows vista ...

I wanna make my linux look  like that, what do i have to do? themes? ..

please watch the video below to give me advices ;)

[http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ)

should we talk in this forum or open another one?

---

### Post by Maestro23 on 2007-10-31
> **bhencetotozo said:**
> WOW  !!!!!!!!!!!!!!

I have something to say ....

Maestro and carlinuxlearner ....

Special thanks to them ... I will be posting a video o myself saying thankyou and showing to the world that you are both  verygood on linux...

[www.youtube.com/thiagocosta85](www.youtube.com/thiagocosta85) .. those are my videos that i made ...

Now i am so happy...

I have a question...

when you go to youtube.com ... if u type LINUX ... the first video found is Linux Ubuntu with beryl vs windows vista ...

I wanna make my linux look  like that, what do i have to do? themes? ..

please watch the video below to give me advices ;)

[http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ)

should we talk in this forum or open another one?

Awesome man.  Glad we got it accomplished.  You need to send a PM to  carlinuxlearner saying "Succes!!!". :)

If you want Compiz-Fusion in Gutsy, first you need to install the Compiz-Manager:

> sudo apt-get install compiz compizconfig-settings-manager 

More info here: [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

In Gutsy, Desktop effects are built in by default.  Goto: System>>Prefs>>Appearance

The Compiz-Manager will put its entry under: System>>Prefs>>Advanced Desktop Effects

Here is the link to the Compiz site: [http://www.compiz-fusion.org/](http://www.compiz-fusion.org/)
Compiz Wiki: [http://wiki.compiz-fusion.org/](http://wiki.compiz-fusion.org/)

I don't know the exact themes/settings that are being used in that video, but I'm sure someone on the forums will know.  You can close down this thread and mark it SOLVED using the Thread Tools.

Start you a new thread for your Compiz questions/issues should they arise.  Again, glad we could help ya.:guitar:

---

### Post by bhencetotozo on 2007-11-01
I cannot find the Thread tool to mark it as solved !!!!

---

### Post by arvore on 2007-11-01
I didn't get.

I still have the following problem when I try to install the nvidia driver using Envy:

ENVY ERROR: The following packages cannot be installed:
libqt3-mt-dev
kernel-wedge
rpm
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev

I enabled all the repositories, and still got nothing...

---

### Post by bhencetotozo on 2007-11-01
Im pretty sure maestro will help you and solve it.

---

### Post by Maestro23 on 2007-11-01
> **bhencetotozo said:**
> I cannot find the Thread tool to mark it as solved !!!!

C'mon man, after all the commands and stuff you went thru to get your card working, you can't find something right in front of ya.:)

---

### Post by bhencetotozo on 2007-11-01
NIce maestro !!!!!!!!!! ahhaha i found it !!!!!!!!! hmmmmm...

Thank you once again man ... now i have the CUBE working !!!!!!!!!!

IF i was on windows i would post te video i recorded with my camera but im affraid i wont be able to do all that on linux .. im still a noob .. !!!!!!

 hmmmmm...
I would know how to convert MOV files, How to edit them (on windows i use Vegas7.0 )

I dont even know how to play MP3 on Linux yet HAHAHAHAHAH ...

IM affraid its gonna take 2 days to find out like it did for me to get the nvidia drivers and the cube. !!!!!!!!!!!!!

---

### Post by carlinuxlearner on 2007-11-01
@ arvore

Try running this in the terminal "sudo apt-get install libqt3-mt-dev kernel-wedge rpm sharutils libgtk2.0-dev libxxf86misc-dev libxtst-dev libxxf86vm-dev libxinerama-dev"

Then try installing Envy the GUI way.


C@RL 

> **arvore said:**
> I didn't get.

I still have the following problem when I try to install the nvidia driver using Envy:

ENVY ERROR: The following packages cannot be installed:
libqt3-mt-dev
kernel-wedge
rpm
sharutils
libgtk2.0-dev
libxxf86misc-dev
libxtst-dev
libxxf86vm-dev
libxinerama-dev

I enabled all the repositories, and still got nothing...

---

### Post by Maestro23 on 2007-11-01
> **bhencetotozo said:**
> NIce maestro !!!!!!!!!! ahhaha i found it !!!!!!!!! hmmmmm...

Thank you once again man ... now i have the CUBE working !!!!!!!!!!

IF i was on windows i would post te video i recorded with my camera but im affraid i wont be able to do all that on linux .. im still a noob .. !!!!!!

 hmmmmm...
I would know how to convert MOV files, How to edit them (on windows i use Vegas7.0 )

I dont even know how to play MP3 on Linux yet HAHAHAHAHAH ...

IM affraid its gonna take 2 days to find out like it did for me to get the nvidia drivers and the cube. !!!!!!!!!!!!!

Oh my, you got your video card installed correctly AND have the pretty eye-candy going... you're getting dangerous man.:)

Seriously, glad you're getting the things you want installed and working properly.  When it comes to multimedia (mp3, playing DVD, etc...) you need to install the proper codecs.  Take a look at Restricted Formats.
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28Formats%29%7C%28Restricted%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28Formats%29%7C%28Restricted%29)

Good luck man.:guitar:

---

### Post by bhencetotozo on 2007-11-02
Maestro once again thank you !!!!..

i will never forget aobut u.. PLus, i recorded a video of my linux running.. ill post it when i go on windows xp or vista...

but right now i jst wanna enjoy the burning windows and magic cube LOL !!!!!!!!!!!


i mentioned ur name on the video by the way ;)

---

### Post by Maestro23 on 2007-11-02
> **bhencetotozo said:**
> Maestro once again thank you !!!!..

i will never forget aobut u.. PLus, i recorded a video of my linux running.. ill post it when i go on windows xp or vista...

but right now i jst wanna enjoy the burning windows and magic cube LOL !!!!!!!!!!!


**i mentioned ur name on the video by the way** ;)

Nooooo... I like to stay in the shadows:)

Seriously, glad I could help.  There are too many people on the forums with far more Ubuntu knowledge than I have.  I just happen to find your thread that day, and was able to help.:lolflag:

---

### Post by carlinuxlearner on 2007-11-02
> **Maestro23 said:**
> There are too many people on the forums with far more Ubuntu knowledge than I have.  I just happen to find your thread that day, and was able to help.:lolflag:

Same here!

C@RL

---

