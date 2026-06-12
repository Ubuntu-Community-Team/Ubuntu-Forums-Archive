---
title: "latest kernel update has broken nvidia"
date: 2007-02-10
forum: General Help
---

### Post by Choad on 2007-02-10
i get a kernel module/driver version mismatch error when i boot up

it seems the kernel module got updated but the nvidia driver stayed.

how can i fix this?

edit: ```
Feb 10 07:56:23 richard-laptop kernel: [17179608.168000] NVRM: API mismatch: the client has the version 1.0-9631, but
Feb 10 07:56:23 richard-laptop kernel: [17179608.168000] NVRM: this kernel module has the version 1.0-8776.  Please
Feb 10 07:56:23 richard-laptop kernel: [17179608.168000] NVRM: make sure that this kernel module and all NVIDIA driver
Feb 10 07:56:23 richard-laptop kernel: [17179608.168000] NVRM: components have the same version.
```

or maybe its the other way around?

---

### Post by tbroderick on 2007-02-10
Did you try re-installing nvidia.

---

### Post by Choad on 2007-02-10
already the latest version

---

### Post by igknighted on 2007-02-10
> **Choad said:**
> already the latest version

It doesnt matter.  When you install a new kernel the old module is no good, because it is built specifically to that kernel.  If you reinstall, it will build a new module that will work with your new kernel.

---

### Post by wall0159 on 2007-02-10
> **igknighted said:**
> It doesnt matter.  When you install a new kernel the old module is no good, because it is built specifically to that kernel.  If you reinstall, it will build a new module that will work with your new kernel.

Sorry to be a dunce, but can you tell me how to do this? had a look at the apt-get man page, and it's not obvious... I'm not sure how to pass the --reinstall option to apt-get without getting it to do anything else...

$> apt-get --reinstall nvidia*

doesn't cut it - seems to want a command, rather than just an option. can you point me in the right direction?

Cheers!

---

### Post by wall0159 on 2007-02-10
> **wall0159 said:**
> doesn't cut it - seems to want a command, rather than just an option. can you point me in the right direction?
Cheers!

Well, I questioned a bit too soon, I did
$> sudo apt-get remove nvidia-glx
$> sudo apt-get install nvidia-glx

which presumably does what you were suggesting, but when I try to startx, I still get
FATAL: Error running install command for nvidia
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***

Can you give me any suggestions?
(I performed the latest kernel upgrade, too)

Thanks,

---

### Post by Choad on 2007-02-10
> **wall0159 said:**
> Well, I questioned a bit too soon, I did
$> sudo apt-get remove nvidia-glx
$> sudo apt-get install nvidia-glx

which presumably does what you were suggesting, but when I try to startx, I still get
FATAL: Error running install command for nvidia
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***

Can you give me any suggestions?
(I performed the latest kernel upgrade, too)

Thanks,
glad im not the only one

its a bit shoddy that this happens at all really. and i seem to remember a big fuss about the same thing not long ago

---

### Post by wall0159 on 2007-02-10
> **Choad said:**
> its a bit shoddy that this happens at all really. and i seem to remember a big fuss about the same thing not long ago

well, it's a consequence of nvidia's binary drivers. I don't think it's really the fault of ubuntu (although I reckon it'd be technically possible to avoid this problem). I'm sure if we were using the "nv" (GPL) driver we wouldn't have these issues. Let's hope nvidia release their drivers under GPL!

---

### Post by gradedcheese on 2007-02-10
> its a bit shoddy that this happens at all really. and i seem to remember a big fuss about the same thing not long ago

I don't mean to sound rude, but this is basically what you can expect from binary drivers.  Basically, an open-source driver is provided with source.  If a kernel update includes a slightly different ABI, the community (or even you, if you wanted) can simply recompile it and provide it to those who update.  With the binary driver that these cards use, you're stuck until someone who has access to the source bothers to recompile it and release it.  Similarly, bugs can't be fixed, architecture support can't be done, etc.  I just thought I'd mention it in case you see people complaining about 'binary blobs' but you don't know why they do it ;)

> Let's hope nvidia release their drivers under GPL 

I don't think they will: they claimed (last I heard) that too much of their driver is written by third parties and therefore it's too hard to get the licensing and top secret 'stuff' under the hood in order to get a GPL release made.  Also I suspect that, as most of these companies do, they use the closed driver to hide workarounds to serious hardware defects and design flaws.

Here's a complaint about these types of drivers, in song :) [http://www.openbsd.org/lyrics.html#39](http://www.openbsd.org/lyrics.html#39)

---

### Post by c.ovidiu on 2007-02-10
Same problem here. The quick solution was to return to 2.6.17-10 for now (grub should give you the option to boot that kernel).

---

### Post by Choad on 2007-02-10
i never understood this. why does a driver have to be compiled in to the kernel?

surely thats a pertty bad design. it either means everyone has to have every driver module loaded, or alternatively everyone with different hardware has to have a different kernel.

why cant modules be loaded outside of the kernel? i mean, obviously theres a reason... but it seems to me the windows way of doing it works alot better for desktop use

---

### Post by sdyson on 2007-02-10
Try: 

```
sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx
```

If you're running this from the previous kernel then you'll need to replace `uname-r` with the actual kernel version (in my case 2.6.17-11-386)

---

### Post by syxbit on 2007-02-10
> **sdyson said:**
> Try: 

```
sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx
```

