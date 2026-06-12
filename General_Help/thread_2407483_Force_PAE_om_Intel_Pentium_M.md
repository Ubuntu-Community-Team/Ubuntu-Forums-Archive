---
title: "Force PAE om Intel Pentium M"
date: 2018-12-04
forum: General Help
---

### Post by hennmann on 2018-12-04
As per
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)
I have an IBM Thinkpad 32 bit with an Intel Pentium M series (Pentium 1500mhz with 1280 megs of RAM running Zorin 6.2 Lite very well) and get the error PAE is disabled!
Following the steps using F6 with no ForcePAE option I used esc and entered the forcepae--forcepae at the end of the string and still get the PAE disabled error nag. 
What steps am I missing here (if any) or am I SOL for trying to get something newer than 6.2 to run?
Zorin 7lite, 8 lite hangs at the boot menu of options after option is selected I.E. Try Zorin, Install Zorin
Lubuntu 18.04 gives PAE error as well as Zorin 12.4 lite
Other than Zorin 6.2 Lite xenialpup 7.5 works well but I would like to install a newer version of Zorin, Ubuntu, or Lubuntu

---

### Post by sudodus on 2018-12-05
1. There should be spaces around '--': 

```

forcepae -- forcepae

```

2. Where did you enter this forcepae token?

- At the grub menu when booting an installed system?

- At the syslinux menu when booting a live system?

- In a file, in this case which file?

. If in **/boot/grub/grub.cfg** it works directly, but may be *overwritten* automatically at an update (or manually if you run **sudo update-grub**). In this case you add it at the end of the line starting with **linux**.

. If in **/etc/default/grub** you must run **sudo update-grub** to get it active (by entering it into **/boot/grub/grub.cfg**). In this case you edit it into the line starting with GRUB_CMDLINE_LINUX or GRUB_CMDLINE_LINUX_DEFAULT, save the file and update-grub,

```

sudo nano /etc/default/grub
sudo update-grub

```

and it should work at reboot.

---

### Post by hennmann on 2018-12-05
As per the picture on the link I  included in my post exactly as their instructions IE if forcePAE isn't in the dropdown menue for F6 press Esc to exit and the string remains. Let me add that this is the menu that appears directly after the USB is selected for boot selection out of the BIOS boot menue. This is when one is first attempting to install or run live with no OS installed yet.
BUT I was unaware of the spaces and this is what I didn't do. I will give this a try because as per their instructions I entered.  
splashforcepae--forcepae
Notice I forgot or overlooked the space between splash and also no spaces before or after the delimiter. 
The red circle kind of threw me off of the space between splash and no mention like yours of a space before and after the delimiter.
This is for the newest or should I say all of the newest Kernels where the man with arms raised in a circle beside the keyboard on the bottom. Sometimes this is the image of myself trying to install when the PAE error is displayed.
I might add AT LEAST this is happening because the Kernel directly before these versions with the older image of boot loader does nothing but hang directly after the option of running live or install is selected.
The only versions of that flavor that worked were:
Zorin 6.2 Lite and the older flavors of Lubuntu and Linux Lite 
All would install but slightly newer (IE 7.0) would hang and the 16.04 and 18.04 using that Kernel would give me the PAE error.

Oh and I might add the Zorin OS6.2 Lite worked great and even updated as much as was available but only so much is available so this is why I'm attempting to install as new as possible of any Lite version with the limited hardware. Limited yes but not as limited as some.

Many thanks for info!
I'm not totally helpless as I just need proper commands for the CLI or terminal. This was apparent when I had GPU driver issues on much newer hardware and one helpful member gave me all the commands to do a full system update and replace the incorrect drivers.
This is why I fled from Linux years ago because sad to say I'm a GUI slave. If you don't know the required commands you are stuck in the mud.

---

