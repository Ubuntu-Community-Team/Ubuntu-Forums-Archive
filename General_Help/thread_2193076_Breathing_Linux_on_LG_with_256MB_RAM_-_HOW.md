---
title: "Breathing Linux on LG with 256MB RAM - HOW?"
date: 2013-12-11
forum: General Help
---

### Post by amjjawad on 2013-12-11
Hi everyone,

As part of my Real Life Activities to Convert my Neighbours to Linux, I have met a new neighbour yesterday who have me "Four" different 'old' Laptops which I converted already to Linux (ATOM Laptop with Lubuntu 13.10, Mini HP with VIA C7 M CPU and 512MB RAM = Xubuntu 12.04.3 and another laptop with 1GB RAM = Xubuntu 12.04.3) and the fourth laptop is LG with 256MB RAM - please see the attached picture.

[ATTACH=CONFIG]248505[/ATTACH]

I have tried Lubuntu 13.10, Lubuntu 12.04 (I know, it is outdated), Xubuntu 12.04.3 (managed to enter the Live Desktop but couldn't do much because the machine is quite old as you see and slow) and finally tried Ubuntu 10.04.3 which is outdated (I know) but was just trying to see what could happen.

So, obviously, this is a special case.

I do know too that with 256MB RAM, one can't do much but that Laptop is for my neighbour's son so definitely, he doesn't need much. Most likely he will use it for his school stuff :)

So, in your opinion, how can we get this very old machine up and running? 

Thoughts are appreciated, thanks in advance!

Edit:
I forgot to add that I couldn't manage to find out what graphics card it has but it didn't let me boot the Lubuntu 12.04 LiveCD and gave me "boot:" on the screen. I was unable to find out the graphics card.

---

### Post by Topsiho on 2013-12-11
You are, it seems, only thinking Ubuntu or it's derivatives.
Why don't you investigate Distrowatch and find a small distribution that fits the old hardware?

First thing that I found at Distrowatch was Damn Small Linux.

Please google, find distrowatch, and try a version of Linux that fits the old laptop :), and have fun.

Topsiho

---

### Post by Bucky Ball on 2013-12-11
Firstly, 12.04 LTS is not outdated. It is supported until April 2017, stable and reliable, as an LTS release is intended to be, and probably your best bet if you're installing for other people (as you are now going to need to upgrade all the the 13.10 machines to the next LTS release, 14.04 LTS in seven months, which can and probably will present a whole new set of problems, or you will leave people with unsupported, i.e. vulnerable, machines).

Try Porteus or Puppy for the 256mb machine. DSL is okay, too, but I have found it to be a little problematic (for me, that is).

---

### Post by amjjawad on 2013-12-11
> **Topsiho said:**
> You are, it seems, only thinking Ubuntu or it's derivatives.
Why don't you investigate Distrowatch and find a small distribution that fits the old hardware?

First thing that I found at Distrowatch was Damn Small Linux.

Please google, find distrowatch, and try a version of Linux that fits the old laptop :), and have fun.

Topsiho

The answer is simple. Because I have done that 3 years ago - [http://ubuntuforums.org/showthread.php?t=1590614](http://ubuntuforums.org/showthread.php?t=1590614) - and the one and only system that worked on that machine on that thread after 30 days of trying and trying was Lubuntu 11.10 :) and yes, that machine is still working :)

I do trust our community and I do trust the power of Ubuntu Based System :)

---

### Post by amjjawad on 2013-12-11
Hi,

> **Bucky Ball said:**
> Firstly, 12.04 LTS is not outdated.
I was very much precious :D
I was talking about "Lubuntu" 12.04, not other variant. Lubuntu 12.04 is NOT an LTS release - [https://wiki.ubuntu.com/Lubuntu#Lubuntu_vs_Ubuntu](https://wiki.ubuntu.com/Lubuntu#Lubuntu_vs_Ubuntu)

And whether it is supported or not, I didn't work on that machine (couldn't booted it with Lubuntu 12.04 LiveCD).

> It is supported until April 2017, stable and reliable, as an LTS release is intended to be, and probably your best bet if you're installing for other people (as you are now going to need to upgrade all the the 13.10 machines to the next LTS release, 14.04 LTS in seven months, which can and probably will present a whole new set of problems, or you will leave people with unsupported, i.e. vulnerable, machines).

I do have a list of the people names, contact numbers, addresses, etc and I know which user has 13.10 and which has 12.04.3 so no worries ;)

>  Try Proteus or Puppy for the 256mb machine. DSL is okay, too, but I have found it to be a little problematic (for me, that is).
I am actually looking at Ubuntu's Empire at the moment. I trust I still can do it with Ubuntu based. 