If you're running this from the previous kernel then you'll need to replace `uname-r` with the actual kernel version (in my case 2.6.17-11-386)
just did that.
I'm using the lupine repo.
I do wish Ubuntu would just host the latest nvidia, it's a real pain to have to add 3rd party repo's (it's not like they update THAT often) and considering nvidia is the best gfx card for linux, they should make more effort.

I tried
sudo aptitude reinstall nvidia-glx, but that didn't work
i then removed, and just did
sudo aptitude install nvidia-glx
this installed the old 87.76 drivers.

when i typed your command, it woked and installed the 97.46 drivers (odd, as i have the repo on, and i expected this to work.

problem is, then when i boot, i get the error 
"Nvidia kernel module has the version 8776, but this X module has the version 9746

any ideas how to make them the same?

---

### Post by sumadartson on 2007-02-10
Exactly the same problem here. The reinstalls don't work. Would reverting to the nvidia drivers hosted by Ubuntu help?

---

### Post by sumadartson on 2007-02-10
The above turned out to work for now. I just eliminated the 'foreign' repository and reverted back to the ubuntu-hosted driver. At least I have a working pc now. hooray

So, comment out the lupine repo, uninstall nvidia-glx and install nvidia-glx again; this should give you a version that works with the most recent kernel update.

---

### Post by russell.h on 2007-02-10
I recommend heading over to [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and getting the latest stable version of 'envy'.

When your driver gets broke (the kernel update broke mine too) you just switch over to command line, type envy, then it will automatically download the latest nvidia driver and set up the kernel module or whatever, then restart X for you.

---

### Post by neighborlee on 2007-02-10
> **wall0159 said:**
> well, it's a consequence of nvidia's binary drivers. I don't think it's really the fault of ubuntu (although I reckon it'd be technically possible to avoid this problem). I'm sure if we were using the "nv" (GPL) driver we wouldn't have these issues. Let's hope nvidia release their drivers under GPL!

Do these breakages occur on other distros as well ?

What caused the abi shift in the first place, and what caused this update not to be tested to avoid problems for ubuntu users ?

If updates are flying out the door instead of QA being done on them first, I think most people would rather wait a little while.  If these changes were of a severe security nature, could a warning have been issues instead, and have given developers more time to make sure it worked on at least most mainstream boxes ( ultimately updates should work everywhere but in a ideal world...)

just wondering because breakage really sucks and reduces overall community trust which in time can yield to other problems...not just community ones either ;(

I think ubuntu has alot going for it, but if this is how things are ( like the ATI mess not long ago ? ) I guess  each individual must reconsider their options.

cheers
nl

---

### Post by tipsqueal on 2007-02-10
I read this thread along with a few others, because my Nvidia drivers were also broken with the update. What I decided to do after reading multiple threads is to comment out my lupine source for the nvidia-glx driver and reinstall the ubuntu hosted nvidia driver. This worked, but when I rebooted and logged in and went to my desktop, something was obviously wrong. I'm using a Viewsonic 20" wide screen LCD, with a native resolution of 1680 x 1050 and the refresh rate is definitely wrong. I went to the preferences section then I selected resolution and it locks me into 1 option, 75 hertz, which looks terrible. I can't really describe what it looks like, but someone may know, it kinda looks all blurry and pixelized, but everything is at the right proportions it should be for the resolution. In order for it to not look messed up, I have to set the resolution to 1280 x 1024, but that looks like complete trash because it's not the native resolution. The only way that I know how to get it to properly work is to use the other beta drivers, that currently don't work with this kernel. Can anyone else help me out?

---

### Post by gradedcheese on 2007-02-10
> **Choad said:**
> i never understood this. why does a driver have to be compiled in to the kernel?

surely thats a pertty bad design. it either means everyone has to have every driver module loaded, or alternatively everyone with different hardware has to have a different kernel.

why cant modules be loaded outside of the kernel? i mean, obviously theres a reason... but it seems to me the windows way of doing it works alot better for desktop use

Because they need to live in kernel space?  There's a huge separation between 'user space' and 'kernel space', and for a very good reason.  Things that play with hardware directly live in kernel space as kernel modules.  Things that live in user space may talk to kernel space through special communication channels, but that's about it (no access to hardware).  This is actually the same in Windows.  Linux modules are not "always loaded", they get loaded when they are needed.  So "every driver module loaded" is not true (same in Windows).  This is also why the different kernel statement isn't true either...

There's nothing wrong with the Kernel design, what's wrong is people's use of binary blob drivers and the manufacturer's continuing policy of making them (the alternative: they give a reference manual to the community and the community writes a real driver for their chipset, or they go so far as to release GPL code themselves).

The ABI change was probably for a good reason, changes and improvements are made to the kernel all the time, and they are safe to do because drivers can be recompiled!  The kernel developers don't even think about the binary blob junk, which obviously can't be recompiled, but those aren't even supposed to exist ;)  And yes, this same problem occurs in other distributions.

---

### Post by spockrock on 2007-02-10
guys the problem is this you are using a newer linux restricted module, that has the 8776 module, but you guys are using the 9xxx driver.  do what I am doing wait, and boot in with generic kernel 2.6.17-10 and wait for the LRM for kernel -11 to hit the repo for you driver.

---

### Post by Choad on 2007-02-10
but you can install binary drivers in windows without a kernel re-compile

that was my point really :)

---

### Post by gradedcheese on 2007-02-10
> **Choad said:**
> but you can install binary drivers in windows without a kernel re-compile

that was my point really :)

Right, because no one has access to their kernel and no one recompiles it.  They therefore can't risk changing the ABI, and so on (actually they do it occasionally, and then drivers are not "XP compatible" and so on, then the manufacturers release new drivers, I'm sure you've seen it before).

Anyhow, I hope you understand that when you use binary drivers in Linux, you're doing something that is actually not supposed to happen, and therefore you cannot expect any support from the kernel developers.  In fact, bug reports and the like from users with 'tainted' kernels aren't generally accepted.

In this case, the problem was that the Ubuntu people didn't catch the ABI change before pushing the new kernel package to the updates, what was definitely a mistake since Ubuntu users are (unfortunately) expected to sometimes have binary blob drivers.  

If you're interested, there are some very good resources online and at the book store about the Linux kernel, its architecture, and why things are the way they are.  If you read about it, I'm pretty sure you'll be fairly impressed with the design.

---

### Post by deanlinkous on 2007-02-10
What can proprietary do for you?

---

### Post by syxbit on 2007-02-10
i fixied it with envy.
it's still REALLY annoying.
ubuntu will never get anywhere if things like these keep happening.
this is the 3rd time an update has broken xorg.
I don't care who's fault it is (fanboys will just blame it on closed source nvidia drivers, and defent ubuntu to death, but in reality, I DON'T CARE WHOSE FAULT IT IS, I JUST KNOW IT ISN'T MINE, AND THAT THESE KINDS OF THINGS DON'T EVER HAPPEN ON MY BROTHERS MACBOOKPRO)

---

### Post by gradedcheese on 2007-02-10
I'm going to stop because indeed my comments are probably not relevant to this thread.  However, I am not a 'fanboy'.  I am just explaining to you why it is that this is broken, why it's not the "kernel's fault", and why binary drivers are wrong.  If you don't care about it, that is alright.  Perhaps a proprietary OS (where this policy is acceptable) is a better option in that case (a 'fanboy' wouldn't tell you that, right?).  For me, having kernel source and the Linux kernel's development process is absolutely important, and I will support the kernel developer's policy on binary blobs.

---

### Post by wall0159 on 2007-02-10
> **sdyson said:**
> Try: 

```
sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx
```

If you're running this from the previous kernel then you'll need to replace `uname-r` with the actual kernel version (in my case 2.6.17-11-386)

Excellent - that did the trick. Thank you very much - I'll bear that in mind for the next kernel upgrade!

Cheers!

---

### Post by Choad on 2007-02-10
ok, i understand where you're coming from

but the linux kernel gets updated ALL the time. we cant really expect companies in the proprietry model to ever support linux if they have to open source their drivers and give away all their precious secrets to the competitors, can we? and we cant expect them to release a driver for every kernel version either.

i just dont see how this isnt a disadvantage to linux. we really need a universal driver interface with the kernel that allows any blob to work. well, thats my opinion anyway. yes, in an ideal foss world, everyone would open their drivers up, but that is simply not reality.

what is the ABI by the way? and why must it change in linux? i assume that this is the reason you cant install a binary driver in linux without recompiling the kernel.

---

### Post by neighborlee on 2007-02-10
> **gradedcheese said:**
> I'm going to stop because indeed my comments are probably not relevant to this thread.  However, I am not a 'fanboy'.  I am just explaining to you why it is that this is broken, why it's not the "kernel's fault", and why binary drivers are wrong.  If you don't care about it, that is alright.  Perhaps a proprietary OS (where this policy is acceptable) is a better option in that case (a 'fanboy' wouldn't tell you that, right?).  For me, having kernel source and the Linux kernel's development process is absolutely important, and I will support the kernel developer's policy on binary blobs.

Yes, to the exclusion of logic ;)...if binary blobs cant' be included due to their being proprietary and not knowing full well of the intent of the code, we get it on that level, but I think the attitude does more harm than good and is not relevant to the longterm goals of linux  which to my way of thinking should also include' things just work' mentality as well....if things work against that methodology to me its a losing  battle..one that the cannonical/*spire merger will go along ways to fixing..we do better when we strive to work together.even if it means temporary mergers between closed and OSS.

cheers
nl

---

### Post by neighborlee on 2007-02-10
> **Choad said:**
> ok, i understand where you're coming from

but the linux kernel gets updated ALL the time. we cant really expect companies in the proprietry model to ever support linux if they have to open source their drivers and give away all their precious secrets to the competitors, can we? and we cant expect them to release a driver for every kernel version either.

i just dont see how this isnt a disadvantage to linux. we really need a universal driver interface with the kernel that allows any blob to work. well, thats my opinion anyway. yes, in an ideal foss world, everyone would open their drivers up, but that is simply not reality.

what is the ABI by the way? and why must it change in linux? i assume that this is the reason you cant install a binary driver in linux without recompiling the kernel.

exactly..only fanboys of linux/OSS would think the reverse holds any merit 'atm' ..

maybe in a future world..but atm we must work together ;)