### Post by hennmann on 2018-12-05
Here is an update
I figured lets try Ubuntu 16.04.5-desktop-i386 and the boot menu never appears for options just the circled man and keyboard followed by the PAE nag. No options for the forcepae that i can figure out how to access.

---

### Post by hennmann on 2018-12-05
Now here is the big question
What is going on here?
Presently out of total frustration of only very early versions being the only option such as Zorin 6.2 Lite, or Puppy Linux Xenial Pup 7.5 and 4.3.1 being the only thing working, Puppy is working very good but i wanted something a bit fancier like Ubuntu or Zorin due to being quite simply spoiled!
Zorin 6.2 Lite works VERY well but is outdated and even though it is outdated actually updated itself to the limited amounts of system updates.
Now I try slightly newer and no matter what I try including Linux Lite 2.0 and when greeted with the USB BOOT Installer menu, select either Live or Install system hangs and sits doing nothing!
If I use the 16.04 flavor or newer I don't get an options menu but am greeted with the man in circle beside the keyboard Icon just to be greeted with PAE disabled and installation aborted. Some Distros did give me the option by hitting Tab but as per 

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

I entered the command incorrect command  "--" without the spaces and it didn't work but was corrected on this but never gave it a try yet, live and learn.

While poking around the web I decided on Debian once again and downloaded the latest but 32 bit version.
Well what the heck it booted, started installation albeit more in depth with very basic graphics but it is installing and even the boot loader is working after partitioning the hard drive with Windows on other partitions.
The only problem now is I'm greeted with an all text Login like using terminal and after entering Username and password lets me in but I need a command to continue.
Anyway during install I wasn't able to properly configure my network ethernet and WIFI of which were detected and had proper drivers so a very limited basic install occurred which is why I'm working in a terminal with no command knowledge.
To make a long story short, why does Debian work or try to work and most of the others won't?

---

### Post by sudodus on 2018-12-06
Standard Ubuntu is too 'heavy' for your old IBM Thinkpad with a Pentium M CPU. I would recommend **Lubuntu**, which has an ultra-light desktop environment (and still the Ubuntu engine under the hood).

I have an IBM Thinkpad T42, with a Pentium M at 1700 MHz and 1280 megs of RAM, similar to yours, and I can run live as well as install from **lubuntu-16.04.1-desktop-i386.iso** and **lubuntu-18.04.1-desktop-i386.iso**.

- See this link, [How to select the version and flavour of Ubuntu](https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865)

