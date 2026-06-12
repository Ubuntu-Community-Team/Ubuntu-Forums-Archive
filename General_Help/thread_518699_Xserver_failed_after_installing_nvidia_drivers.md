---
title: "Xserver failed after installing nvidia drivers"
date: 2007-08-06
forum: General Help
---

### Post by J.One on 2007-08-06
Hello guys, need some help here

Problem:
I didn't have any boarders on any window manager except Aquamarine and i was thought that there is a driver update wich i did. (I had restricted drivers). I had them installed in a wierd combination between Envy and Automatix wich i cannot remember.
After uninstalling drivers from Envy again (wich i think was not a clean unninstal, despite i couldn't get into the Restricted Driver Menu because a got a message "You don't have restricted drivers", i reboot and i got a Xserver Fail.
So i went on GRUB and i install manually nvidia drivers with                                            
                                           sudo NVIDIA-Linux-x86_64-100.14.11-pkg2.run

All went well till next restart wich Xserver couldn't be loaded...

Any ideas how i can work this again? Because i have many things on my hard drive wich i cannot perform a clean install of Ubuntu..

System Running:
Amd64 3500+ GeForce XFX 6600 GT 256 with 1024 RAM 
Platform:
Ubuntu Feisty AMD64 Version.

---

### Post by Saner on 2007-08-06
whats the X error ?

Change the /etc/X11/xorg.conf


> 
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Unknown"
EndSection


Too


> 
Section "Device"
    Identifier     "Videocard0"
    Driver         "vesa"
    VendorName     "NVIDIA Corporation"
    BoardName      "Unknown"
EndSection



and X should load.

I would remove the restricted drivers etc... and all the crap associated with that and then manually install the Nvidia ones.

It worked fine for me doing it that way with a XFX 6600 256 (note not the GT version)

You will also need to install the kernel-header files for your kernel.

---

### Post by J.One on 2007-08-06
i will reconfigure xserver with "vesa" this time instead of "nvidia" i was entering before, but can you plz tell me a sure way how to install manually nvidia drivers? Is there a chance of leaving a file of previous installation with Envy or Automatix and corrupt with the new one after manually installation? If yes how can i make a clean UNinstall?

---

### Post by dragonwings on 2007-08-06
sudo aptitude install nvidia-glx-new

for latest drivers

sudo dpkg-reconfigure xserver-xorg

to configure xserver :Note my have to be done in recovery mode

if any problems with window frames eg:terminal window all white and unuseable just untick 
desktop effects wobbly windows and cube 

all should be good :Note may take a few goes depending on your skill .
took me 3 goes before i got it 

GOOD LUCK

---

### Post by J.One on 2007-08-06
Saner! You are a SAVIOR! It worked after putting "vesa" instead of "nvidia" but plz tell me a way how to clean unninstall all crap that i have installed through Envy and Automatix and a sure way to install manually nvidia drivers to have all things working fine again....

Any help will be Gratefull!

---

### Post by Saner on 2007-08-06
Dunno to be honest (I know its not much help)

I always manually install my drivers, so I have never had to remove them.

You could try synaptic package manager to see if they are listed there.

---

### Post by J.One on 2007-08-06
Gimme your msn to have an instant contact if you want and provide you with any help i can also :)

---

### Post by Saner on 2007-08-06
I cant at the moment, I am re-installing my dedicated server, so I am busy.

But if no one else can help, I may be about later you can add me

insane @ h0td.com

(without the spaces)

---

### Post by dragonwings on 2007-08-06
go to system on desk top
then
administation
then
synaptic pakage maneger
click search
and search for envy or what ever you want to get rid of

when you find it right click on it and mark for complete removal

that should do it

good luck

---

### Post by J.One on 2007-08-06
Dragonwings thnx for the advice but i have a question..
After getting rid of all envy stuff, it will erase only the programm or the drivers it has installed also? Because my concern is to delete all files that have been installed with restricted drivers so to do not conflict when i try to install legacy driver...

---