to opposite extreme does none of us much good ;)

cheers
g.leej

---

### Post by syxbit on 2007-02-10
> **Choad said:**
> ok, i understand where you're coming from

but the linux kernel gets updated ALL the time. we cant really expect companies in the proprietry model to ever support linux if they have to open source their drivers and give away all their precious secrets to the competitors, can we? and we cant expect them to release a driver for every kernel version either.

i just dont see how this isnt a disadvantage to linux. we really need a universal driver interface with the kernel that allows any blob to work. well, thats my opinion anyway. yes, in an ideal foss world, everyone would open their drivers up, but that is simply not reality.

what is the ABI by the way? and why must it change in linux? i assume that this is the reason you cant install a binary driver in linux without recompiling the kernel.

that's like me saying
"i'm making a windows program, but because i can't get windows source code, my program is no good. BUT since it's not my fault, everyone should use my program anyway"
it's ridiculous. we don't care who's to blame for breakage, we just care that it doesn't happen.
it's true, the linux kernel doesn't have control over nvidia binaries, but they could test compatibility, and give a warning, at least
i had a big assignment to get done.
imagine my friends laughing at me (as i've always told them linux is the most stable OS) that i have to trouble shoot for an hour before i can write my paper......

---

### Post by OffHand on 2007-02-10
> **syxbit said:**
> 
imagine my friends laughing at me (as i've always told them linux is the most stable OS) that i have to trouble shoot for an hour before i can write my paper......

If you don't mess with it, it is. No one put a gun to your head and forced you to use the binary blobs.

---

### Post by hotani on 2007-02-10
This is what happens when I attempt to run the fix posted above:

```

shell> sudo apt-get install --reinstall linux-restricted-modules-2.6.17-11-generic nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 4491kB/12.2MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  nvidia-glx
Install these packages without verification [y/N]? y
Err http://albertomilone.com binary/ nvidia-glx 1.0.9631+2.6.17.8-1
  404 /drivers/edgy/nonlegacy/32bit/binary/nvidia-glx_1.0.9631+2.6.17.8-1_i386.deb
Failed to fetch http://albertomilone.com/drivers/edgy/nonlegacy/32bit/binary/nvidia-glx_1.0.9631+2.6.17.8-1_i386.deb  404 /drivers/edgy/nonlegacy/32bit/binary/nvidia-glx_1.0.9631+2.6.17.8-1_i386.deb
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by Choad on 2007-02-10
me too. altho i have enough linux knowledge to get a workable system with the nv drivers. still, this is just another reason why i dont feel confident enough about ubuntu to give it to anyone i meet and know that it will meet their requirements with no effort.

i mean, people go on about the modularity of linux, and the monolithic nature of windows, and how modularity is so much better (which it is) but yet when it comes to drivers, linux is about as un-modular as it gets. *everything* is compiled in the kernel.

---

### Post by Choad on 2007-02-10
> **OffHand said:**
> If you don't mess with it, it is. No one put a gun to your head and forced you to use the binary blobs.
but then you're left with no 3d acceleration, and therefore a £150 paperweight inside your machine

---

### Post by Choad on 2007-02-10
> **hotani said:**
> This is what happens when I attempt to run the fix posted above:

```

shell> sudo apt-get install --reinstall linux-restricted-modules-2.6.17-11-generic nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 4491kB/12.2MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  nvidia-glx
Install these packages without verification [y/N]? y
Err http://albertomilone.com binary/ nvidia-glx 1.0.9631+2.6.17.8-1
  404 /drivers/edgy/nonlegacy/32bit/binary/nvidia-glx_1.0.9631+2.6.17.8-1_i386.deb
Failed to fetch http://albertomilone.com/drivers/edgy/nonlegacy/32bit/binary/nvidia-glx_1.0.9631+2.6.17.8-1_i386.deb  404 /drivers/edgy/nonlegacy/32bit/binary/nvidia-glx_1.0.9631+2.6.17.8-1_i386.deb
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```
try envy. it worked for me :)

---

### Post by OffHand on 2007-02-10
> **Choad said:**
> but then you're left with no 3d acceleration, and therefore a £150 paperweight inside your machine

You can get 3D from the nvidia drivers from the repositories.

---

### Post by amano on 2007-02-10
> **russell.h said:**
> I recommend heading over to [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and getting the latest stable version of 'envy'.

When your driver gets broke (the kernel update broke mine too) you just switch over to command line, type envy, then it will automatically download the latest nvidia driver and set up the kernel module or whatever, then restart X for you.

That didn't work for me. I bootet into the failsafe mode. i started my internet dialin script and envy. It downloaded the driver and configured it. But the problem remains.

BTW, as this was my first experience with the failsafe mode that you can select from grub: 

Is it normal that you are automatically logged in as root?

---

### Post by sultanoswing on 2007-02-10
Envy worked fine for me too - pain free kernel/driver upgrading! :)

Of course you have ton install envy first, then:

When the 'X Server Failed To Start' message comes up after a kernel upgrade, simply ctrl-shift-F1 > login as root > type 'envy' and you're good to go.

Personally, I don't let the envy script autoconfigure my xorg.conf, since I already have the xorg.conf options set just how I want them.

---

### Post by amano on 2007-02-10
Oh. Yes. Perhaps I shouldn't have tried the recovery mode. I will try the tty1 as well.

EDIT: That works. I wonder what the recovery mode is for. It logs you in as root without asking for the password. And your settings have no effects? Strange

BTW, now Beryl isn't working anymore. It starts up but always falls back to metacity. I reinstalled the beryl packages via synaptic, but no luck

Oh my... :/

---

### Post by rko618 on 2007-02-10
> **russell.h said:**
> I recommend heading over to [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and getting the latest stable version of 'envy'.

When your driver gets broke (the kernel update broke mine too) you just switch over to command line, type envy, then it will automatically download the latest nvidia driver and set up the kernel module or whatever, then restart X for you.


Wow, that was awesome.  I really like the envy way of fixing this.

I tried running sudo apt-get install --reinstall linux-restricted-modules-2.6.17-11-generic nvidia-glx but that didn't work but envy did the trick flawlessly :).

---

### Post by russell.h on 2007-02-10
> **amano said:**
> Oh. Yes. Perhaps I shouldn't have tried the recovery mode. I will try the tty1 as well.

EDIT: That works. I wonder what the recovery mode is for. It logs you in as root without asking for the password. And your settings have no effects? Strange

BTW, now Beryl isn't working anymore. It starts up but always falls back to metacity. I reinstalled the beryl packages via synaptic, but no luck

Oh my... :/

EDIT2: Seems to happen to others as well: [http://forum.beryl-project.org/viewtopic.php?f=36&t=3533&hilit=kernel+update](http://forum.beryl-project.org/viewtopic.php?f=36&t=3533&hilit=kernel+update)
And there doesn't seem to be fast and easy fix. :(
Did you let it autoconfig your xorg.conf? If so it probably got rid of whatever options you had set to make Beryl work (thats what happened to me).

---

### Post by Shakabab on 2007-02-11
[QUOTE=syxbit]i fixied it with envy. it's still REALLY annoying. ubuntu will never get anywhere if things like these keep happening. this is the 3rd time an update has broken xorg. I don't care who's fault it is (fanboys will just blame it on closed source nvidia drivers, and defent ubuntu to death, but in reality, I DON'T CARE WHOSE FAULT IT IS, I JUST KNOW IT ISN'T MINE, AND THAT THESE KINDS OF THINGS DON'T EVER HAPPEN ON MY BROTHERS MACBOOKPRO)[/QUOTE]

Then go get a Macbook pro. Your brother paid a fair amount of money for one, and he can expect high standards because he's working with software **specifically tuned** for that A-quality (and priced) hardware thats in those configurations. It's quite a lot easier for developers to get things stable if you don't have to support thousands of different configurations.

That being said, you're attitude is ridiculous. It **does** matter whose fault it is. How would you expect this to ever be properly fixed if everybody would think like that? Geez, if you want every decision to be taken for you head back to Windows or go buy a decent Mac. Linux is the greatest example of consumer generated content and due to its nature you sometimes have to have a little patience with it. For free software, I really don't mind. 

[QUOTE=syxbit]that's like me saying
"i'm making a windows program, but because i can't get windows source code, my program is no good. BUT since it's not my fault, everyone should use my program anyway"
it's ridiculous. we don't care who's to blame for breakage, we just care that it doesn't happen.
it's true, the linux kernel doesn't have control over nvidia binaries, but they could test compatibility, and give a warning, at least i had a big assignment to get done.
imagine my friends laughing at me (as i've always told them linux is the most stable OS) that i have to trouble shoot for an hour before i can write my paper......[/QUOTE]

Then maybe you should used your head before you go troubleshooting. Lets see... I updated my kernel and now I can't login to Xorg anymore.. mmm what could be the problem here? Oh wait, of course. Its the damn kernel update. I'll just switch back to the previous and will be up and running again. This whole process shouldn't have taken more than five minutes.  Seriously, if you depent on your OS that much, go buy a book about it.

---

### Post by sdyson on 2007-02-11
> **hotani said:**
> This is what happens when I attempt to run the fix posted above:

```

shell> sudo apt-get install --reinstall linux-restricted-modules-2.6.17-11-generic nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 4491kB/12.2MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  nvidia-glx
Install these packages without verification [y/N]? y
Err http://albertomilone.com binary/ nvidia-glx 1.0.9631+2.6.17.8-1
  404 /drivers/edgy/nonlegacy/32bit/binary/nvidia-glx_1.0.9631+2.6.17.8-1_i386.deb
Failed to fetch http://albertomilone.com/drivers/edgy/nonlegacy/32bit/binary/nvidia-glx_1.0.9631+2.6.17.8-1_i386.deb  404 /drivers/edgy/nonlegacy/32bit/binary/nvidia-glx_1.0.9631+2.6.17.8-1_i386.deb
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

Sounds like you don't have a net connection. Try booting into the previous kernel from grub and try the command from there. That's what I did.

---

### Post by hotani on 2007-02-11
got it going again with [Envy](http://albertomilone.com/nvidia_scripts1.html). :)

---

### Post by shareMenaPeace on 2007-02-11
Doh, came back this morning booted and see message nvidiia.ko not found - was a little scary :)

I like to see a notification WHEN xyou choose to update a kernel that this is pointed out along with fixes (envy etc).

Cheers

---

### Post by syxbit on 2007-02-11
> **Shakabab said:**
> Then go get a Macbook pro. Your brother paid a fair amount of money for one, and he can expect high standards because he's working with software **specifically tuned** for that A-quality (and priced) hardware thats in those configurations. It's quite a lot easier for developers to get things stable if you don't have to support thousands of different configurations.

That being said, you're attitude is ridiculous. It **does** matter whose fault it is. How would you expect this to ever be properly fixed if everybody would think like that? Geez, if you want every decision to be taken for you head back to Windows or go buy a decent Mac. Linux is the greatest example of consumer generated content and due to its nature you sometimes have to have a little patience with it. For free software, I really don't mind. 



Then maybe you should used your head before you go troubleshooting. Lets see... I updated my kernel and now I can't login to Xorg anymore.. mmm what could be the problem here? Oh wait, of course. Its the damn kernel update. I'll just switch back to the previous and will be up and running again. This whole process shouldn't have taken more than five minutes.  Seriously, if you depent on your OS that much, go buy a book about it.

knowing people like you exist make me embarrassed to be a linux user sometimes..
so basically, if someone complains that something doesn't work your reply is
"Don't expect it to work,,,,,,it's free.....if you want your OS to work buy a macbookpro"

RIDICULOUS

---

### Post by kweiner on 2007-02-12
Returning to kernel 2.6.17-generic did not work for me.  X still did not start because it couldn't load the nvidia kernel module.  I was able to start X after changing the driver setting in xorg.conf from nvidia to nv, however.  But now, I can't even start glxgears :(

What do I need to do in order to return to using the binary nvidia driver with the new 2.6.17-generic kernel?

---

### Post by skabaas on 2007-02-12
Envy fixed the problem for me too!

---

### Post by WinterWeaver on 2007-02-12
To anyone that used Envy to fix... Does your beryl work?

I had a bad experience with Envy a couple of months back. It worked the first 2 weeks, then there was some minor update, and my xgl and xorg was broken again.

... I'm too afraid to use envy again .. >.<

.sigh... this is now the 3rd time this happens to me... and I've had Ubuntu for only 6 months now :( and the worse thing is, everything was running sooo beautifully last night. Today, I run the update, and now it's all broken.

...

---

### Post by NickPresta on 2007-02-12
So is this upgrade stable or not?

Right now, I have:
```
$ sudo apt-get -s dist-upgrade
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-2.6.17-11 linux-headers-2.6.17-11-generic linux-image-2.6.17-11-generic linux-restricted-modules-2.6.17-11-generic
The following packages will be upgraded:
  language-pack-en language-pack-kde-en libgnomevfs2-0 libgnomevfs2-common linux-generic linux-headers-generic linux-image-generic linux-libc-dev linux-restricted-modules-common
  linux-restricted-modules-generic nvidia-glx
11 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Inst language-pack-en [1:6.10+20061130] (1:6.10+20070115 Ubuntu:6.10/edgy-updates)
Inst language-pack-kde-en [1:6.10+20061130] (1:6.10+20070115 Ubuntu:6.10/edgy-updates)
Inst libgnomevfs2-0 [2.16.1-0ubuntu4] (2.16.1-0ubuntu7 Ubuntu:6.10/edgy-updates) []
Inst libgnomevfs2-common [2.16.1-0ubuntu4] (2.16.1-0ubuntu7 Ubuntu:6.10/edgy-updates)
Inst linux-image-2.6.17-11-generic (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Inst linux-image-generic [2.6.17.10] (2.6.17.11 Ubuntu:6.10/edgy-security)
Inst linux-restricted-modules-common [2.6.17.7-10.1-9746] (2.6.17.7-11.1-9746 lupine:6.10/edgy)
Inst linux-restricted-modules-2.6.17-11-generic (2.6.17.7-11.1-9746 lupine:6.10/edgy)
Inst linux-restricted-modules-generic [2.6.17.10] (2.6.17.11 Ubuntu:6.10/edgy-security)
Inst linux-generic [2.6.17.10] (2.6.17.11 Ubuntu:6.10/edgy-security)
Inst linux-headers-2.6.17-11 (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Inst linux-headers-2.6.17-11-generic (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Inst linux-headers-generic [2.6.17.10] (2.6.17.11 Ubuntu:6.10/edgy-security)
Inst linux-libc-dev [2.6.17.1-10.34] (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Inst nvidia-glx [1.0.9746+2.6.17.7-10.1-9746] (1.0.9746+2.6.17.7-11.1-9746 lupine:6.10/edgy)
Conf language-pack-en (1:6.10+20070115 Ubuntu:6.10/edgy-updates)
Conf language-pack-kde-en (1:6.10+20070115 Ubuntu:6.10/edgy-updates)
Conf libgnomevfs2-common (2.16.1-0ubuntu7 Ubuntu:6.10/edgy-updates)
Conf libgnomevfs2-0 (2.16.1-0ubuntu7 Ubuntu:6.10/edgy-updates)
Conf linux-image-2.6.17-11-generic (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Conf linux-image-generic (2.6.17.11 Ubuntu:6.10/edgy-security)
Conf linux-restricted-modules-common (2.6.17.7-11.1-9746 lupine:6.10/edgy)
Conf linux-restricted-modules-2.6.17-11-generic (2.6.17.7-11.1-9746 lupine:6.10/edgy)
Conf linux-restricted-modules-generic (2.6.17.11 Ubuntu:6.10/edgy-security)
Conf linux-generic (2.6.17.11 Ubuntu:6.10/edgy-security)
Conf linux-headers-2.6.17-11 (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Conf linux-headers-2.6.17-11-generic (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Conf linux-headers-generic (2.6.17.11 Ubuntu:6.10/edgy-security)
Conf linux-libc-dev (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Conf nvidia-glx (1.0.9746+2.6.17.7-11.1-9746 lupine:6.10/edgy)
```

This should be fine, right?

---

### Post by arcman on 2007-02-12
Welllll, that was sure fun!
After restarting from the update, X was completely broken.  I was able to get the server back up from a backdated xorg.conf file, and then got the nVidia driver back running through envy.  Then after I fully repaired the xorg.conf file I was able to get Beryl running normally (basically had to follow the original installation instructions off of the beryl wiki, everything pertaining to xorg.conf).  

This being the second time an update has completely trashed X, looks like I'm going to have to disable auto updates.

---

### Post by russell.h on 2007-02-12
I saw a linux-restricted-modules update and installed it, not sure whether that means the kernel update no longer breaks anything.

@ syxbits: Linux is free and open source (well everything in question with the exception of the nvidia driver is open source). As much as I agree that these sorts of things should be avoided, quite frankly you come across sounding like a spoiled idiot when you get angry at people who are giving you software for free for allowing a third party application that you installed to "break" it.

That being said, if Ubuntu expects to compete in the desktop OS market it is going to need to stay caught up, which, in 2007 means providing full "out of the box" support for beryl and/or compiz that won't knock unsuspecting linux novices back to the command line.

But seriously, lets keep the conversation rational and the angry capitalization to a minimum.

---

### Post by NickPresta on 2007-02-12
I would just like to state that the upgrade did not break anything for me. 
```
$ sudo apt-get -s dist-upgrade
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-2.6.17-11 linux-headers-2.6.17-11-generic linux-image-2.6.17-11-generic linux-restricted-modules-2.6.17-11-generic
The following packages will be upgraded:
  language-pack-en language-pack-kde-en libgnomevfs2-0 libgnomevfs2-common linux-generic linux-headers-generic linux-image-generic linux-libc-dev linux-restricted-modules-common
  linux-restricted-modules-generic nvidia-glx
11 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Inst language-pack-en [1:6.10+20061130] (1:6.10+20070115 Ubuntu:6.10/edgy-updates)
Inst language-pack-kde-en [1:6.10+20061130] (1:6.10+20070115 Ubuntu:6.10/edgy-updates)
Inst libgnomevfs2-0 [2.16.1-0ubuntu4] (2.16.1-0ubuntu7 Ubuntu:6.10/edgy-updates) []
Inst libgnomevfs2-common [2.16.1-0ubuntu4] (2.16.1-0ubuntu7 Ubuntu:6.10/edgy-updates)
Inst linux-image-2.6.17-11-generic (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Inst linux-image-generic [2.6.17.10] (2.6.17.11 Ubuntu:6.10/edgy-security)
Inst linux-restricted-modules-common [2.6.17.7-10.1-9746] (2.6.17.7-11.1-9746 lupine:6.10/edgy)
Inst linux-restricted-modules-2.6.17-11-generic (2.6.17.7-11.1-9746 lupine:6.10/edgy)
Inst linux-restricted-modules-generic [2.6.17.10] (2.6.17.11 Ubuntu:6.10/edgy-security)
Inst linux-generic [2.6.17.10] (2.6.17.11 Ubuntu:6.10/edgy-security)
Inst linux-headers-2.6.17-11 (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Inst linux-headers-2.6.17-11-generic (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Inst linux-headers-generic [2.6.17.10] (2.6.17.11 Ubuntu:6.10/edgy-security)
Inst linux-libc-dev [2.6.17.1-10.34] (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Inst nvidia-glx [1.0.9746+2.6.17.7-10.1-9746] (1.0.9746+2.6.17.7-11.1-9746 lupine:6.10/edgy)
Conf language-pack-en (1:6.10+20070115 Ubuntu:6.10/edgy-updates)
Conf language-pack-kde-en (1:6.10+20070115 Ubuntu:6.10/edgy-updates)
Conf libgnomevfs2-common (2.16.1-0ubuntu7 Ubuntu:6.10/edgy-updates)
Conf libgnomevfs2-0 (2.16.1-0ubuntu7 Ubuntu:6.10/edgy-updates)
Conf linux-image-2.6.17-11-generic (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Conf linux-image-generic (2.6.17.11 Ubuntu:6.10/edgy-security)
Conf linux-restricted-modules-common (2.6.17.7-11.1-9746 lupine:6.10/edgy)
Conf linux-restricted-modules-2.6.17-11-generic (2.6.17.7-11.1-9746 lupine:6.10/edgy)
Conf linux-restricted-modules-generic (2.6.17.11 Ubuntu:6.10/edgy-security)
Conf linux-generic (2.6.17.11 Ubuntu:6.10/edgy-security)
Conf linux-headers-2.6.17-11 (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Conf linux-headers-2.6.17-11-generic (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Conf linux-headers-generic (2.6.17.11 Ubuntu:6.10/edgy-security)
Conf linux-libc-dev (2.6.17.1-11.35 Ubuntu:6.10/edgy-security)
Conf nvidia-glx (1.0.9746+2.6.17.7-11.1-9746 lupine:6.10/edgy)
```

I logged in, everything was fine (Beryl too), and I uninstalled the 2.6.17.10 kernel to remove it's entry from my menu.lst.

---

### Post by eduardoeltortuga on 2007-02-12
I really thought that envy would work. I've been searching high an low to fix my puter since I last updated Ubuntu. I had this computer Smoking man! My 1st dual boot! I even got beryl to work after crashing the first few times. 
     I installed envy and I really thought this would give me the new nvidia drivers to work with the new linux kernel.  I'm still getting the message "Failed to start the X server. Details are diff though. "(WW) Warning  (EE) error (NI) not implemented". 
Any more help would sure be appreciated!

---

### Post by kipeloff on 2007-02-12
I've got the same error with driver version mismach.
Return to the previous version helped, then I've tried to reinstall kernel modules and nvidia-glx (apt-get shouting about some package missing try apt-get upgate or fix-missing). I double checked my sources list.
Then I simple removed nvidia-glx and installed it back, "X" is back in newest version.

---

### Post by mcrae on 2007-02-12
Hi,
I had the similar problem after updaing the kernel...I have installed Xgl/compiz on my Nvidia and it seemed working well untill I tried to open xterm
then there was this message:

Warning: Color name "black" is not defined

any ideas how to solve this; I really work a lot with xterminals and they are behaving bad now

---

### Post by hotani on 2007-02-12
> **WinterWeaver said:**
> To anyone that used Envy to fix... Does your beryl work?

...

Yes. When it finishes doing its thing and asks if you want it to update xorg.conf, choose NO.

---

### Post by rafciu123 on 2007-02-12
Hi there,

I am a newbie user and I tried to follow the flow of posts but I got lost. I have the same problem and I am able to see X in kernel 10 but not in 11. What command should I use to make it work?
Please also note to which kernel I should boot when I use this command?

---

### Post by russell.h on 2007-02-12
> **rafciu123 said:**
> Hi there,

I am a newbie user and I tried to follow the flow of posts but I got lost. I have the same problem and I am able to see X in kernel 10 but not in 11. What command should I use to make it work?
Please also note to which kernel I should boot when I use this command?

The most straightforward (although not necessarily the easiest) is:

1. Boot the new kernel, select no when you get to the error messages, and get to the command line (you may have to press Control + Alt + F1 to do this, but I don't think so). Once you are at the command line log in as you (type your name at the prompt, then your password when it asks).

2. Now put in the following commands:
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb
```
```
sudo dpkg -i envy_0.8.1-0ubuntu6_all.deb
```
<here it will ask for your password, so type that in>
```
envy
```
Now it will probably ask for your password again. Type that in and it will take you to a list of options. You want option 1, so just type in the number 1 and press enter.

Envy will now download and install (building a new kernel module if my understanding is correct) the latest nvidia driver. It will ask you a few questions, most notably whether you want it to automatically reconfigure xorg.conf. You probably want to answer no to this, since allowing it to do this will break Beryl or Compiz if they are running, and unless you have broken xorg.conf since it was last working it should still work.

It will ask you if you want to restart the X server, hit yes. Your GUI should boot up now.

---

### Post by amano on 2007-02-12
> **WinterWeaver said:**
> To anyone that used Envy to fix... Does your beryl work?

I had a bad experience with Envy a couple of months back. It worked the first 2 weeks, then there was some minor update, and my xgl and xorg was broken again.

... I'm too afraid to use envy again .. >.<

.sigh... this is now the 3rd time this happens to me... and I've had Ubuntu for only 6 months now :( and the worse thing is, everything was running sooo beautifully last night. Today, I run the update, and now it's all broken.

...

Envy disabled the composite extension for me in the xorg.conf. I had to set it to "enabled" manually. But otherwise nvidia and beryl work fine now.

And maybe I should have told envy to NOT adjust the xorg.conf. It had asked me, but I said "yes".

---

### Post by BigWillyT on 2007-02-12
> **spockrock said:**
> guys the problem is this you are using a newer linux restricted module, that has the 8776 module, but you guys are using the 9xxx driver.  do what I am doing wait, and boot in with generic kernel 2.6.17-10 and wait for the LRM for kernel -11 to hit the repo for you driver.
Is this why I'm having issues with X breaking using the 9xxx driver that I manually dl'd and installed from the NVIDIA site?  Didn't start happening until after the kernel update and is easily fixed with a reinstall of the driver.  Had similar issues before that whenever I rebooted my machine(I dual-boot) that X would break and I'd have to reinstall driver.  I was able to fix that problem by disabling "nv" which is still disabled yet every time I boot into Ubunutu, X is broken. :(

---

### Post by Shakabab on 2007-02-12
> **syxbit said:**
> knowing people like you exist make me embarrassed to be a linux user sometimes..
so basically, if someone complains that something doesn't work your reply is
"Don't expect it to work,,,,,,it's free.....if you want your OS to work buy a macbookpro"

RIDICULOUS

Take an English course, then do some self-reflecting. You might pick up a usefull skill or two. As for you 'embarrassed to be a linux user ' point of view: go buy a book or two. Learn something and come back with a little more knowledge about people and operating systems. You do a lot of talking and complaining, but there's little constructive that comes out of your mouth. 

If you really believe the point of my post was that 'you can't expect free software to work' you might need to take more than one English course actually. My point was and is that you can't get the level of support on a free operating system that you get on an os like Mac or Windows. Unless you pay for professional support you have to have a little patience from time to time. And like I said, if small inconveniences like this drive you up the roof, you might need to consider heading back to Windows or get some professional (paid) support. In fact, if you know so little about this operating system  (and you depend on it this badly) those might be your best options. Complaining gets you nowhere.

You sure as hell can't start shouting 'I want this fixed, because I use this software and it was not my fault it was broken. And i want it fixed NOW.' Make a donation, or contribute to the community otherwise to improve things. Nobody likes errors. But unlike you, most people would gladly participate in making sure that error won't happen again. You Sir, take something thats beautiful free and start demanding the community to obeys your direct needs. In the warez scene, they would simply call you a leecher. They would be right.

---

### Post by syxbit on 2007-02-12
> **Shakabab said:**
> Take an English course, then do some self-reflecting. You might pick up a usefull skill or two. As for you 'embarrassed to be a linux user ' point of view: go buy a book or two. Learn something and come back with a little more knowledge about people and operating systems. You do a lot of talking and complaining, but there's little constructive that comes out of your mouth. 

If you really believe the point of my post was that 'you can't expect free software to work' you might need to take more than one English course actually. My point was and is that you can't get the level of support on a free operating system that you get on an os like Mac or Windows. Unless you pay for professional support you have to have a little patience from time to time. And like I said, if small inconveniences like this drive you up the roof, you might need to consider heading back to Windows or get some professional (paid) support. In fact, if you know so little about this operating system  (and you depend on it this badly) those might be your best options. Complaining gets you nowhere.

You sure as hell can't start shouting 'I want this fixed, because I use this software and it was not my fault it was broken. And i want it fixed NOW.' Make a donation, or contribute to the community otherwise to improve things. Nobody likes errors. But unlike you, most people would gladly participate in making sure that error won't happen again. You Sir, take something thats beautiful free and start demanding the community to obeys your direct needs. In the warez scene, they would simply call you a leecher. They would be right.

you couldn't be further wrong
There's a big difference between support, and things not breaking.
i don't need support for linux, i just don't think AUTO-updates should break stuff.
I don't ever need support in windows or MAC because these things don't happen

---

### Post by rafciu123 on 2007-02-12
> **russell.h said:**
> The most straightforward (although not necessarily the easiest) is:

1. Boot the new kernel, select no when you get to the error messages, and get to the command line (you may have to press Control + Alt + F1 to do this, but I don't think so). Once you are at the command line log in as you (type your name at the prompt, then your password when it asks).

2. Now put in the following commands:
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu6_all.deb
```
```
sudo dpkg -i envy_0.8.1-0ubuntu6_all.deb
```
<here it will ask for your password, so type that in>
```
envy
```
Now it will probably ask for your password again. Type that in and it will take you to a list of options. You want option 1, so just type in the number 1 and press enter.

Envy will now download and install (building a new kernel module if my understanding is correct) the latest nvidia driver. It will ask you a few questions, most notably whether you want it to automatically reconfigure xorg.conf. You probably want to answer no to this, since allowing it to do this will break Beryl or Compiz if they are running, and unless you have broken xorg.conf since it was last working it should still work.

It will ask you if you want to restart the X server, hit yes. Your GUI should boot up now.

Hi,

I get the following error when I run envy after it downloads driver from nvidia:
"You do not appear to have header files installed in your system. Please install your distribution's header libc development package."

Now X stopped working also for kernel 10.

Can you please advice?

---

### Post by hikaricore on 2007-02-12
> **syxbit said:**
> you couldn't be further wrong

Reading this line of text, hurts my brain.

That is all.

---

### Post by syxbit on 2007-02-12
> **hikaricore said:**
> Reading this line of text, hurts my brain.

That is all.

what hurts about it?

he's saying i should use windows if i want support.
but like i said, i don't need support. I just think things shouldn't break.
at the very least, there should be some warning of breakage
this is the 3rd time it's happened to me now...

---

### Post by rafciu123 on 2007-02-12
> **syxbit said:**
> what hurts about it?

he's saying i should use windows if i want support.
but like i said, i don't need support. I just think things shouldn't break.
at the very least, there should be some warning of breakage
this is the 3rd time it's happened to me now...

Does it mean that I will have to go through driver installation every time my system gets updated?

---

### Post by PartisanEntity on 2007-02-12
Hello everyone,

I would like to join the club, I am on Dapper but experiencing the exact same problem, ever since the kernel update I just can't get the 9746 driver from nvidia to work, I too get these API mismatch errors as well as messages in the log files that certain modules cannot be found.

It is driving me nuts because I have three issues when using the 8776 drivers:

1) Google Earth is unusable due to a rendering error.
2) My laptop screen turns off completely when I shut down X server so I cannot see what I am typing or doing outside of X server.
3) Also the laptop screen will not power on again after suspension.

I have tried the Envy script as well as the repo method, both from alberto milone's website but the errors remain.

Also, when I try to install xserver-xorg-dev I get a message that some dependencies will not be installed. (And I am assuming this package is needed for the driver compiling, and I am assuming further that the failure to have this package prevents the nvidia installer from being able to either compile properly or find the location of the modules (it keeps mentioning having had to guess the location of the modules during the installation)).

Im wondering whether the 9746 drivers will ever be taken up into the ubuntu repo?

Or, how come the 8776 drivers were included in the repo but not the 9746 drivers?

---

### Post by WinterWeaver on 2007-02-12
I agree with Shakabab. Yes, I've had a couple of disappointing updates, but I always get it fixed within the hour. If you are really upset about this, why not just disable your auto-update once your system is running nicely.
Thats the beauty of this OS, you have a choice.

Anyway, thanks for the replies on Envy. I decided to give it another go, and must say that it's improved a lot since the last one, which makes me happy.
To get xorg ready for aiglx etc. I ran this code:
```
sudo nvidia-xconfig --add-argb-glx-visuals
```

Beryl didn't work ok though. The window decorations was dead and Cairo-Clock & Kiba-dock had funy black and white blocks.
To get beryl working properly, I had to do the following.
First I removed it completely with the Package Manager. I just searched for Beryl, and removed absolutely everything Beryl-related.
next I installed Beryl again from this(I already had the repos and key added):
```
sudo apt-get install beryl emerald-themes
```

So, I'm happy, everything is working perfectly again :)
Thanks Everyone!

WW

---

### Post by WinterWeaver on 2007-02-12
It makes me happy that they might put Envy in the next release :)
envy was super easy to install, and I'll be using that from now on. I'm happy that it's been updated properly. So next time there is a kernel update, I'll just run envy again ^_^

