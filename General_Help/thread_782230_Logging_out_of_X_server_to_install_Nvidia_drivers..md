---
title: "Logging out of X server to install Nvidia drivers."
date: 2008-05-04
forum: General Help
---

### Post by MechWarrior001 on 2008-05-04
Any help?

I'm trying to install nvidia drivers so i trype "sudo -i <nvidia driver package name>.run" into the terminal and it says i have to exit X Server to install. Some help please.

---

### Post by AmishFury on 2008-05-04
simple solution.... use Envy

---

### Post by Tatty on 2008-05-04
I would highly reccomend using the hardware drivers manager (system->administration->hardware drivers) or envy (from the repos) rather than installing the driver manually.

But if you want to do it manually then:

1. Switch to a different tty console with ctrl+alt+F1
2. Stop X with sudo /etc/init.d/gdm stop
3. Install drivers with sudo _sh_ <nvidia driver package name>.run
4. Start X and gnome again with sudo /etc/init.d/gdm start

---

### Post by madjr on 2008-05-04
> **AmishFury said:**
> simple solution.... use Envy

+1 to envyNG 

oh and this's the wrong forum section.

---

### Post by MechWarrior001 on 2008-05-05
Yeah see the thing is I don't have internet access on my Linux comp so I'm using this one, So the problem is I can't get the driver off the repositories, as well as download envy. 

P.S. Do I have to use the *nvidia-glx-new *specifically or can I use the one off of the nvidia website?

P.S.S Which forum does this belong in?

P.S.S.S What is X Server anyways?

---

### Post by FuturePilot on 2008-05-05
You can use the one from Nvidia's website, however you're also going to need to install some dev packages so it can compile the kernel module. X is the graphical environment that your Desktop Environment runs on top of. Without X you just have a terminal. 

I think in your case it would be easier to download the Ubuntu package [here]("http://packages.ubuntu.com/hardy/i386/nvidia-glx-new/download") and just install that. Best way would be to move it to /var/cache/apt/archives/ and then open the Hardware Drivers under System&#8594;Administration and install it.

---

