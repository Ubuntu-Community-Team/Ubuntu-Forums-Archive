---
title: "How Nthe Heck Do You Get Nvidia Accelerated Graphics Drivers To Work?"
date: 2007-07-04
forum: General Help
---

### Post by stoodleysnow on 2007-07-04
I have a 64 bit Ubuntu Feisty 7.04 installation on a computer of the following spec:

Intel Core 2 Duo, 2.13 GHz, LGA775
Asus P5B motherboard
:arrow:[COLOR="Red"]Nvidia Gforce 7600 GS PCI-E x16 Graphics card[/COLOR]
500GB SATA Hard Disk
1GB DDR2 RAM
DVD ROM
DVD RW with Lightscribe
Smart card reader
Floppy disk drive
Dial up modem (just in case)

I installed automatic updates a few days ago. The next time I started up my computer, the X server failed to load. I trawled the forums, and found out a few ways of getting temporarily around the problem.
So I tried:
> sudo apt-get install nvidia-glx-legacy nvidia-settings
sudo nvidia-glx-config enable
sudo nano /etc/X11/xorg.conf
(where I changed 'nvidia' to 'nv' under the device bit)
On rebooting, my desktop was back... but running the legacy driver, so no compiz-fusion, which I have really enjoyed of late.
So I tried to install the Nvidia restricted driver again, and it went back to command line only again.
I have since tried umpteen methods of uninstalling and reinstalling the nvidia drivers, including envy (didn't help, still the same result), > sudo dpkg-reconfigure xserver-xorg (very confusing, I probably messed something up in there) and Nvidia's latest binary, with the result that it is now in the Error state again, with yet another error:](*,)
>  Error: API mismatch: the NVIDIA kernel module has version 1.0-9639, but this X module has the version 1.0-9631..........................(obvious stuff about 'try reinstalling this or that' which I've already trried)......................
failed to initialize the Nvidia kernel module:


I sort of understand what the problem is, but if I try solving it , I'll probably end up digging the hole in the mud that is my computer even deeper. And I would rather not have to reinstall everything.

This is now the third day I have spent trying to solve this. HELP!
[-o<

---

### Post by stoodleysnow on 2007-07-04
Hello?
Anyone have an answer?
Please? :?:

---

### Post by Jordan777 on 2007-07-04
I was having very similar problems to you and nothing worked.  I don't know about your situation but all I have on my desktop right now is documents imported from my windows partition.  I just completely deleted my /home and / partitions for Ubuntu and reinstalled completely one time.  Then after all the updates I installed envy which set up my graphics drivers for me and allows me to select the correct resolutions.  After all this Ubuntu has been working great.  I have restarted about twice now no problems so I shouldn't have any more.  I don't have a link for envy so just search and use the word envy.  There are links all over for it.;)  Good luck!  Don't let it stress you out too much.  I had to reinstall my / about 10 times before I just COMPLETELY uninstalled Ubuntu and now it works great.

---

### Post by Jordan777 on 2007-07-04
I saw that abut envy but maybe if you completely uninstall your Ubuntu partitions (excluding swap) it may work.  Only try if you have just a handful of documents you can very easily copy and replace.  I don't want to be the cause of you losing something huge. ;)

---

### Post by stoodleysnow on 2007-07-04
So you're basically saying it's  time for a full reinstallation?
RIGHT.
(meshes fingers together and turns hands outwards so the joints click)
Let's get backing up, then.:)
Thanks.
I'll let you know if I have any more problems.

---

### Post by Rock_Lee_NuX on 2007-07-05
> So you're basically saying it's time for a full reinstallation?
RIGHT.
(meshes fingers together and turns hands outwards so the joints click)
Let's get backing up, then.
Thanks.
I'll let you know if I have any more problems.

Hey **stoodleysnow**, I have exactly the same problem! 

But I don't think that reinstallingthe whole OS is the only option. There has to be a solution to completely erase the nVidia driver traces.

We must dig a bit more... :)

---

### Post by jocko on 2007-07-05
> **stoodleysnow said:**
> 
:arrow:[COLOR=Red]Nvidia Gforce 7600 GS PCI-E x16 Graphics card[/COLOR]


With that card you do **not** want to use the legacy drivers (they only support old cards and will probably not work at all with your card).
You'll probably have better luck if you install "nvidia-glx" or "nvidia-glx-new" instead.
Have you tried the restricted driver manager?
It should set up the correct driver and enable it in xorg.conf.

Try like this:
1. Uninstall the nvidia-glx-legacy package. (sudo apt-get uninstall nvidia-glx-legacy)
2. Edit xorg.conf to use either "vesa" or "nv".
3. Reboot
4. Start the restricted driver manager and enable the drivers for your graphics card. (sudo restricted-manager)
5. Reboot again.

---

### Post by AriciU on 2007-07-05
Don't reinstall everything just for those drivers... I had the exact same problem earlier trying to update to the latest Nvidia drivers (100.14.11 or something like that) only to have compiz-fusion not startup. I then tried to revert back to the original drivers i had but couldn't start X anymore.

I did:

apt-get remove nvidia-*

This will remove everything concerning nvidia on your system.

Then i edited xorg.conf and set "vesa" as the driver instead of "nvidia".

Started X again and ran Envy. Uninstalled Nvidia driver to make sure everything is out then reinstalled the Nvidia driver thru Envy (100.14.09). Everything was fine after that and compiz fusion was working again.

---

### Post by Jordan777 on 2007-07-05
Wow I totally forgot about this thread my bad :D.  hey I'm glad it worked out for you.  I am not a guru in any subject about Linux haha I just listed what worked for me when nothing else did.;)

---

### Post by stoodleysnow on 2007-07-06
Too late, I already reinstalled. I think it's better than it was before, though, because now I know exactly what packages I need I've been able to install just them, and have a nice streamlined system now. :-)
But, alas, my backup disc (though apparently burned OK) is scratched and unmountable.:-({|= So it's a good job there was nowt important on it!:D
):P

---