just to be sure... kernel updates like this, typically only happens... how many times?? every 3 months? more/less ?

---

### Post by rafciu123 on 2007-02-12
>>just to be sure... kernel updates like this, typically only happens... how many times?? >>every 3 months? more/less ?

Why did it happen me third day I use linux? :lolflag:

---

### Post by WinterWeaver on 2007-02-12
rofl!

hehe it happens. but once you know what's up, its fast and easy to fix ^_^
can be annoying sometimes, but when I see that there is updates, I always have a quick look at what is being updated, before I run the update. This way I have a better Idea of what might change, and if something does go wrong, then I know where to start.

The Forums are also a great help =D

---

### Post by syxbit on 2007-02-12
i'd understand if this happened on feisty, but on edgy, and the "uber" reliable dapper too?

---

### Post by WinterWeaver on 2007-02-12
you seem to forget the whole thing behind the open supported driver and the third party drivers.

Use the standard Nvidia drivers in Edgy and Dapper, and you wont have this problem. (of course then we don't have all the pretty XGL etc.)

Use the Proprietary drivers and you will.

Hence the Choice you are given.... use 'em or dont.

Rather than try shoot everyone with the problem, why dont you use that energy and pour that into a project, or fund, or something that can actually help the Ubuntu (and Linux) community benefit from it, and hopefully, this type of thing can be avoided in the future.

I do understand your feelings. I also had a slight twitch when I updated and my X was broken, again, but we must focus on solving these problems, rather than flare about it.

---

### Post by rafciu123 on 2007-02-12
Are there any drivers for nvidia which are built in Ubuntu which I can use? After I installed Ubuntu it didn't look good because redrawing of objects /like scrolling web page/ took about 1s. Was I using some generic VGA drivers instead of nvidia or these were those built in nvidia drivers? What are advantages of using those not built in drivers?

---

### Post by Shakabab on 2007-02-13
> **rafciu123 said:**
> Are there any drivers for nvidia which are built in Ubuntu which I can use? After I installed Ubuntu it didn't look good because redrawing of objects /like scrolling web page/ took about 1s. Was I using some generic VGA drivers instead of nvidia or these were those built in nvidia drivers? What are advantages of using those not built in drivers?

Yeah, take a look here. Installing this should give you more performance then you have had so far. [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by russell.h on 2007-02-13
> **rafciu123 said:**
> Hi,

I get the following error when I run envy after it downloads driver from nvidia:
"You do not appear to have header files installed in your system. Please install your distribution's header libc development package."

Now X stopped working also for kernel 10.

Can you please advice?
I'm not sure, you might try
```
sudo apt-get install linux-headers-generic
```
If that doesn't work try searching around the forums some (I would do it myself, but its going on 1 AM here).

Good Luck

---

### Post by Draconist on 2007-02-13
People, all of you using lupino's repo need to do just one simple thing; forget about 'envy' or 'headers' or anything else, just this:

install...

"linux-restricted-modules-2.6.17-11-generic"

and thatz it! :)

It worked with me & to some other people, the simpliest way possible!

Cheers all...

---

### Post by rafciu123 on 2007-02-13
Russel, thanks for advice but I'm afraid it didn't work. I even tried downloading package which matches my kernel from the internet using wget and installing it but envy still complaints about missing "libc development package" as I reported in post #64:-(

Unfortunately I couldn't find solution on the web so any help will be appreciated.

Do you think I should start another thread with this problem?

---

### Post by cookfromfrozen on 2007-02-13
> **neighborlee said:**
> I guess  each individual must reconsider their options.

These kinds of problems seem to be happening all the time with Ubuntu.  Q&A on updates seems to be nonexistent.  Before you all start flaming me, think about it.  We're pretty much all using the same kernel and either the fglrx ATI driver or the nvidia-glx driver.  It isn't as if there are a 100 different kernels in use with Edgy today and about 20 different graphics drivers.

I don't see people having these kind of breakages on other distros nearly as much as I see them with Ubuntu.

I love Ubuntu, but everytime something on my system breaks because I click that orange icon, I'm being pushed that little bit further towards another distro.

---

### Post by rafciu123 on 2007-02-13
How do I make sure that next time my system gets updated I don't loose wireless card or X? Is there some setting that forces checking all the packages that need to be updated with the kernel?
Just after I installed ubuntu couple of days ago, I updated the system and I lost wireless also.

---

### Post by cookfromfrozen on 2007-02-14
> **rafciu123 said:**
>  I updated the system and I lost wireless also.
When that happens, it's usually because the linux-restricted-modules package that corresponds to the kernel was not installed with the kernel update, and wireless ends up breaking.

Type **uname -r** in a terminal to find out what kernel version you're running, then go into the package manager and see if you can find a linux-restricted-modules package that matches that version; the latest update installs a new kernel and the corresponding modules package is **linux-restricted-modules-2.6.17-11-generic**

Hope this helps.

---

### Post by rafciu123 on 2007-02-14
> **cookfromfrozen said:**
> When that happens, it's usually because the linux-restricted-modules package that corresponds to the kernel was not installed with the kernel update, and wireless ends up breaking.

Type **uname -r** in a terminal to find out what kernel version you're running, then go into the package manager and see if you can find a linux-restricted-modules package that matches that version; the latest update installs a new kernel and the corresponding modules package is **linux-restricted-modules-2.6.17-11-generic**

Hope this helps.

Yes, it was the case.

---

### Post by nomadk26 on 2007-02-23
> **rafciu123 said:**
> Hi,

I get the following error when I run envy after it downloads driver from nvidia:
"You do not appear to have header files installed in your system. Please install your distribution's header libc development package."

Now X stopped working also for kernel 10.

Can you please advice?

I had to do the following:
start synaptic find libc6, and libc6-dev highlight each one, go to the top click on Package goto Force Version to 2.4-1ubuntu12.3. click apply. wait for update. then open terminal and type in envy, hit enter.

---

### Post by noah_parkcity on 2007-03-28
Thank you [SIZE="5"]Sdyson[/SIZE].

Without people like you, us n00bs would be lost!!! [SIZE="5"]All fixed with one copy and paste?
[/SIZE]
Amazing....

My Nvidia Video Driver Failed After A Simple Update (WTF? Over)

I read the explanation of why Binary drivers are not a mix with OSS, but I suggest that we graciously ask the gurus out there to at least design a BACKUP system to be able to produce a USABLE resolution. Note, I never suggested anything nearing perfection, just usable. The reason why we desperately need this is because joe-sixpack and my dad are not curious and willing to read ubuntu forums and google to fix computer problems, they are busy doing OTHER things. They simply need their apps to WORK, period. I truly thought Ubuntu was ready for desktop prime-time, even amongst the computer-challenged people out there.  However, after having my gorgeous desktop turn into crap after downloading a simple update and then rebooting coupled with the  webcam that I finally got working after a weekend of reading and trial and error. Not everybody likes this kind of challenge boys and girls! Especially my old dad. Guess I'll have to do the remote thing to fix his and my bro's pc. This does, however, seriously limit how many people a n00b can support through this eventual migration.

If the Nvidia Video Driver fails to load or work, giving you a low resolution desktop where your icons on your desktop look HUGE then use his code.

At the Terminal Command Prompt type:

sudo apt-get install --reinstall linux-restricted-modules-`uname -r` nvidia-glx

If you're running this from the previous kernel then you'll need to replace `uname-r` with the actual kernel version (in my case 2.6.17-11-generic)

Worked like a charm. Cheers.

---

### Post by RgnKjnVA on 2008-02-14
here it is a year later and I have the same issue. One question though...How do you get to the command line to install/run envy?  When my X fails to start my machine appears to hang after the audio driver initialization (timidity/alsa). It never finishes booting up so how will I be able to try the fixes in this thread?

---

### Post by sdyson on 2008-02-14
You should have a safe mode option on the grub menu.

---

### Post by RgnKjnVA on 2008-02-14
so how does one get into this grub menu? I follow the prompt and press Esc yet no menu comes up and my machine starts up...or fails to start up in this case as usual. I've tried pressing it multiple times and holding it but it simply doesn't present a menu.

---

### Post by UK-Wobbie on 2008-02-14
I say envy to fix nvidia problems.

---

### Post by RgnKjnVA on 2008-02-14
For the record, I was having trouble with the Esc key because I'm using a KVM switch between my XP and Linux machines. Connecting the keyboard directly to the Linux machine registered the key punch and I was able to get it squared away. I'm not sure I understand why the KVM was an issue.

I've also installed Envy for what that's worth

---