Problem is, I couldn't even boot the Ubuntu 10.04 LiveCD!

---

### Post by Bucky Ball on 2013-12-11
> **amjjawad said:**
> ... I have done that 3 years ago ...

A long time in technology. Things change fast. 

Try 'Porteus' I mean, not 'Proteus'.

[http://build.porteus.org/](http://build.porteus.org/)

---

### Post by amjjawad on 2013-12-11
I am not 100% sure but I guess there is a problem with the graphics card! After the LG Logo, I can see the LiveCD/LiveUSB Menu but whatever I choose, either I see "boot:" or black screen!

---

### Post by Bucky Ball on 2013-12-11
Would help if you mentioned what you are trying to install ...

Either way, at the LiveCD menu hit F6>nomodset. Continue as normal.

---

### Post by amjjawad on 2013-12-11
> **Bucky Ball said:**
> Would help if you mentioned what you are trying to install ...
Trying with different LiveCDs/LiveUSB of different Ubuntu Variants and different versions. I am trying now the LiveCD of Ubuntu 10.04 just to see what exactly can I make out of that ... 

> Either way, at the LiveCD menu hit F6>nomodset. Continue as normal.
Well, this is what I am trying to do but it doesn't let me do anything :/

---

### Post by amjjawad on 2013-12-11
For some VERY odd and weird reason, the laptop is rebooting itself right after I select anything from the Live Menu :/

It just let me one time to go through the installation process of one of the versions I am trying but right after the username and password, it rebooted itself :/

And, for yet another weird and odd reason, I need to keep pressing Fn+F7 to see something on the Screen as the Screen keeps turning to black, like I am connecting it to an external monitor but it is NOT attached to anything.

It is LG, LS50a with Intel Pentium M 1.4GHz-1.8GHz, 15" XGA TFT LCD, 256MB RAM and I think 40GB HDD.

---

### Post by amjjawad on 2013-12-11
[ATTACH=CONFIG]248507[/ATTACH]

[ATTACH=CONFIG]248508[/ATTACH]


Anyone has the same device?

---

### Post by amjjawad on 2013-12-11
Now, it shuts itself down O_o

It works fine on Windows XP. That machine still has XP and it is working without any problem!!!!!

I am out of idea at the moment. Not sure what else do I have to try? it is either rebooting itself or turning itself off. No matter what I do, same result. I hate to give up but I am out of idea at the moment. Thoughts?

---

### Post by Bucky Ball on 2013-12-11
Nothing to do with Windows. You are trying 32bit, not 64bit? How much RAM has this machine got? Is there actually free space to install to?

---

### Post by amjjawad on 2013-12-11
> **Bucky Ball said:**
> Nothing to do with Windows.
What I am trying to say that while I am on Windows XP, the laptop is not rebooting itself nor shut itself down.


> You are trying 32bit, not 64bit? 
I am not new :P
Definitely, i386 ;)

> How much RAM has this machine got? 
Check the thread's name ;)

> Is there actually free space to install to?
Yes of course but that has nothing to do with the issue as far as I can tell. It is not letting me to do anything anyway. The installation process has not yet reached to the point where it needs to play with the HDD.

I just don't know why the laptop is turning itself off or rebooting itself? I just can't find a logical answer.

---

### Post by fantab on 2013-12-11
With only 256Mb RAM, [Lubuntu alternative or Lubuntu minimal]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu#Minimal_Install") is your best option.

Since you are resurrecting old systems, you might want to keep [Knoppix Live]("http://knoppix.net/") at your disposal. Its a great distro for hardware diagnostics and fixes. The default comes with LXDE.
You might find these '[Cheat Codes]("http://knoppix.net/wiki/Cheat_Codes")' interesting.

Edit:
> I just don't know why the laptop is turning itself off or rebooting itself? I just can't find a logical answer. 				

Does the laptop has the heating issue. When a computer 'turns off' and then 'restarts', the first thing to look for will be cpu heating, second, run SMART tests on HDD to confirm its not dying.

---

### Post by amjjawad on 2013-12-11
> **fantab said:**
> With only 256Mb RAM, [Lubuntu alternative or Lubuntu minimal]("https://help.ubuntu.com/community/Lubuntu/GetLubuntu#Minimal_Install") is your best option.
Or Crunchbang. I am aware of that, thanks but the problem is the laptop is NOT letting me to do anything :/

> Since you are resurrecting old systems, you might want to keep [Knoppix Live]("http://knoppix.net/") at your disposal. Its a great distro for hardware diagnostics and fixes. The default comes with LXDE.
You might find these '[Cheat Codes]("http://knoppix.net/wiki/Cheat_Codes")' interesting.
Burning the LiveCD now, hope I can reach a bit further this time!

