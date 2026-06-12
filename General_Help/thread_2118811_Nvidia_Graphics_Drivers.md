---
title: "Nvidia Graphics Drivers"
date: 2013-02-22
forum: General Help
---

### Post by Howie1992 on 2013-02-22
Hello. I am new to the forums and kind of new to Ubuntu and I am having a problem when trying to install Experimental 310 drivers. My laptop specs are:

Sony Vaio VGN-AW290J/AH
Intel Core 2 Duo 2.66 Ghz
2 Gb Ram (had a stick go out. Getting a new one soon as it is standard 4gb ram)
Nvidia GeForce 9600M GT
Ubuntu 12.04 32bit (fully updated)

I am using the Nvidia Current-update driver right now. If it helps when I had to get my driver for windows I had to get them directly from the Sony website as I couldn't get any from Nvidia's website. Last time I tried to get the Experimental 310 my Ubuntu crashed and I couldn't load up afterwards and had to reinstall Ubuntu. If I cant can I still play Serious Sam 3 BFE from Steam?

---

### Post by JiuJitsu500 on 2013-02-22
I had trouble with the 310 version too, it's the first experimental version that broke my system actually.

But, the following PPA is one of the most trusted in the debian repo's and is maintained by a few cononical employees. It gets you the latest stable nvidia drivers with every update you do so you don't have to keep downloading new ones every time one is released by nvidia. They also maintain the ATI drivers, so the PPA has quite a few packages.

Simply run these three commands:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings

After every update again, it will upgrade your driver if it's in this PPA. Serious Sam 3 should be no problem at all.

---

### Post by Howie1992 on 2013-02-22
Thank you very much! I will try this route and see what happens. :D Though I do have to ask how many times will I need to run this command line? Just once until a new driver comes out or what?

---

### Post by Howie1992 on 2013-02-22
Ok. I ran the three commands and on the last one this popped up:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-current : Depends: xorg-video-abi-11
                  Depends: xserver-xorg-core (>= 2:1.10.99.901)
E: Unable to correct problems, you have held broken packages.

And according to steam it updated to driver version 304.64-0ubuntu0.2

---

### Post by dino99 on 2013-02-22
which ubuntu are you using ?

---

### Post by Howie1992 on 2013-02-22
12.04.2 32bit

---

### Post by dino99 on 2013-02-22
so have you a working system (with "nouveau" driver) or is it broken ?

if broken, boot in recovery mode : hold "shift" key down at bios end process to get the grub menu, select the second line to load the "recovery mode"

there, select network activation, then the root console (latest choice) and run:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install -f
(if you get an update packages proposal, then do the upgrade)

sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it yourself)

then type "exit" to get back the main menu, and choose the first choice

---

### Post by Howie1992 on 2013-02-22
It all seems to be working fine as far as I can tell. I can run CS:S and HoN load up just fine. I was asking about Serious Sam 3 because I didn't want to pay for it and then not be able to play it.

---

### Post by dino99 on 2013-02-22
so what's about your first request ?
** I am having a problem when trying to install Experimental 310 drivers. ****

and now you're asking something else  :confused:

is it a fake ?

---

### Post by Howie1992 on 2013-02-22
I asked both questions if you read it more closely. And I still cant get the 310 drivers to install. They refuse to but it isn't that big of a deal. I just figured that I would ask for help since I couldn't get them to install myself. And as far as it being broken I don't understand what you meant by that as I said I am fairly new to Ubuntu as far as this graphics things go as before all I used it for was web browsing on my previous uses of it. Right now the system is working fine as I can still do everything just fine as I was checking on getting the 310 drivers as Serious Sam 3 said it requires 310 minimum according to Steam but I have had several games say they have a certain minimum and then run on something below that. This is a serious help thread but you have to realize that I am new and dont understand what I am being asked. I have no problems loading up my system and as far as I can tell the command lines that JiuJitsu gave me did update my drivers but not to 310 thus why I posted how far it went.

---

### Post by Subv3rse on 2013-02-22
The Experimental 310 drivers (which work flawlessly (if you exclude the previous need to install linux-headers) in 12.04, 12.04.1, 12.10 and both x86 and x64 bit versions are very broken in 12.04.2 at the moment. I've been noticing this myself on all 'buntu builds currently.

Trying to find a fix isn't really yielding any useful information at the moment. Not sure what they've managed to do this time round.

-Subv3rse

---

### Post by Subv3rse on 2013-02-23
I've managed to get the 310 drivers working now. Steps to reproduce (As i'm not sure whether it was only one element or a combination that fixed it):

Installed Ubuntu 12.04.2 (x86)
Installed build-essential, linux-sources, linux-headers-`uname -r`
Ran a dist-upgrade
installed Steam

I don't know how important the previous elements are to this, but I remember from previous installs that Steam also installs jockey and both the 304 and 310 nvidia drivers, therefore I suspect the installation of Steam is all that's required to make this work in 12.04.2

Regardless, it auto-magically switched from using 304 to 310 without my intervention; which was a touch odd.

-Subv3rse

---