### Post by aktiwers on 2008-05-05
[http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735](http://ubuntuforums.org/showthread.php?p=4105735&posted=1#post4105735)

---

### Post by swoll1980 on 2008-05-05
Envy ng works flawlessly

---

### Post by MechWarrior001 on 2008-05-05
> **FuturePilot said:**
> You can use the one from Nvidia's website, however you're also going to need to install some dev packages so it can compile the kernel module. X is the graphical environment that your Desktop Environment runs on top of. Without X you just have a terminal. 

I think in your case it would be easier to download the Ubuntu package [here]("http://packages.ubuntu.com/hardy/i386/nvidia-glx-new/download") and just install that. Best way would be to move it to /var/cache/apt/archives/ and then open the Hardware Drivers under System&#8594;Administration and install it.

I tried the link, but its for I386. Any packages for a AMD Sempron 3100+?

---

### Post by FuturePilot on 2008-05-05
[Here you go]("http://packages.ubuntu.com/hardy/amd64/nvidia-glx-new/download")

---

### Post by MechWarrior001 on 2008-05-05
Now its saying that the connection timed out every time I click the link.

---

### Post by FuturePilot on 2008-05-05
Hmmmm. It works here.
Here's a direct link to a package
[http://mirror.mcs.anl.gov/pub/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.12-16.34_amd64.deb]("http://mirror.mcs.anl.gov/pub/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.12-16.34_amd64.deb")

---

### Post by lswest on 2008-05-05
also, the command to kill X is simply ```
sudo /etc/init.d/gdm stop # for ubuntu
sudo /etc/init.d/kdm stop # for kubuntu
sudo /etc/init.d/xdm stop # for xubuntu
``` and then to start it just change "stop" to "start"

---

### Post by MechWarrior001 on 2008-05-05
Ok I entered the Linux Terminal using Ctrl+alt+F1, so I run the install file.
 
Now it says no precompiled kernel interface. (I don't have internet on my Ubuntu comp yet)
 
I am using:
 
AMD Sempron 3100+, Nvidia NFORCE 3-A, DDR400 1.5 GB RAM, Nvidia 7800 GS AGP, X-Fi Sound Blaster.
 
So I hit that and it tries to make a kernel interface but says:
 
"unable to load kernel module 'nvidia.ko'" 
 
Please give some HELP!

---

### Post by lswest on 2008-05-06
i'm pretty sure you'll need internet for this, then you have to do: ```
sudo apt-get install build-essential
``` and then try to compile a kernel manually, which (i believe) also requires internet.

---

### Post by MechWarrior001 on 2008-05-06
>  		i'm pretty sure you'll need internet for this, then you have to do:  	Code:
 	sudo apt-get install build-essential 
 and then try to compile a kernel manually, which (i believe) also requires internet.

No Offense to Hardcore Linux Fans, but this is INSANITY AND MADNESS!!!!!

---

### Post by lswest on 2008-05-06
> **MechWarrior001 said:**
> No Offense to Hardcore Linux Fans, but this is INSANITY AND MADNESS!!!!!

why? most of the repos are based online, and i'm pretty sure you can install the build-essential package from an alternate install disk, and i said i wasn't sure if the compiling of a kernel needs internet, but i do believe it does, because it downloads the source files off the 'net.  They can't stick everything one may or may not need on a CD, it's just not possible storage-wise.  there are ways of installing packages without internet, such as AptOnCD, but i find it hard to believe you can't stick an ethernet cable in that computer for all of 5 minutes.

Sorry if it seems harsh, but really, but in my experience people have always been able to get internet for the few minutes needed to install required packages, especially if they can post on these forums (unless it's an issue with dial-up or low bandwidth, then i'd suggest downloading AptOnCD at a friend's house).

P.S. thanks for the thanks.

---

### Post by MechWarrior001 on 2008-05-06
My parents took the router out of my room and are forcing me to wait to buy a WNIC.

So, therefore, Not only can't I use my Ethernet, I have to buy a $70-100 WNIC and go through the whole WEP/WPA Key Authentication Process, which is gonna take forever 'cause my parents forgot the admin password to my Wireless router.

And I'm using the school computers to access these forums. (And all the Nvidia & wine packages I download for my comp seem to be wrong Architechture!!!! :icon_frown::mad::confused:)

---

### Post by lswest on 2008-05-06
> **MechWarrior001 said:**
> My parents took the router out of my room and are forcing me to wait to buy a WNIC.

So, therefore, Not only can't I use my Ethernet, I have to buy a $70-100 WNIC and go through the whole WEP/WPA Key Authentication Process, which is gonna take forever 'cause my parents forgot the admin password to my Wireless router.

And I'm using the school computers to access these forums. (And all the Nvidia & wine packages I download for my comp seem to be wrong Architechture!!!! :icon_frown::mad::confused:)

Ah, that's unfortunate :S and to log into the router, there is a reset button somewhere on it, so you could easily set it back to default where the admin password should be "0000" (or else it will specify in the manual).  And hmm, what are the specs on your computer?

---

### Post by briandu on 2008-05-06
Hi there,

9600GT on q6600 - using Ubuntu AMD64 mode

I conducted the nvidia-glx-new download as deb file and using gdebi I re-installed it. the hardware manager did not register this again.

Reboot no change.

conducted the gdm stop, the sh NVIDIA pkg run for versions 171.06 and 173.08 and still no change.

On the initial fresh install I get 1680x1200 on fb mode (not NVIDIA) but now that i have installed the NVIDIA stuff I can only get  800x600 and on NV.

Any ideas?

thanks in advance

---

### Post by MechWarrior001 on 2008-05-06
AMD Sempron 3100+ ~1.81 gHz (754 Socket Architecture)

Nvidia nforce 3-A DRR400 1.5 GB RAM

Nvidia Geforce 7800 GS AGP 8x

Creative X-Fi Fatal1ty Sound Blaster Series Sound Card

Western Digital 160GB SATA HDD

Samsung 932B SyncMaster LCD Screen

---

### Post by briandu on 2008-05-06
Have you got any further?

---

### Post by briandu on 2008-05-06
Well i have uninstalled nvidia-glx-new, 171.06 and 173.08 and install envyng.

It did not recognise the card so I am doing a manual install.

Now I have a blank screen with nothing but "sparkly bits". this does not help

---

### Post by briandu on 2008-05-06
I tried envyng and it failed. So I had to reboot and use the menu recovery mode so I could get back to square one. At lease that works! 

I am not sure as to what is missing :confused:

BTW the h/ware driver still does not show

---

### Post by aktiwers on 2008-05-06
Have you tried that link I posted in post number 7 here?
A "manual" install could be the answer.

---

### Post by lswest on 2008-05-07
> **MechWarrior001 said:**
> AMD Sempron 3100+ ~1.81 gHz (754 Socket Architecture)

Nvidia nforce 3-A DRR400 1.5 GB RAM

Nvidia Geforce 7800 GS AGP 8x

Creative X-Fi Fatal1ty Sound Blaster Series Sound Card

Western Digital 160GB SATA HDD

Samsung 932B SyncMaster LCD Screen

i don't suppose you remember if you installed the amd64 or the i386 system?  if you don't type in ```
uname -a
``` in the terminal, second last word will be something like i386, i686, amd64, etc.  Post back (just take note, no need for the whole output).

---

### Post by RAOF on 2008-05-07
> **briandu said:**
> Hi there,

9600GT on q6600 - using Ubuntu AMD64 mode
...

You'll need to do something funky because your card isn't supported by any official nvidia driver.  [https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual) is the wiki page for how to install the beta drivers that your card needs.

@MechWarrior001:  You're right, it's not much fun setting up an Ubuntu system without an internet connection.  Getting your driver working *should* be as easy as downloading the **nvidia-glx-new** package for your architecture (either i386, or amd64 - see the previous post) and possibly the appropriate **linux-restricted-modules** package (this will probably be **linux-restricted-modules-2.6.24-16-generic** - the last part of the package name should be the output of the **uname -r** command) from packages.ubuntu.com, installing them, running 'sudo nvidia-xconfig' to set your X driver to be the binary driver, and restarting.

Pay attention to any warnings or errors raised during those steps; it will make it much, much easier to help you if you include the output of any failing operations.  The above procedure should work, but might not depending on what manual changes you've made trying to get the nvidia.com drivers installed.

---

### Post by briandu on 2008-05-07
ROAF,

I did follow the guide but to no avail.  Also I tried as per msg #7 - no result.

I think I am going to set up my old 8600GT card first - that worked fine on Ubuntu 7.10; then try the 9600GT card.

Maybe I get lucky?

---

### Post by MechWarrior001 on 2008-05-07
Now I gotta wait 'till I get home. :-|

---

### Post by briandu on 2008-05-07
Nope that did not work either.

I am now flummoxed as to the solution here. The odd thing is that I have another installation of Ubuntu i386 c/w Compiz/Beryl that I configured under 7.10 and it worked. I then upgraded that to 8.04 and it still works.

It is an AMD64 3500 dual with a 8600 GT card. (i386 and NOT 64)

I looked at the xorg.conf and added any diffs into my xorg.conf but no diffs - I still get the low grade xconf menu that does NOT detect the card of drivers.

Any ideas anyone?:confused:

---

### Post by briandu on 2008-05-07
SOLVED!!! :popcorn:

So this is what I did:
open terminal:
cd /lib/linux-restricted-modules

sudo rm .nvidia*

then:
downloaded the NVIDIA driver - I used 173.08 from the archives.
sudo chmod +x NVIDIA-Linux-x86_64-173.08-pkg2.run    note this is for 64 mode
(note place this in you home directory - easy access)

press Ctrl+Alt+F1
log in 



enter:
sudo /etc/init.d/gdm stop
sudo apt-get install nvidia-settings
sudo sh NVIDIA-Linux-x86_64-173.08-pkg2.run (say yes to all prompts)
sudo reboot

then:
Done!!!!:popcorn:

Goodluck.

now I can get on with Beryl/Compiz etc.

---

### Post by Zanshin on 2008-05-08
briandu, i have a nVidia 9600GT also.  been running the 171.06 driver but wonder if the 173.06 is better and looking to try it out.  would be interested in comparing notes on performance of this card.  

Question:  how does one uninstall a beta driver like 171.06 which was installed from a *.run file?  I'm assuming this is required before installing the 173.06 beta per the steps above.  

Thanks!!

Updated:  

if my driver was installed with this:
   sudo sh NVIDIA-Linux-x86-171.06-pkg1.run

would my uninstall simply be this?
   sudo sh NVIDIA-Linux-x86-171.06-pkg1.run --uninstall

[found this idea in the envyNG faqs]

---

### Post by aktiwers on 2008-05-08
> **Zanshin said:**
> briandu, i have a nVidia 9600GT also.  been running the 171.06 driver but wonder if the 173.06 is better and looking to try it out.  would be interested in comparing notes on performance of this card.  

Question:  how does one uninstall a beta driver like 171.06 which was installed from a *.run file?  I'm assuming this is required before installing the 173.06 beta per the steps above.  

Thanks!!

Updated:  

if my driver was installed with this:
   sudo sh NVIDIA-Linux-x86-171.06-pkg1.run

would my uninstall simply be this?
   sudo sh NVIDIA-Linux-x86-171.06-pkg1.run --uninstall

[found this idea in the envyNG faqs]

He posted that already, I did too in post number 7 :) Just replace the filename

---

### Post by Zanshin on 2008-05-08
Sorry, but that didn't answer my question.  I already understand how to do the manual install.  I was successful doing it for 171.06.  (see here [http://ubuntuforums.org/showpost.php?p=4904783&postcount=413]("http://ubuntuforums.org/showpost.php?p=4904783&postcount=413") )

I am looking at now installing the newer 173.08 beta driver, but don't want to cause any conflicts with the existing beta driver.  

To clarify my questions:
1)  Do I need to do a manual uninstall of the 171.06 driver FIRST ?
2a)  If so, how is that done?  (I have a hunch in my prior post - can anyone confirm?)
2b)  If not and I just use the same install commands, what happens to the previously installed driver?  Is it written over by the new installer?  