- and the more general advice in the following link, [Old hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by hennmann on 2018-12-06
sudodus
Well I did a reinstall of Debian 9 but this time in full graphic mode, more options, was now able to configure WIFI and ether network. The first attempt was minimal graphics and full network install with myself not able to "talk" to it through commands and   it spent enough time downloading software, updates etc. is still installing  so I will give it a go and see what happens. Maybe Sloth, I don't know but didn't complain about PAE. I think the Lubuntu was the only flavor with the newer Kernel with the Circled Man that even gave me the forcepae option AND with with your instructions I should be able to get the forcepae to work. For now I will let Debian 9 install. What the heck if it is installing great without any nags or problems at least I will try it, got nothing to lose except time and everything to gain such as knowledge which I need in the Linux area.
The BooT loader at the first attempt looks like modern Ubuntu flavor but blue and if it is the newest Kernel it puzzles me why the PAE didn't pop up??? Probably another hour to go so I will post results. As far as I know what is installing is Debian 9.6.0-i386 and if this IBM can function with this my Acer Aspire One 533 with an Atom 455 1.66ghz and 2 gb of RAM should be able to handle regular Ub 18.0.4 and this is a 64 bit processor giving me more software options.

Oh! it's cleaning up..................

---

### Post by hennmann on 2018-12-06
First time startup with a great deal of hard drive activity of course but that is expected. Under details it shows Gnome Version 3.22.2 and if you can give me the command to use in the terminal to gain more information.
Otherwise it is running great albeit a little slothy but better than my Acer struggling with Win10. Comparable to my Acer with 1 gb of RAM and Win 7 Starter edition before I bumped up to 2 and a SSD. If your IBM is like mine you should have the hard drive slid in the side for quick swap and if you have a spare drive in the junk box giver a try. If I get brave I will try the Lubuntu as per your suggestions If I can get the PAE sorted out. It's not snappy like the Puppy or Zorin 6.2 Lite but it is very usable with all the latest (I think?) software. It also has everything but the kitchen sink installed for APPS and software as well. If the Lubuntu is the one that gave me the forcepae option instead of ramming it to boot then I can test it live.

---

### Post by sudodus on 2018-12-06
Yes, it is a good idea to **try linux distros live** before installing and Lubuntu is one of the good alternatives.

Debian 9 is still providing a non-pae kernel (in the Debian i386 iso files, while the Debian i686 iso files need pae (and with Pentium M can work around it with the forcepae boot option)).

---

### Post by MoebusNet on 2018-12-06
>  I would recommend Lubuntu, which has an ultra-light desktop environment (and still the Ubuntu engine under the hood).  +1

I've investigated many distros trying to keep my antique Dell Latitude D800 1.4 Ghz Pentium-M going. Since it is a 32-bit-only machine, it can feel somewhat abandoned by newer OS's. Thankfully, Lubuntu  18.04.1 stepped up, installed well and runs well for me. I have a little bit more RAM than you (2Gb), but otherwise similar. A couple of notes, BTW - PAE is only useful on 32-bit OS's if your system is going to exceed about 3Gb RAM; that is not an issue for you. Unfortunately for us, PAE is a kernel requirement for all modern kernels, even though it is so rarely utilized by 32-bit desktop systems. My Banias Pentium-M is PAE-capable, it just doesn't advertise the fact (a hardware bug) which is why *forcepae* works. Another thing is that a limiting factor is your video card; Ubuntu, Kubuntu and others require a much more capable video card than was/is available for our systems (mine is _64Mb_ VRAM rather than 1.5Gb VRAM like my more modern notebook). Lubuntu's open-source video driver works well with my video card.

Written on my Lubuntu 18.04.1 Pentium-M.

---

### Post by hennmann on 2018-12-06
MoebusNet I agree and feel the same way you do with the way things are going and have become! I will not give up on Debian since it gave me some of the least grief other than Puppy and as I'm typing this thanks to sudodus I now have Lubuntu 18.04 installing on my Thinkpad BUT the difference is I re partitioned the tiny little 40GB and gave / more and reduced home and increased my swap from 1.28gb to 3 gb. Perhaps a necessary move on the swap but perhaps Debian would have performed slightly better with more swap?? All I can say at this point is my Acer was a tired snail on Win 7 Starter with 1 GB and became an Olympic Snail with 2 GB and even better with a SSD. The main point of this experiment other than learning is to see what performs the best with the best layout to resurrect this IBM and if this is successful will be a good move for the Acer. My Acer is at least 64 bit giving more options when 32 is being abandoned. As for the Swap for my size I selected? Well my HP Omnibook Xe3 with the PIII800 with 128 megs of RAM was TOTALLY USELESS on Live Puppy 4.3.1 making me despise running in Live and making me think Live is a waste of time using a USB on older systems with limited resources.  Just installing with a swap of 2gb with such pathetic amounts of RAM made it a very snappy laptop and outperforming Win 2000!! Using the same config Mandrake 7 from 2001 was very much at home and performed as good as Puppy and this wasn't considered to be a Lite OS back in the day but a normal typical alternative to Windows. 
Now that Lubuntu 18.0.4 has completed, the verdict is navigating around is a bit livelier but Firefox still requires about 10 seconds to open as well. It is now installing updates which also can help performance perhaps? 
Also it is very stripped down for APPS and other programs compared to Debian 9 4.6.0 I do believe is the version. Debian was stuffed very full with everything but the kitchen sink and I will give Lubuntu a try but I'm curious if the larger swap will do anything and will probably try it again to see if I can notice any difference other than my imagination. One thing about Debian is it brings me back to the way things used to be for more steps being required during installation including partitioning, network, etc. and perhaps this is better to make people learn more instead of relying on automated installation where NOOBS don't understand the required partitions and file systems. Also with Debian I was required to set up a / password as well also like the older versions so two passwords are required if desired, one to log in as the user, and another to prevent accidental discombobulation of your system. Lubuntu only asked for one password which was to log on as a user instead of /Root.
If this IBM had more horsepower I think Debian would be my first choice not being stripped down and forcing me to forcepae as well for the latest OS they have to offer. What they did making these extra steps not required was a great move in their part to create less frustration preventing me from trying other versions because like I mentioned earlier there was NO menu to select any options or forcepae! As soon as my BIOS boot selected the USB it was straight to the circled man and next to the PAE disabled indication and aborted installation. Lubuntu at least gave me this option and oh yes what about some of the others with the earlier kernel prior to the "circled man of death" logo where they would freeze or lock up after making the selection?  Zorin 7,8.1, 11 and even Linux Lite didn't get past this either no matter the version!

---

### Post by hennmann on 2018-12-06
It appears to be settling in as the updates install etc. and Firefox is much faster now. Things look so promising that perhaps I will leave it (Lubuntu) on and shop for a larger small hard drive for this old timer. It has a 40 GB drive in it and even double that would be great.

---

### Post by MoebusNet on 2018-12-07
My D800 is old enough that it uses a PATA interface rather than the newer and faster SATA interface. Between PATA and my BIOS constraints, 120 Gb was the biggest HDD I could fit. My D800 has a hot-swappable CD/DVD drive that I can swap out for a hot-swappable sled with a PATA to SATA 500Gb HDD for additional storage, although I primarily use it for additional backup. Stuff like videos I keep on my backup USB3 4Tb external HDD.

---

### Post by hennmann on 2018-12-07
Moebus you might be surprised what fits as I have hardware much older such as my 1999 PIII 450 Slotket version that started life as a PII and a BIOS flash updated it to PIII! I purchased it with a 6.4 GB HHD and it wouldn't recognize a much larger and a BIOS flash solved this but there are software patches that were around to fool the BIOS.  The RAM was brutal in cost nothing compared to what it is selling for so RAM was always bare minimum and a few months later a 25 GB hard drive came on the market for $2500.00 for the rich and famous. I purchased new in late 1999 for a King's ransom with ISA and PCI slots only and I can't remember if it had a very crude AGP slot or if I had to use PCI video card? Believe it or not I still have it and I used to run XP on it VERY WELL. I replaced it with my socket 939 in 2004 and this was a true 64 bit that I ran until I purchased my Krait 970A SLI not even a year ago.
Now my IBM I don't know if the 3gb swap is a waste of time and space so I'm probably going to retry the Debian 9.6.0 i386 to see if there is any difference between the 1.2 and 3 gb swap, probably not?

Delayed posting due to installation and now I can answer my question, the larger swap most certainly helped and the Debian seems to be operating a bit faster during operating various software. It is very usable so but of course isn't as fast as Lubuntu but otherwise if this was my only option I wouldn't complain. Right now it runs like my Acer Aspire running Win7 Starter Edition 32 bit. The comparison, faster than the Acer ran BEFORE I upgraded the ram to 2 GB and slower than it is now with the 2gb and a SSD but keep in mind we have an Atom 455 1.66 with Hyperthreading that shows up as dual core processor and more ram with most likely a faster bus speed and ram. 
With the Lubuntu it is out performing the Acer running Win 7 Starter.
Running Live to test has been suggested but in my honest opinion from what i have seen, live is a very poor test running entirely in ram! My HP Omnibook Xe3 PIII800 and 128 megs of ram was virtually useless in live but performs better than Win 2000 it was intended for when Pup 4.3.1 was permanently installed and with a swap partition.
The better test will be on my Acer for Zorin 12.4 Lite, Debian 9, and Lubuntu and of course i have the option of 32/64 as well. What the heck, perhaps I will try regular Ubuntu 18.0.4.1 and perhaps regular Ub will be like Debian on my IBM? I will give it a try because nothing got wiped out with the Thinkpad running dual OS XP/Lubuntu or Debian. The only difference is my Acer has Win 10 and Win 7 with an empty reserved partition for such an attempt. Win 10 will not be a loss if things go wrong because my Acer runs it slower than the IBM with Debian before I increased the size of swap.

---

### Post by MoebusNet on 2018-12-08
@Hennmann - For me, the Live DVD/USB has been most useful not as a daily driver or comparison, but to verify hardware compatibility. When I first started working with Ubuntu, Ubuntu 5.10 Breezy Badger was in vogue and I had issues with my WiFi card driver and my video card driver, if I recall. It wasn't until Ubuntu 8.04 that I felt comfortable enough with Linux and Ubuntu to quit Windows as a backup. In the interim, I always used (in the old days) the Live-CD to verify hardware compatibility before upgrading versions because it seemed to be a much bigger issue then. >  live is a very poor test running entirely in ram!  From my understanding, what really slows down the Live DVD/USB is the access time required to get data from the optical drive or the flash drive. Unlike Puppy OS, which can load entirely to RAM, the Ubuntu OS family is not designed to run entirely from RAM because a fair number of people wouldn't have enough system RAM (as in your case). That is why an installed version of Ubuntu will always be faster, even if it has to access the HDD/SSD swap partition to supplement the system RAM.

---

### Post by sudodus on 2018-12-08
@MoebusNet,

You *can* run Ubuntu, Lubuntu etc, live in RAM, if you have enough RAM in the computer: Boot with the boot option **toram**.

---

### Post by MoebusNet on 2018-12-08
@sudous,

Thank you! That is something I did not know and have never tried. I imagine my new notebook with 32Gb RAM should be able to do that. I don't believe my old notebook with 2GB RAM would have much surplus for toram. I'll need to read up on this right away. Thank you again!

---

### Post by sudodus on 2018-12-08
@MoebusNet,

I think it is useful mainly for live and persistent live systems (in computers with a lot a RAM). [mkusb](https://help.ubuntu.com/community/mkusb) creates a grub menuentry with toram automatically, when you create a persistent live system. (The system image is copied to RAM, but the system is still depending on the casper-rw file. A live-only system with toram will be completely detached from the drive it was booted from, all partitions can be unmounted and the drive can be unplugged, while the system is running.

It is possible also for installed systems, but I am afraid, that it is not straightforward. There is a thread by **terminator14** about it that was developed for some previous version of Ubuntu, but I don't think it has been updated for the new versions of Ubuntu.

[ Making Ubuntu Fast using RAM (updated and simplified)](https://ubuntuforums.org/showthread.php?t=1594694)

Good luck testing **toram** and please share your result (with 32 GB RAM) :-)

---

### Post by hennmann on 2018-12-08
MoebusNet you are in the same boat as myself with the exception of your new notebook with 32 GB of RAM. All of my Notebooks and Netbooks as the case may be for the Acer a netbook all have 2 gb or less down to 128 megs for the HP. The only exception to this is my Desktop PC's  MSI Krait Edition with 32 and an FX8370x8, or my Gigabyt M68MTS2 AM3 and an Athlon 640x4  with 16 GB. Both the Krait and Gig are running Kingston HyperX Fury 1600 RAM.................BUT
the older systems I have also have slower BUS speeds, slower RAM, less RAM including an MSI K9N6PGM2 AM2 that is maxed out with slower 8GB RAM but due to the totally STUPID prices sellers want for obsolete unwanted RAM I'm sitting at 4 on this 64 bit system!!
At the end of the day running Live or in RAM on the older systems with limited slower resources gives the tested hardware, software, and both at the same time a bad reputation and indication of usefulness or should I say uselessness. Take the HP with the mighty PIII 800 and 128 megs of RAM, totally useless on so called live and very slow installing Puppy 4.3.1 to the point of tossing it in a recycle bin or tipping it in the trash, but throw a swap of 1-3gb, and a permanent installation it behaves like or better than my IBM with a Pentium M 1500 and 1280 of RAM running Debian 9.4.6.0 and yes it (the IBM) is now more responsive opening and running Firefox after I bumped up the swap to 3gb. Perhaps excessive on the swap but perhaps more is better than too little or perhaps every little thing helps? These were all usefulness tests and I will end up reinstalling Lubuntu 18.0.4.1 on the IBM but as for the Acer other members of this forum are running regular Ubuntu 18.0.4.1 on Netbooks with smaller Atom processors than mine albeit running slower than many would like but running and serving a purpose. My tests will continue on the Acer just to see what I can get away with including the fact I have more options having a bit more power and 64 bit capabilities.
IMHO for testing (on older including single and small dual core processors depending on how power hungry you are?) I suggest install on a hard drive, do research on partitioning, install a reasonable swap, and chuck that fully automated install in the bush especially for the older anemic systems! NOOB or not, learning too much is better than not enough.
I read an article on line about Debian vs Ubuntu about the pros and cons of both, Debian is considered very stable and well put together but the cons are it isn't recommended for NOOBs as installation is much more extensive including one thing I had to set up which is a / account as well as user account. This was always a step needing to be done with the older distros for everything, Mandrake, Redhat, etc.  If one doesn't know or isn't totally sure what they are doing setting up a / account is probably a good way of not ruining things [-Xby only running in the regular user account and if critical settings are required research should be done and then log into /. 
Now because this step is eliminated (unless I just missed it) in Ubuntu can somebody tell me a quick easy step to set up / account?:redface:

---

### Post by MoebusNet on 2018-12-09
Everything I've read about the design goals of Ubuntu lead me to believe that the Ubuntu OS family was designed intentionally to avoid a "/ account". Instead, the concept used is that the first user is set up with administrator privileges via the *sudo* command. By issuing this CLI command in Terminal and entering the correct password (from the installation setup) you achieve root privileges to accomplish tasks that would otherwise be unauthorized to an ordinary user. Ordinary tasks like web browsing, document generation, spreadsheet manipulation are performed as an ordinary user. The concept is to allow an ordinary user to accomplish their required tasks without being able to seriously screw up their system. Ubuntu is a multi-user-capable system, so that both ordinary users and users with administrator privileges can be added to the system after the Operating System is set up for the first user. If you have finished setting up Lubuntu, for example, and you want to download and install software you must enter the admin password to accomplish this. Depending on how you set things up, this may or may not be the same password as for the first user at installation. I hope I haven't made things too confusing for you! This may explain it better: [https://www.howtoforge.com/tutorial/sudo-beginners-guide/](https://www.howtoforge.com/tutorial/sudo-beginners-guide/)

---

### Post by hennmann on 2018-12-14
Thanks Moebusnet
While I was trying various flavors including Lubuntu seems to me I attempted to install software where / account was required. Okay root in terminal like I remember years ago being a GUI slave blindly stabbing around in the dark with a dull broken knife. Well the terminal didn't like that one and after a moment of wondering the lights went on and typed sudo and all went well. Now I'm an "advanced GUI Slave" blindly stabbing around with at least a knife.

---

### Post by MoebusNet on 2018-12-17
Glad to help! When you get a chance, please mark this thread 'SOLVED' using the Thread Tools at the upper-right of the web page.

---