> Does the laptop has the heating issue. When a computer 'turns off' and then 'restarts', the first thing to look for will be cpu heating, second, run SMART tests on HDD to confirm its not dying.
No, the temp is very normal and no overheating at all. As I confirmed, the laptop 'works' like a charm when I run Windows XP which is installed. It is on my left now sitting beside me, it has been on Windows XP for more than 30mins, nothing is wrong. With Linux, it is either rebooting or turning off.

Just did a scan disc and defregement, etc and everything is working without any issue on Windows XP. I just wanted to check and try to re-produce the same behaviour but Windows XP works. Sad but true :) because I wish the other way around.

---

### Post by amjjawad on 2013-12-12
Sigh, this laptop is giving me hard time but yet again, I shall not give up.

Good news is, with LiveCD of Knoppix, I managed to wipe Windows XP and created new Linux Partitions to prepare the machine for the installation (I do create my partitions first before anything else and then install - this is what I do for the last 3 years).

Bad news is: the laptop, yet again, rebooted or turned itself off :(

I couldn't boot again from the LiveCD of Knoppix!

By the way, even with 256MB RAM, Knoppix worked really nicely, I was surprised!

What else we need to try here?

---

### Post by fantab on 2013-12-12
Could there be a problem with the CD drive itself? Any chance of using a USB drive? Check in the BIOS for related settings.
Have you tried the hardware related codes with Knoppix, (when it was booting)?

Since you've removed XP, try changing the SATA mode to 'AHCI'... 
Will it be possible to try with another stick of RAM?
Try adding some 'Thermal Paste' to the CPU...

That 'turning off' and 'rebooting' most definitely indicates a hardware problem... also if possible get a BIOS update/upgrade.
Why XP worked beats me but check the hardware..

---

### Post by amjjawad on 2013-12-12
> **fantab said:**
> Could there be a problem with the CD drive itself?
I don't think so because the LiveCD worked nicely at the very try and couldn't boot again due to the reboot issue.

> Any chance of using a USB drive?
Have done that already before even using a LiveCD, and same behaviour.

>  Have you tried the hardware related codes with Knoppix, (when it was booting)?
No, because the LiveCD just worked without anything from my side and then couldn't boot again due to the reboot issue.

>  Since you've removed XP, try changing the SATA mode to 'AHCI'... 
I don't think it has SATA anyway but will check this.

>  Will it be possible to try with another stick of RAM?
Have done that already, same result.

>  Try adding some 'Thermal Paste' to the CPU...
I don't have that and not sure how to do it.

>  That 'turning off' and 'rebooting' most definitely indicates a hardware problem... 
Okay but which part? it is not overheating! 

> also if possible get a BIOS update/upgrade.
Never done that in Linux and since there is NO system installed, I have no clue how to do that nor if that even possible! 

>  Why XP worked beats me but check the hardware..
Same here, I have no idea. I just hope I didn't do a bad mistake by removing XP as that was the only think that worked on that machine!

---

### Post by fantab on 2013-12-12
"Thermal Paste" is applied on the CPU. It is there on every CPU, but it eventually dries up causing CPU heating. And the moment CPU begins to heat up system shuts down or reboots.... you may not feel the heat on outside.
[https://www.youtube.com/watch?v=D8oYJnkWzXk](https://www.youtube.com/watch?v=D8oYJnkWzXk)

There are OS independent methods to update BIOS firmware... check on the Mobo manufacturer's website.

I have a bad CD drive. It works in a way, but cause issues... more often the CD/DVD (bootable) does not work, rarely it does boot. When it doesn't I get 'boot errors', while the same DVD/CD works fine on other machines. However, all the media CD/DVD's work great. 
Try a CD/DVD lens cleaner... and see if it helps. 

Also try replacing the CMOS battery... even that can cause shutdowns...

---

### Post by amjjawad on 2013-12-12
_**Update 1:**_
I managed to boot from the LiveCD of Knoppix and did a RAM Test.
I left the room, went to the kitchen to make some white tea with blueberry and when I came back to my room, the machine was OFF.


_**Update 2:**_
I forgot to mention this on my previous post and because it is happening again, I think this could be important to mention.

The Keyboard is NOT working while I am on Knoppix LiveCD!!!
I can use the mouse but I can NOT type one single character.

This is, by far, the weirdest case I have ever seen and it seems all the hardware issues exist in one device.

Now, it is ON. It is on the Live Desktop of Knoppix doing nothing. If it will turn OFF again or reboot while it is idle sitting doing nothing, this is 100% a hardware issue that I am not sure how to fix.

Will report back!

---

### Post by varunendra on 2013-12-12
Whether it helps or not, be aware that trying a "Live media" (be it cd or usb) itself can be a problem with only 256MB RAM, especially when it is something like a full fledged desktop session.

If you are inclined to use Live media for all the testing, may I suggest to try a very basic desktop version (only for diagnostics) like DSL, Slax, INSERT (included in UBCD) or whatever distro it is on the HBCD (Hiren's Boot CD). They are not 'full fledged' desktop distros and are designed to be as light as possible while running in live mode.

The fact that Knoppix ran fine only reaffirms this belief of mine, since distros like Knoppix or Slax are designed to be mainly used as Live CD/USBs. But in their attempt to provide a lot of commonly used 'features', they tend to be heavier than those I mentioned above.

As a test, could you do a full install of Lubuntu on an external drive (hard disk or flash), then try booting from it? A full installation runs mostly from the source disk, hence it has less chance of facing a bottleneck on the RAM part.

As for testing the RAM, you can do it from any live CD of Ubuntu or its other variants, and I'm sure you already know this. :)

---

### Post by Bucky Ball on 2013-12-12
Yea, look. This was advised an age ago on this thread and the thread is consequently beginning to go nowhere. You are NOT going to get a regular install of *buntu or any of the flavours on that computer. A short list of choices are:

Damn Small Linux
Puppy
Porteus
Minimal install (maybe, but some work involved)
Linux from Scratch (definitely but LOT of work involved)

Hunt down other lightweight distros. Anything else is a waste of time and you are wasting our time and yours if you are trying to install *ubuntu. No point in trying to offer help because there is none to give. Bottom line: They are NOT going to work.

---

### Post by varunendra on 2013-12-12
> **Bucky Ball said:**
> You are NOT going to get a regular install of *buntu or any of the flavours on that computer..

It may work, if the test with a full install on the external drive proves to be successful.

A fully installed system won't have the overhead of a virtual filesystem that is inherent part of a 'Live' system, so 256 MB should be sufficient for a light distro like Lubuntu. Although it may barely be usable when using apps like chromium browser or something similar that can dramatically eat up memory. But getting the OS itself up and running shouldn't be a problem. Once that is achieved, the swap space should be able to bear some load as well.

**PS:**
I just tested Lubuntu 12.04 on a virtual machine (vmware) with 324 MB RAM (and no Swap), and it was almost unusable. The point it makes is - trying a full fledged Desktop distro in **[COLOR="#FF0000"]Live[/COLOR]** mode, with only 256 MB RAM, is hopeless.

---

### Post by Bucky Ball on 2013-12-12
> **varunendra said:**
> ... trying a full fledged Desktop distro in **[COLOR="#FF0000"]Live[/COLOR]** mode, with only 256 MB RAM, is hopeless.

Exactly. You might be able to get to an Lubuntu desktop with 256 but that's about it. You might even get to open a terminal. I don't like your chances much better if you actually succeed in getting it installed.

---

### Post by amjjawad on 2013-12-12
> **Bucky Ball said:**
> Yea, look. This was advised an age ago on this thread and the thread is consequently beginning to go nowhere. You are NOT going to get a regular install of *buntu or any of the flavours on that computer.
A short list of choices are:

Damn Small Linux
Puppy
Porteus
Minimal install (maybe, but some work involved)
Linux from Scratch (definitely but LOT of work involved)

Hunt down other lightweight distros. Anything else is a waste of time and you are wasting our time and yours if you are trying to install *ubuntu. No point in trying to offer help because there is none to give. Bottom line: They are NOT going to work.

While I do respect your opinion, I strongly disagree because as long as the machine is not yet 'dead', there is nothing called impossible and if someone can't figure out a solution, someone else might be able to :)

Since 'you' think I am wasting 'your' time, would you please advice of other Ubuntu Forum that is 'more' helpful and user friendly which might be able to help?

I am definitely not attempting to waste anyone's time. I am 'NOT' interested to try other systems because I still think this can work on Ubuntu Based System, even the Mini ISO then adding up the needed packages.

If you speak on behalf of all Ubuntu Community and you are technically 100% sure this will 'not' work, as per what you posted, then feel free to close this thread and I am going to seek help/support elsewhere :)

Thank you!

---

### Post by amjjawad on 2013-12-12
Will mark this thread as SOLVED even though it is NOT.

Sorry to waste your time and I am going to seek help/support else where :)

Have a great day/evening/night!

---

### Post by mastablasta on 2013-12-12
BIOS can probably be updated using floppy or CD with DOS on it.

i got constant crashes and reboots with lubuntu on that low ram.

things to try do a text based install, reduce the GPU usage of ram in BIOS. just install soemthign on it see if it still missbehaves.

in windows XP i got reboots, crashes and like yours it turned itself off occasionally. though not always. and it took about 10 minutes to boot. firts i ran Ubuntu 10.04 but after a few updates it go really slow. so i switched to Chrunchbang with XFCE. it works well now. no crashes. i think it needs an update since i think it's older version of debian.

---

### Post by varunendra on 2013-12-12
> **amjjawad said:**
> Since 'you' think I am wasting 'your' time, would you please advice of other Ubuntu Forum that is 'more' helpful and user friendly which might be able to help?
Whoa! Why do you think any of us thinks you are wasting anyone's time? Or that this is no longer a 'user friendly' forum ? :)

Everyone is entitled to their opinions and so are you entitled your right to accept or ignore them. There is nothing to be taken so seriously. :P

**PS:**
Please don't mark the thread as [Solved] when it is not. The title becomes deceptive in that case.

---

### Post by amjjawad on 2013-12-12
Just for the record and for those who think that laptop is not going to work, please be informed that this laptop is now UP and RUNNING :)