Thanks in advance!

---

### Post by aktiwers on 2008-05-08
1) I never uninstall the current driver I usually just install the newest one on top of the old one
2a) Sorry this I don't know.
2b) Either it gets overwritten or it gets left unused - actually I'm not quite sure about this, but I guess it will be overwritten. I think nvidia made the installer so it overwrites, but again im not 100% sure.

Just do a normal manual install of the new driver, and you should be fine(I mean no conflicts). Try it out, worst case come back and we will find out what to do :)

---

### Post by Neo0351 on 2008-05-08
> **aktiwers said:**
> 1) I never uninstall the current driver I usually just install the newest one on top of the old one
2a) Sorry this I don't know.
2b) Either it gets overwritten or it gets left unused - actually I'm not quite sure about this, but I guess it will be overwritten. I think nvidia made the installer so it overwrites, but again im not 100% sure.

Just do a normal manual install of the new driver, and you should be fine(I mean no conflicts). Try it out, worst case come back and we will find out what to do :)

the nvidia installer automatically uninstalls the old driver before the new one is installed.

> Zanshin  	
Re: Logging out of X server to install Nvidia drivers.
Sorry, but that didn't answer my question. I already understand how to do the manual install. I was successful doing it for 171.06. (see here [http://ubuntuforums.org/showpost.php...&postcount=413](http://ubuntuforums.org/showpost.php...&postcount=413) )

I am looking at now installing the newer 173.08 beta driver, but don't want to cause any conflicts with the existing beta driver.

To clarify my questions:
1) Do I need to do a manual uninstall of the 171.06 driver FIRST ?
2a) If so, how is that done? (I have a hunch in my prior post - can anyone confirm?)
2b) If not and I just use the same install commands, what happens to the previously installed driver? Is it written over by the new installer?

Thanks in advance!

you really dont need to install the 173.08 drivers.  i havent noticed any difference between them and the 171.06 drivers.  actually i think i get flickers from the 173.08 drivers.

---

### Post by Zanshin on 2008-05-09
Thanks for the followups!!  Nice to know that I can skip the uninstall part for next time though!  

Turns out that what i found was correct for the uninstall.  

This will uninstall the older driver:
sudo sh NVIDIA-Linux-x86-*[COLOR="Blue"]your.old.ver.here[/COLOR]*-pkg1.run --uninstall

Also did the newer 173.08 beta install and found my glxgears results dropped to the 7200-7400 fps range (where they were at 10000-11000 fps on version 171.06).  Your mileage may vary.  :guitar:

Seems previous posts on 173.08 being a bit flaky were correct.  So, I reinstalled 171.06.  Looking forward to the next driver release!

---

