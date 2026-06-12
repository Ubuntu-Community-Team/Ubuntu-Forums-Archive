---
title: "ubuntu help (urgent)"
date: 2008-06-18
forum: General Help
---

### Post by Jaxite on 2008-06-18
Okay, heres the reality.
Im 11 years old, i decided to install ubuntu as it looks cool, and seems secure. I deleted windows xp for it, installed it all and it's working fine. Only 1.. no, 2 problems..

1. My screen resolution is wrong. All the buttons, everything seems big. I only have a small screen for my laptop, how do i fix it?

2. I tried downloading msn, and a few other .exe's and .zips. But when I tried to open, it said 'Open with what?'. I realised i needed winrar for .zip and .rar, but how come i can't open .exe's?
PLEASE HELP
My dad will kill me if he finds out i have installed a new operating system that isn't working properly.
=[
Thanks

---

### Post by Nepherte on 2008-06-18
2. The applications for windows will not work on Ubuntu, or linux in general unless you use wine. There do exist a lot of alternatives for pretty much every application on Windows. For msn you have, for example, pidgin, emesene and amsn. You can install software using synaptic, the package manager that comes with ubuntu: System > administration > synaptic package manager.

---

### Post by rraj.be on 2008-06-18
You can use wine for installing windows application's.

No exe can run under ubuntu without wine.

But note that all windows applications are [COLOR="DarkRed"]NOT[/COLOR] compatible with wine.

Type this to install windows application in wine

```
sudo apt-get install wine
```

get here for more info.

[[COLOR="Blue"]www.winehq.org/[/COLOR]]("www.winehq.org/")

---

### Post by manfer on 2008-06-18
> **rraj.be said:**
> 

But note that all windows applications are compatible with wine.



Is this true or you forgot a not?

---

### Post by rraj.be on 2008-06-18
> **manfer said:**
> Is this true or you forgot a not?

I am extremly sorry.

I missed that "NOT" there.

Thanks a lot for the notification.

---

### Post by ubuscout on 2008-06-18
> **Jaxite said:**
> Okay, heres the reality.
...
My dad will kill me if he finds out i have installed a new operating system that isn't working properly.
=[
Thanks

...dont'be afraid about your choice ! ;-)   ..u have choosen the best way... maybe u'll find some difficult at first... but with patience (u need only of this), u will workaround everything with ubuntu ;) !

For the windows application, wine is one of the best way... but not always u can run every application...  with little bit more experience you could try in the next also virtualization windows (ie virtualbox) maybe for more critical windows application...

btw for wine syntax is something like this:
wine "/your-application-path/your-application-name"



good luck :)

---

### Post by Jaxite on 2008-06-18
i just downloaded wine, it downloaded as a .tar.bz2 and i can't open it

the files dont really matter too much atm, i just need to fix the screen first

---

### Post by mali2297 on 2008-06-18
Regarding the first problem...

Open the settings manager and then go to the *Display* menu. See if it helps changing the settings there. You can also try changing Font DPI in the *User Interface* menu (96 is usually a good option).

Post back if you still have problems.

---