It is not dead and it is working.

However, I had to try another system (not Ubuntu based) just to make sure it is NOT hopeless as some may think.

I will try later to install an Ubuntu based system, most likely the Mini ISO.

Thank you ;)

---

### Post by amjjawad on 2013-12-12
> **varunendra said:**
> **PS:**
Please don't mark the thread as [Solved] when it is not. The title becomes deceptive in that case.

But I have managed to get that 'hopeless' machine to work like a brand new laptop so marking this thread as solved is very good idea IMHO :D

Until I find more time (not today) to try an Ubuntu based system, most likely the Mini ISO, I don't have further Qs :)

Thank you, my friend and good to see you again ;)

---

### Post by varunendra on 2013-12-12
> **amjjawad said:**
> But I have managed to get that 'hopeless' machine to work like a brand new laptop..

Glad to know that :)

---

### Post by sudodus on 2013-12-12
> **varunendra said:**
> It may work, if the test with a full install on the external drive proves to be successful.

A fully installed system won't have the overhead of a virtual filesystem that is inherent part of a 'Live' system, so 256 MB should be sufficient for a light distro like Lubuntu. Although it may barely be usable when using apps like chromium browser or something similar that can dramatically eat up memory. But getting the OS itself up and running shouldn't be a problem. Once that is achieved, the swap space should be able to bear some load as well.

