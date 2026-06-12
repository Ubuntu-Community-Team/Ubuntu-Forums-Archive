---
title: "Windows apps under wine"
date: 2007-07-29
forum: General Help
---

### Post by dragn on 2007-07-29
So far I have not been able to get any windows apps to run under wine.
Some install and others don't thats to be expected but the one's that do have me stumped foe ex: Power DVD"
It installs and shows in the system and creates shortcuts but just wont run and no error messages to go by.



Crash the Gates and smash the Windows

---

### Post by astralsin on 2007-07-29
there are alternatives to power dvd.  try vlc, i like it much better than any other player out there. 

sudo apt-get install vlc

---

### Post by FluffyElmo on 2007-07-29
Wherever possible you should try to find an Ubuntu equivalent to Windows programs since they'll generally be faster and more stable than running Windows applications under Wine. In the case of DVD playing you have to install the css library to read encrypted DVDs but then there are a range of good players to use like VLC, MPlayer, Xine or the built in Movie Player (Totem). 

Check here for instructions on how to read enable DVD playback:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability")

If there are Windows programs you have to run then you might want to try Wine-doors which provides a GUI to install a lot of common Windows programs, there is an Ubuntu package for it here: [http://www.ubuntuessentials.net/2007/07/23/finally-an-ubuntu-package-for-wine-doors/]("http://www.ubuntuessentials.net/2007/07/23/finally-an-ubuntu-package-for-wine-doors/")

---

### Post by dragn on 2007-07-29
I followed all instructions right down to the cut and paste of commands at terminal.
The best I get is choppy audio from VLC.
I was only using Power DVD as an example

.sudo apt-get install libdvdread3 
sudo /usr/share/doc/libdvdread3/install-css.sh
sudo apt-get install totem-xine

sudo apt-get install libdvdcss2

MPLAYER says no device

TOTEM says: The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

VLC not responding

---

### Post by DalekClock on 2007-07-29
I use Ogle for DVDs. You can find it under Add/Remove.

Apart from that, the only suggestion I can think of that doesn't require a Windows liscence if forking out on CrossOver, which is not an option if you're out of cash, not willing to test it out or just don't want to pay for software.

---

### Post by dragn on 2007-07-29
I finally got it working!!
There was a conflict with some of the packages I installed so I scaled it back some by removing all unneeded  
apps even some that came with the install  except core stuff like Firefox and Office and Evolution.

Now on to the next stage...finding Linux apps that do what I was doing under Windows :)
If anyone has any software suggestions I would be greatfull
TV capture  (hopefully to MPEG)
Guide plus   
Video editor

Crash the Gates and break the Windows

---

### Post by Tobster on 2007-07-29
I'm not doing the sales thing but in my own experience CrossOver is worth using with Windows applications but it does cost around $20 USA but on the other hand they do pass on codes to WINE so it worth it

---