### Post by Jaxite on 2008-06-18
still no luck =[

---

### Post by rraj.be on 2008-06-18
> **Jaxite said:**
> i just downloaded wine, it downloaded as a .tar.bz2 and i can't open it

the files dont really matter too much atm, i just need to fix the screen first


Than installing manually its better to go with typing 
```

sudo apt-get install wine
```

---

### Post by bufsabre666 on 2008-06-18
> **Jaxite said:**
> i just downloaded wine, it downloaded as a .tar.bz2 and i can't open it

the files dont really matter too much atm, i just need to fix the screen first
the screen res see: system->preferences->screen resolution

for the other one, you dont need to compile from source

go applications->accessories->terminal

then like others have said
```
sudo apt-get update && sudo apt-get install wine
```

some of you guys and dolls forget that not everyone knows, you need to explain to open the terminal first

---

### Post by Jaxite on 2008-06-18
the screen res see: system->preferences->screen resolution

I tried that, is that the same as setting manager>display ?
If it is, it just made things bigger..

---

### Post by mali2297 on 2008-06-18
> **Jaxite said:**
> still no luck =[

Is the font size very large?

You might need to edit the xorg.conf file. Press Alt+F2 to open a run dialog. Then type
```

gksudo mousepad /etc/X11/xorg.conf

```
This will open the file in an editor. Find the "Device" section, it looks something like this:
```

Section "Device"
        Identifier      "Something"
        Driver          "Something"


EndSection

```
Within this section add the line
```

        Option  "DDC" "No"

```
Save, quit and restart.

Based on the tag of the thread, I have assumed that you use Xubuntu. Is this right?

---

### Post by sisco311 on 2008-06-18
First try to enable the restricted drivers for your video card:
Application --> System --> Hardware Drivers

---

### Post by Jaxite on 2008-06-18
yes im using xubuntu
i just tried that what you said, 
this is the file 
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
        Option  "DDC" "No"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```
restarted, nothing happened..

---

### Post by aimpau on 2008-06-18
Just to "xubuntu-summarize"

1. You have to open what is called a "terminal" and type the codes they're giving you. Remember to put in your password, it will not show but its there.
2. Next, about the resolution, check first if it needs drivers:
Applications--->>System--->>Hardware Drivers
3. For resolution: system->preferences->screen resolution
4. Remember, when we said you should get "wine" we didn't intend for you to go to your web browser and download it as a file. The codes that were given to you would automatically do that and install that as well. Pretty neat!
5. Don't worry about your dad. You have 13659 active forum members here who are willing to help.

---

### Post by Jaxite on 2008-06-18
> **aimpau said:**
> Just to "xubuntu-summarize"

1. You have to open what is called a "terminal" and type the codes they're giving you. Remember to put in your password, it will not show but its there.
2. Next, about the resolution, check first if it needs drivers:
Applications--->>System--->>Hardware Drivers
3. For resolution: system->preferences->screen resolution
4. Remember, when we said you should get "wine" we didn't intend for you to go to your web browser and download it as a file. The codes that were given to you would automatically do that and install that as well. Pretty neat!
5. Don't worry about your dad. You have 13659 active forum members here who are willing to help.

Yeah i downloaded wine now so thats all done, installed winrar and stuff.
System>hardware drivers:
```

no Proprietary drivers are in use on this system

```

oh and heres a screenshot of my screen
[IMG]http://i30.tinypic.com/2zdu0bl.jpg[/IMG][

---

### Post by mali2297 on 2008-06-18
> **Jaxite said:**
> Yeah i downloaded wine now so thats all done, installed winrar and stuff.
System>hardware drivers:
```

no Proprietary drivers are in use on this system

```

Open a terminal and type (or copy/paste)
```

lspci | grep VGA

```
Post the output.

---

### Post by bijeeshvs on 2008-06-18
just enable the driver in there

can u post the configuration of ur laptop like the video card..............


dont worry

---

### Post by Jaxite on 2008-06-18
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

---

### Post by bijeeshvs on 2008-06-18
hello every one please show him the GUI way not the command way u people will freak away him with all those command line things , and some one coming from windows is not at all familiar with command line u may be familiar with it but not a newcomer.........

---

### Post by bijeeshvs on 2008-06-18
hey did you managed to solve it????????????????????????

---

### Post by mali2297 on 2008-06-18
In a terminal, type
```

sudo dpkg-reconfigure xserver-xorg

```
You will be asked a bunch of questions. Answer them as best you can. When asked for the graphics card, see if you can find SIS in the list and choose that. If you don't know the answer to a question, just go with the default and press Enter.

EDIT: You will be asked for your password. You won't see any stars or anything as you type it but don't worry, it is still read.

> **bijeeshvs said:**
> hello every one please show him the GUI way not the command way u people will freak away him with all those command line things , and some one coming from windows is not at all familiar with command line u may be familiar with it but not a newcomer.........

I would do that, but unfortunately I do not know how to solve this through the GUI.

---

### Post by Jaxite on 2008-06-18
> **mali2297 said:**
> In a terminal, type
```

sudo dpkg-reconfigure xserver-xorg

```
You will be asked a bunch of questions. Answer them as best you can. When asked for the graphics card, see if you can find SIS in the list and choose that. If you don't know the answer to a question, just go with the default and press Enter.

EDIT: You will be asked for your password. You won't see any stars or anything as you type it but don't worry, it is still read.



I would do that, but unfortunately I do not know how to solve this through the GUI.

it came up with stuff about the keyboard.. nothing about gfx card

---

### Post by mali2297 on 2008-06-18
> **Jaxite said:**
> it came up with stuff about the keyboard.. nothing about gfx card

I think SiS should be available, check that the package [xserver-xorg-video-sis]("http://packages.ubuntu.com/hardy/xserver-xorg-video-sis") is installed. Use the search function in Synaptic package manager.

---

### Post by Jaxite on 2008-06-18
it found it, i thinks its enabled and stuff?

---

### Post by mali2297 on 2008-06-18
> **Jaxite said:**
> it found it, i thinks its enabled and stuff?

But you didn't find SiS when you ran *sudo dpkg-reconfigure xserver-xorg*?

Perhaps you should check again.

---

### Post by Jaxite on 2008-06-18
i get
```

&#9474; Rather than communicating directly with the video hardware, the X   &#9474; 
 &#9474; server may be configured to perform some operations, such as video  &#9474; 
 &#9474; mode switching, via the kernel's framebuffer driver.                &#9474; 
 &#9474;                                                                     &#9474; 
 &#9474; In theory, either approach should work, but in practice, sometimes  &#9474; 
 &#9474; one does and the other does not.  Enabling this option is the safe  &#9474; 
 &#9474; bet, but feel free to turn it off if it appears to cause problems.  &#9474; 
 &#9474;                                                                     &#9474; 
 &#9474; Use kernel framebuffer device interface?                            &#9474; 
 &#9474;                                                                     &#9474; 
 &#9474;                  <Yes>                     <No>   

```
i click no:
```

 &#9474; The default keyboard layout selection for the Xorg server will be   &#9474; 
 &#9474; based on a combination of the language and the keyboard layout      &#9474; 
 &#9474; selected in the installer.                                          &#9474; 
 &#9474;                                                                     &#9474; 
 &#9474; Choose this option if you want the keyboard layout to be            &#9474; 
 &#9474; redetected.  Do not choose it if you want to keep your current      &#9474; 
 &#9474; layout.                                                             &#9474; 
 &#9474;                                                                     &#9474; 
 &#9474; Autodetect keyboard layout?                                         &#9474; 
 &#9474;                                                                     &#9474; 
 &#9474;                  <Yes>                     <No>  

```
no:
```

 &#9474; For the X server to handle the keyboard correctly, a keyboard       &#9474; 
 &#9474; layout must be entered.  Available layouts depend on which XKB      &#9474; 
 &#9474; rule set and keyboard model were previously selected.               &#9474; 
 &#9474;                                                                     &#9474; 
 &#9474; Experienced users can use any layout supported by the selected XKB  &#9474; 
 &#9474; rule set.  If the xkb-data package has been unpacked, see the       &#9474; 
 &#9474; /usr/share/X11/xkb/rules directory for available rule sets.         &#9474; 
 &#9474;                                                                     &#9474; 
 &#9474; Users of U.S. English keyboards should enter "us".  Users of        &#9474; 
 &#9474; keyboards localized for other countries should generally enter      &#9474; 
 &#9474; their ISO 3166 country code.  E.g., France uses "fr", and Germany   &#9474; 
 &#9474; uses "de".                                                          &#9474; 
 &#9474;                                                                     &#9474; 
 &#9474;                               <Ok>     

```
then ok&us:
```

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring xserver-xorg &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474; For the X server to handle the keyboard correctly, an XKB rule set  &#9474; 
 &#9474; must be chosen.                                                     &#9474; 
 &#9474;                                                                     &#9474; 
 &#9474; Users of most keyboards should enter "xorg".  Users of Sun Type 4   &#9474; 
 &#9474; and Type 5 keyboards, however, should enter "sun".                  &#9474; 
 &#9474;                                                                     &#9474; 
 &#9474; Experienced users can use any defined XKB rule set.  If the         &#9474; 
 &#9474; xkb-data package has been unpacked, see the                         &#9474; 
 &#9474; /usr/share/X11/xkb/rules directory for available rule sets.         &#9474; 
 &#9474;                                                                     &#9474; 
 &#9474; When in doubt, this value should be set to "xorg".                  &#9474; 
 &#9474;                                                                     &#9474; 
 &#9474; XKB rule set to use:                                                &#9474; 
 &#9474;                                                                     &#9474; 
 &#9474; xorg_______________________________________________________________ &#9474; 
 &#9474;                                                                     &#9474; 
 &#9474;                               <Ok>  

```
ok:
```

For the X server to handle the keyboard correctly, a keyboard       &#8593; 
 &#9474; model must be entered.  Available models depend on which XKB rule   &#9646; 
 &#9474; set is in use.                                                      &#9618; 
 &#9474;                                                                     &#9618; 
 &#9474;  With the "xorg" rule set:                                          &#9618; 
 &#9474;  - pc101: traditional IBM PC/AT style keyboard with 101 keys,       &#9618; 
 &#9474; common in                                                           &#9618; 
 &#9474;           the United States.  Has no "logo" or "menu" keys;         &#9618; 
 &#9474;  - pc104: similar to pc101 model, with additional keys, usually     &#9618; 
 &#9474; engraved                                                            &#9618; 
 &#9474;           with a "logo" symbol and a "menu" symbol;                 &#9618; 
 &#9474;  - pc102: similar to pc101 and often found in Europe. Includes a    &#9618; 
 &#9474; "< >" key;                                                          &#9618; 
 &#9474;  - pc105: similar to pc104 and often found in Europe.

```
(Theres more of it, just the same as above tho)
```

&#9474;                                                                     &#9474; 
 &#9474; For the X server to handle the keyboard as desired, a keyboard      &#8593; 
 &#9474; variant may be entered.  Available variants depend on which XKB     &#9646; 
 &#9474; rule set, model, and layout were previously selected.               &#9618; 
 &#9474;                                                                     &#9618; 
 &#9474; Many keyboard layouts support an option to treat "dead" keys such   &#9618; 
 &#9474; as non-spacing accent marks and diaereses as normal spacing keys,   &#9618; 
 &#9474; and if this is the preferred behavior, enter "nodeadkeys".          &#9618; 
 &#9474;                                                                     &#9618; 
 &#9474; Experienced users can use any variant supported by the selected     &#9618; 
 &#9474; XKB layout.  If the xkb-data package has been unpacked, see the     &#9618; 
 &#9474; /usr/share/X11/xkb/symbols directory for the file corresponding to  &#9618; 
 &#9474; your selected layout for available variants.                        &#9618; 
 &#9474;                                                                     &#9618; 
 &#9474; Users of U.S. English keyboards should generally leave this entry 

```
thats it =/

---

### Post by aimpau on 2008-06-18
I'm also using xubuntu and my VGA is this:
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

So I know it is working and so should yours.

---

### Post by Jaxite on 2008-06-18
well it's not =/
i might just go back to windows.

---

### Post by mali2297 on 2008-06-18
OK, my suggestion to use dpkg-reconfigure seems to be out of date. I think you can use a graphical tool called *displayconfig-gtk* instead to choose the driver.

In a terminal, type
```

gksudo displayconfig-gtk

```
and it should come up a window where you can specify your graphics card.

If it doesn't show, use Synaptic again to see if displayconfig-gtk is installed.

---

### Post by scorp123 on 2008-06-18
Try "Ubuntu" ... "Xubuntu" is quite spartanic IMHO (nothing wrong with that but a newcomer might be a bit overwhelmed with that). Ubuntu with its GNOME interface is way easier to use (e.g. the programs that setup screen resolution etc. are easier to find and IMHO seem to work better). If you still want to use XFCE as your graphical interface you could still install it later via Synaptic.

Also ... for a really *REALLY* really nice and beginner-friendly Linux, please try this one: 

Linux MINT 5 'Elyssa':
[http://www.linuxmint.com/mirrors.php?id=25](http://www.linuxmint.com/mirrors.php?id=25)

Make sure you really get the "Linux MINT 5 'Elyssa' Main Edition" ... because only this one will have all their tools which make it so beginner-friendly.

A review can be found here:
[http://www.distro-review.com/review-linux-mint-5-elyssa](http://www.distro-review.com/review-linux-mint-5-elyssa)

"Linux MINT" is a different distribution but it is based on Ubuntu ... basically the same way Ubuntu is based on Debian.

The reason why I recommend it here is that you might perceive it to be "friendlier" than pure Ubuntu. Please give it a try, OK?

---

### Post by beckols on 2008-06-18
For your own safety you might be better off reinstalling windows so you don't get into trouble :), but I would recommend sticking with linux via VMWare.  If you've never heard of vmware, this is what it does.  It's basically like having a separate computer and operating system that you can run from your current operating system.  It runs in a little window, and if you mess anything up, it can be restored to the original state with one click. For more information check out the site, [www.vmware.com]("www.vmware.com").  Although, if you want to stick it out, I commend you... the best way to learn linux is to be forced to learn linux by having it as your only OS.  If you really want to stick with linux I would recommend these (in order, start from the top):
[Terminal For Beginners]("http://ubuntuforums.org/showthread.php?t=73885")
[Learning the Shell]("http://linuxcommand.org/learning_the_shell.php")
[Writing Shell Scripts]("http://linuxcommand.org/writing_shell_scripts.php")

After that, you will have the knowledge to begin learning on your own.  Some good reference sites:
[www.tldp.org]("http://www.tldp.org/")
[The Linux Tutorial]("http://www.linux-tutorial.info/modules.php?name=MContent&pageid=224")
And of course, this site

---

### Post by Jaxite on 2008-06-18
>.<
I don't want to read all that stuff, all i need to know is why my screen resolution is how it is, and how to fix it.

---

### Post by scorp123 on 2008-06-18
> **Jaxite said:**
> >.<
I don't want to read all that stuff Linux is not Windows :D

Happy re-installing Windows then for you. Come back again when you grow up, OK? :)  Maybe you will appreciate this stuff more when you get older. :)

---

### Post by Jaxite on 2008-06-18
im saying there is no point in reading all that stuff that i already know/dont need to know.

---

### Post by scorp123 on 2008-06-18
> **Jaxite said:**
> im saying there is no point in reading all that stuff that i already know/dont need to know. Maybe.

But please read my posting above. You might find "Ubuntu" with its GNOME interface way easier to use. Or "Linux Mint" which might be better suited for you. At least give that a try. It's a live CD too so you can download it and take a look at how well it does on your system without installing it.

---

### Post by beckols on 2008-06-18
I definitely second that on trying ubuntu instead of xubuntu.  If you are adamant about trying out linux, then you should just go ahead and format and switch to ubuntu 8.04.  I have no experience with linux MINT but I've heard good things.  Ubuntu is still very user friendly though, and you sound like you have a decent amount of knowledge about computers in general so I don't think it will be too much of a problem as long as you use the resources at hand.  And I'm not saying you should read all of those RIGHT NOW, I'm saying if you are going to stick with linux you should gradually read those to gain a basic understanding of the OS.

---

### Post by Jaxite on 2008-06-19
Okay. i installed ubuntu, deleted xubuntu.
now ?
It's the same as it was with xubuntu, too big

---

### Post by mali2297 on 2008-06-19
> **Jaxite said:**
> Okay. i installed ubuntu, deleted xubuntu.
now ?
It's the same as it was with xubuntu, too big

Can you open displayconfig-gtk? See my earlier post. It might also be available through the menus as *Screen and Graphics Preferences*.

---

### Post by Jaxite on 2008-06-19
yes i can access it.
what settings shall i put it as?

---

### Post by russlar on 2008-06-19
> **Jaxite said:**
> yes i can access it.
what settings shall i put it as?

whatever settings you want. if the stuff on the screen is too big, then your resolution is too low.

---

### Post by cmnorton on 2008-06-19
As to your screen resolution, that may be easily fixable. I am familiar with Kubuntu and Ubuntu, but not xubuntu. Somewhere, perhaps at the top of your screen, there is a menu item that might say System. 

If there is, click on that, select an item like Preferences, and see if display is located there. If you click on that, you can probably change your screen resolution. If you are asked for a password, use the password of your user account, the one you used to log in.

As to the Microsoft applications not running, you seemed to have gotten a good answer. 

Just take this one step at a time, and you should be okay.

---

### Post by mali2297 on 2008-06-19
> **Jaxite said:**
> yes i can access it.
what settings shall i put it as?

See if you can specify SiS as the graphics card.

---

### Post by Jaxite on 2008-06-19
ok i set it as sis, nothing happened
then i reopened it and it came as: 'vesa - generic vesa-complaint vid..'

---

### Post by mali2297 on 2008-06-19
I have dug in the forums and found other posts that describe problems with SiS cards. There might be solution here:
[http://ubuntuforums.org/showthread.php?t=615094&page=3?post=#71](http://ubuntuforums.org/showthread.php?t=615094&page=3?post=#71)
Try to follow the steps. The code shall be entered in a terminal.

If you need more help, don't be afraid to ask.

EDIT:
I just read this:
> N.b. if you run displayconfig-gtk again, it will say that you are using Vesa, and so will xorg.conf, but that's not true, as X autoconfigures itself to use sis.
Before anything else, try restarting Ubuntu. It might be enough.

---

### Post by Jaxite on 2008-06-20
didn't work, =[

---

### Post by Het Irv on 2008-06-20
Another suggestion that might make it easier for you:
Reinstall Windows so that whoever else needs to use the computer/laptop can use it.  Then install Ubuntu through Wubi, this allows you to have two Operating Systems on a computer at the same time, although you cannot run them at the same time.  This will allow you to learn how to use Ubuntu at your own pace with out being rushed.  Once you feel confident then you can explore other ways of installing.

To install Ubuntu with Wubi, just pop in the Live CD while you are in Windows and follow the menus.  It is extremely simple so you shouldn't have any problems.

---

### Post by Jaxite on 2008-06-20
>.<
Have i not explained that i don't want to use wubi..
becuase i dont have enoughram..

---

### Post by mali2297 on 2008-06-20
> **Jaxite said:**
> didn't work, =[

Did you get through all the steps without any error messages?
If not, tell us what you did and where it failed.

---

### Post by Het Irv on 2008-06-20
No, you didn't.  There is another way to accomplish the same effect as Wubi.  You could set up a Dual-Boot.  The only difference between a dual-boot and Wubi is that Ubuntu will be in its own partition.
Here is a great How-To:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by mali2297 on 2008-06-20
Another idea...

Open xorg.conf in an editor
```

gksudo gedit /etc/X11/xorg.conf

```
Add the bold text to the "Monitor" section:
```

Section "Monitor"
	Identifier	"Configured Monitor"
        [b]HorizSync 28-72
        VertRefresh 43-60[/b]
EndSection

```
Save and exit the editor.

To see if it works, press Ctrl+Alt+Backspace to restart the graphical user interface (quicker than rebooting).

---

### Post by trevelyan on 2008-06-20
i had the same problem with Ubuntu. i dont know if it will work with Xubuntu but maybe it does.

the way i soved this was:
browse your hard drive and navigate to:
```
/usr/share/applications
```
look for "Screens and Graphics" and double click it to open it.

on the "screen" tab click on the "Model:" bar and select an LCD with the native resolution for your monitor. then on "Resolution" bar select the resolution you want.
click OK and log out and back in for the changes to take effect.

let me know if that helped. to then talk about the programs you can use.

---

### Post by +Eric on 2008-06-20
> **Jaxite said:**
> >.<
Have i not explained that i don't want to use wubi..
becuase i dont have enoughram..

Actually, it requires no more ram than a regular Ubuntu Installation would.....

Reference:
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

A little more than half way down:
> 
             **[SIZE=3]Is this running Ubuntu within a virtual environment or something similar?[/SIZE]**

             No. This is a real installation, the only difference is that Ubuntu is installed within a file as opposed to being installed within its own partition. Thus we spare you the trouble of creating a free partition for Ubuntu. And we spare you the trouble to have of having to burn a CD-Rom.
This is to say that it's not running ubuntu on top of windows, it's basically making dual booting VERY easy however probably sacrificing a tad bit of performance since Ubuntu won't have it's own partition.....

In fact, this was how I started out with Ubuntu just a few months ago on my laptop. I have no moved both my laptop and desktop to Ubuntu in a true dual boot setup with Windows. But Wubi was just fine for me on my laptop, although I do feel there was a slight performance boost after I moved away from Wubi.

Wubi may be a viable option for you since you may still have some things you'd like to do in windows anyway!

Stick with it, it's worth it, and good luck!

---

### Post by pmlxuser on 2008-06-20
> **ubuscout said:**
> ...dont'be afraid about your choice ! ;-)   ..u have choosen the best way... maybe u'll find some difficult at first... but with patience (u need only of this), u will workaround everything with ubuntu ;) !

For the windows application, wine is one of the best way... but not always u can run every application...  with little bit more experience you could try in the next also virtualization windows (ie virtualbox) maybe for more critical windows application...

btw for wine syntax is something like this:
wine "/your-application-path/your-application-name"



good luck :)

i depends doesn't it, He will "kill you" if its His computer you messed up. But if its yours just tell Him its for a "science project" you are doing till you figure out a way of dealing with all your current problems

As you will find out that NOT all windows application work with WINE

---

### Post by mike2357 on 2008-06-20
Step 1:  Tell your dad the truth
Step 2:  Work with him to resolve whatever computer problems you happen to be having.  It might be fun for you to work together.  If anything, he'll soon understand the value of frequent backups.

I have an 11-year old myself.

---