> **amjjawad said:**
> Just for the record and for those who think  that laptop is not going to work, please be informed that this laptop is  now UP and RUNNING :smile:

It is not dead and it is working.

However, I had to try another system (not Ubuntu based) just to make sure it is NOT hopeless as some may think.

I will try later to install an Ubuntu based system, most likely the Mini ISO.

Thank you :wink:

An easy way to make a full install according to *varunendra *is to use the [One Button Installer]("https://wiki.ubuntu.com/phillw/OBI"). It works for me in a Pentium II with 128 MB RAM with several 12.04 based flavours and re-spins including *kansasnoob*'s ***Precise Gnome Classic Tweaks***, which is heavier than Lubuntu. Try some of the tarballs including ***LubuntuCoreSaucy***.

So 256 MB should be enough to play (but not use it for heavy internet browsing). But run ***memtest*** again, there might be something wrong with the RAM, that will show, when most (or all) of it is used.

---

### Post by Bucky Ball on 2013-12-12
Over reaction. Never said anything about the machine beyond hopeless. Of course there's hope. What I did say was that a Ubuntu flavour would be virtually impossible to get running with 256mb of RAM. Please read more carefully. Never said the machine was not going to work with any OS. Even  suggested a list of OSs that may work on it. I wouldn't give up either and I never suggested any such thing and have no idea where you got the idea I did.

Yes, mini.iso will work, or at least install the kernel, but you are going to need to do a lot of planning regarding what packages you install after that. Start with the desktop environment. 

As I mentioned posts ago, Porteus or Puppy will probably work fine. 

To repeat: I never said anything about your hardware being beyond hope. It was software related. Take a deep breath.

---

### Post by amjjawad on 2013-12-16
The son of my neighbour didn't really like SliTaz mostly because there is no Wireless Connection. He was insisting to collect the Laptop because his son was nagging and insisting, etc so he didn't want to wait for more experiments. However, he was super happy and dazzled that almost dead and so old machine has worked and became faster :)

If he will bring it back to me, I think I know what to do :)

---