### Post by Steve1961 on 2007-08-06
> **J.One said:**
> Saner! You are a SAVIOR! It worked after putting "vesa" instead of "nvidia" but plz tell me a way how to clean unninstall all crap that i have installed through Envy and Automatix and a sure way to install manually nvidia drivers to have all things working fine again....

Any help will be Gratefull!

I've never used envy or automatix, but from a terminal you could try the following:

sudo nvidia-installer --uninstall

Then just:

sudo apt-get install nvidia-glx

and edit /etc/X11/xorg.conf and replace vesa with the word nvidia.

---

### Post by dragonwings on 2007-08-06
to be honest im not 100% on that 
but i used that method to uninstall my wine windows emulater and it did the job 
i cant see why it wont work for you?

and when you install latest driver it should get rid of the old one anyway

---

### Post by J.One on 2007-08-06
when i typed sudo apt-get install nvidia-glx it said that non package installed because i have the newest version etc...But how this is happening? I uninstall them first with the above command you gave me...
Also after restarting i got Xserver fail again because it need to be "vesa" and not "nvidia"..
When i reconfigure X from grub and put "vesa" instead of "nvidia" is loging in ok.
But still no drivers and of course no 3d

---

### Post by Steve1961 on 2007-08-06
> **J.One said:**
> when i typed sudo apt-get install nvidia-glx it said that non package installed because i have the newest version etc...But how this is happening? I uninstall them first with the above command you gave me...
Also after restarting i got Xserver fail again because it need to be "vesa" and not "nvidia"..
When i reconfigure X from grub and put "vesa" instead of "nvidia" is loging in ok.
But still no drivers and of course no 3d

Open synaptic and remove the nvidia glx or nvidia glx new package.  Then reinstall nvidia glx or nvidia glx new.  Change vesa to nvidia in your xorg.conf file.  Make sure desktop effects are turned off, and restart x (ctrl-backspace).

---

### Post by dragonwings on 2007-08-06
with synaptic package maneger serach nvidia
and see whats there  mark for complete removal 

the coomand for the newest driver is

sudo aptitude install nvidia-glx-new

then type

sudo apt-get update

 to update

when in xorg set to vesa 

then in the desktop administration click restricted driver activate it 

may need to re do xserver and set to nvidia  insteed of vesa 

just keep trying and youll get there

---

### Post by Steve1961 on 2007-08-06
One more thing.  I just upgraded to nvidia-glx-new from nvidia-glx and had to reboot for the settings to take effect - got the standard error message when I just tried restarting the x-server.  Once you're up and running you can add the extra entries for desktop effects.  This is my xorg.conf:

Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
    Option      "RenderAccel"   "1"
    Option      "AllowGLXWithComposite" "1"
    Option      "RandRRotation" "1"
    Option      "AddARGBGLXVisuals"     "1"
    Option      "DisableGLXRootClipping"        "1"
    Option      "TripleBuffer"  "1"
    Option      "UseEDID"       "1"
    Option      "UseEdidFreqs"  "1"
    Option      "DynamicTwinView"       "0"
    Option      "IgnoreDisplayDevices"  "TV"
    Option      "Coolbits"      "1"
#       Option      "UseEdidDpi"   "FALSE"
    Option      "DPI"   "96 x 96"

---

### Post by J.One on 2007-08-06
Guys, i will be gratefull, you gave me much help that i couldn't make it through here...Despite all these, i still have no boarders on windows at all window decorator managers except Aquamarine KDE (i run gnome, don't think is there a problem with this).....

If you can find me a solution to these boarders.....then.........thnks!

---

### Post by dragonwings on 2007-08-07
my only other thought is it may be to do wiih open gl   ??
maybe a recent programe install conflict such as k9 or kb3 deved  etc??
try disabling open gl ???
sorry i cannt be more help im all outa ideas .???

---

### Post by J.One on 2007-08-07
Nevermind Dragonwings, i will stay like this (beryl & Aquamarine) till something new comes up...
H read about KDE4...take a look, can't remember the url right now.

---

