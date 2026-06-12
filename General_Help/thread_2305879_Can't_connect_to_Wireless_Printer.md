---
title: "Can't connect to Wireless Printer"
date: 2015-12-10
forum: General Help
---

### Post by Davekyn on 2015-12-10
I am using Ubutnu 14.04 on a note book as part of a wireless home network.  Currently having issues connecting to our Samsung CLX-3305FW Wireless Printer.

I have been doing the following:  Whilst having turned on the printer/warmed up.

1. System Settings -> [IMG]http://i181.photobucket.com/albums/x30/davekyn/System%20Settings_003_zpsfvu0y9uu.png[/IMG]

2. I then CLICK + ADD  (and or the other add button [seems to do the same thing]) -> [IMG]http://i181.photobucket.com/albums/x30/davekyn/Printers%20-%20localhost_004_zpsk41f0qr9.png[/IMG]

3. which leads to this -> [IMG]http://i181.photobucket.com/albums/x30/davekyn/New%20Printer_005_zpssfylflqu.png[/IMG]

4. then this -> where is hangs and does nothing -  [IMG]http://i181.photobucket.com/albums/x30/davekyn/New%20Printer_006_zpsxqkaap7f.png[/IMG]
The Forward Tab stays greyed out, whilst the screen remains static and goes no further.
_______________________________________________________________________________________________________

I have downloaded a Linux Drivers for the printer form the Samsung Site.  
The file is a tar.gz.  [IMG]http://i181.photobucket.com/albums/x30/davekyn/Selection_008_zps42fvmmc8.png[/IMG]

I extracted it, but know not what else to do. [IMG]http://i181.photobucket.com/albums/x30/davekyn/uld_007_zpsmv3zbgkh.png[/IMG]

Please advise in a step like manner as to where I should go next and I will continue to feed back likewise.

KISS is the best approach.  Even then it still goes over my head. ;)

---

### Post by leunam12 on 2015-12-10
It seems that running install.sh installs both the printer and the scanner; then you have install-printer.sh and install-scanner.sh and for all of them their respective uninstallers. If you want to install both this is what I would do:

First I would backup my system, then...
1- Open terminal (Ctrl+Alt+T).
2- Type (press enter after each line command) ```
cd Downloads/uld/
```
3- Type ```
chmod +x install.sh
sudo ./install.sh
```
Follow any promts.
That should take care of it.

---

### Post by howefield on 2015-12-10
After doing the above, at stage 3 as per your images, try putting the IP of the printer into the Host field if the printer isn't found automatically.

The forward button should then become active.

---

### Post by kurt18947 on 2015-12-10
> **leunam12 said:**
> It seems that running install.sh installs both the printer and the scanner; then you have install-printer.sh and install-scanner.sh and for all of them their respective uninstallers. If you want to install both this is what I would do:

First I would backup my system, then...
1- Open terminal (Ctrl+Alt+T).
2- Type (press enter after each line command) ```
cd Downloads/uld/
```
3- Type ```
chmod +x install.sh
sudo ./install.sh
```
Follow any promts.
That should take care of it.

That is my experience. I did find that the scripts are executable when downloaded. If I copied the folder to removable storage then back again they lost the execute permission. I'm a little surprised that davekyn's printer wasn't just found when he clicked on 'find network printer'. The last time I installed a new distro, the printer and drivers were found, no downloads necessary. I am using the alternative printer utility -- system-config-printer but I don't know that it matters. I also assigned a static I.P. address to my printers but again I don't know if that makes a difference.

---

### Post by Davekyn on 2015-12-10
Good & Bad News. :)

1stly, [COLOR=#ff0000]Thank you[/COLOR] for your timely responses.  

It turns out that the other windows computers in the house could also not connect to the wifi printer.  The connection between the printer and router seem to no longer be working.  My wife, whom is more tech savy than I, is now working on the problem.  The others in the house need a working printer.  Once they have connected to the printer I will try again.  

I note my wife mentioned that our printer has a Dynamic IP and not a static one.  I will ask if she is able to make it static if after my next attempt to find printer fails.
___________________________________

WHAT I DID DO before finding out the printer and router had issues, was follow the advice given here.  TY for that.  Your instructions helped me to install both the files as directed.  I enjoy learning to use the terminal.  Hopefully adding the printer driver when perhaps was not necessary will not corrupt the system somehow.

I note you did say **back up system**, however to me as a new Linux User ... Whilst that is no doubt sound advice (TY for it) ... that sounded like more hours and further book reading.  I admit, that I did not do any back ups.  (have no idea, but will soon learn enough, when I get sick of reinstalling the OS)   

Fact is - I have come to learn with my windows installations, especially when you don't have much installed ... that as a Newbie to whatever applications, that reinstalling the OS is just as quick to rectifying what one does not understand.  I also learn a lot with each installation.  Of course, the more I have set up an OS, the more practical backing up becomes.  Sometimes such is an excuse for being lazy and others times it's not. :)
__________________________

I'll get there.  Anyways, I got more posts to make. LOL - Bluetooth keyboard is next, after I nail this one in the but. ;)
Back soon enough.

PS - THANKS FOR KEEPING IT SIMPLE. I had issues taking on the information provided within the Fedora Forum.[SIZE=1]* (straight over my head with much of the info assuming I knew way more than I did)*[/SIZE]
I can already tell my experience is going to be far more welcoming in this here forum instead.

PSS [I]- Ubuntu has picked up everything for me thus far!!!  I'm tethering off my phone as well and pretty much doing everything I was before when using windows.  I'm really impressed with how Ubuntu has come along.  Been like 10 years since I last tried it out.

____
[/I]

[IMG]https://farm6.staticflickr.com/5631/23033655333_c3654c53fa_n.jpg[/IMG]

The problem was entirely in the printer.  We have also now made static IP as well. 

At any rate ... Thx again. ;)

---

