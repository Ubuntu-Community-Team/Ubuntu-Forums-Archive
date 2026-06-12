---
title: "[SOLVED] Enegizer Duo Installition"
date: 2007-10-15
forum: General Help
---

### Post by selman_akinci on 2007-10-15
I just installed Ubuntu yesterday for the first time. And now i am in shock to see that such diffrent things in this operation system... First thing i need to solve is opening .exe installition files for my programs, drivers..... I heard about wine but there is no link or such where i can download the .zip file or whatever..... I am pretty impressed wit ubuntu.... If this system had no difficulty opening any windows programs i would never install windows...

I bought my enegizer duo battery charger but it has no download for ubuntu... can i install it anyway? can i open the .exe in any way?

remember i am 1 day in this system, plz tell me what to do...
here is the link i am trying to work in ubuntu:
[ http://energizer.com/usbcharger/language/english/download.aspx]("http://energizer.com/usbcharger/language/english/download.aspx") :confused::confused::confused::confused::confused:
Plz help me with this system i read about switching from windows but that help only explains importing stuff which is useless..... it never explains like , here in ubuntu boot is like the windows folder and root is like system32 and grub is the documents and settings....... 

I dont even understand where this thing installs the things,.....

---

### Post by greenstar on 2007-10-17
Take your time and go easy, you'll catch on to how things work in Ubuntu. 

I'll try to help. 

1.) Plug the charger into your usb port and see if it charges your batteries. It may not need any more setup than that.

2.) The energizer program seems to be just an on-screen display of charging progress, so don't worry about the .exe for now. There's probably also an LED indicator on the charger itself that will tell you the same thing. 

3.) Installing software in Ubuntu isn't like installing software in Windows. I can help if you tell me what kind of software you want to install.

4.) [B][U]Windows                     =    Ubuntu
[/U][/B]     C:                                =       /  
     Documents & Settings  =    /home
     User Directory              =    /home/your-username/
     My Documents             =    /home/your-username/Documents
My Pictures = /home/your-username/Pictures

Those last two might need to be created, simply right click and select Create Folder at the top of the context menu.

Note: /home/current_logged-in_user is abbreviated as ~, you can see this by opening a terminal Applications->Accessories->Terminal and type ~/Des then hit [Tab] and you'll see that it autocompletes the Desktop directory of the current logged in user. ~ is called a tilda. So, if I do ~/Des then [Tab] in Terminal on my box I get:
```
brandon@Stormtrooper:~$
brandon@Stormtrooper:~$ ~/Des
brandon@Stormtrooper:~$ ~/Desktop/
```Greenstar

---

### Post by greenstar on 2007-10-18
Did this solve your problem? If so, please mark your thread solved. Instructions are in my signature block.

Greenstar

---

### Post by SoloSalsa on 2008-07-11
Dude, I just found that charger at Menards today for like super sale half price!  A plain two-cell charger would not be worth it, but: (1) computer charge progress metre (2) very good design (3) little mains to USB jack.  This sounded like an INCREDIBLE device, so I got it.  I have not tried the charge indication software yet, but I'll come back later with my attempt...

In the mean time, you still need WINE!  Don't mark that thread solved, until you get what you came for.  Sure, Greenstar gave you some basic orientation to file hierarchy, but your first and primary concern was the charger, not folder structure...

So, to get WINE...  I'm positive that this has been covered at least once before around the forums (did you search for "WINE install" yet?), but I'll try to give a quick how-to.

In the System menu, in the Administration sub menu, launch Synaptic Package Manager.
In Synaptic, find wine.  Either run a search for it, or go down through the gigantic list of everything until you find it.  It will be called "wine", no prefixes or suffixes.  When you've found wine, either alternate-click it and "Mark for Installation" or click the square next to its name and then choose "Mark for Installation".  Then, the final step: in the button bar, choose Apply.

When WINE is installed, Windows executables should open in WINE by default.

EDIT:
I am no master at WINE configuration...  With all automatic default stuff, I could not get the charger thing working.

---

