---
title: "Three simple questions (slightly lengthy)"
date: 2007-10-05
forum: General Help
---

### Post by iconicmoronic on 2007-10-05
As a new Ubuntu user I guess I have a lot of questions. 
One that is important though is root account enabling; and I know there are security advisories against the enabling of root login, but all-in-all they mean little to myself.

I read the unofficial Ubuntu guide, and there are alot of helpful hints and tricks in there for those of you who have not seen it, [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

Anyhow, ifyou look on that guide, or one of its siblings that for dapper, edgy; etc. - near to the bottom is the enabling of root login via the boot time startup scripts. By adding rw init=/bin/bash root login is enabled from boot and this is all well; however, I'm wondering how I might enable root access via the GUI because despite this entry, one can still not logon as root from the f7 terminal.

One other question I had is regarding ALSA. I'm using the dapper drake edition of Ubuntu, and have used edgyand feisty --- both of those did have proper configuration for ALSA and sound was enabled and where I'd just as soon disable the feature, being that the sound driver is integrated to the motherboard there isn't much point to it, plus I get a few annoying warning! messages about sound devices and things.

Where can I locate a file for configuring ALSA. I sort of want to do this on my own, but I don't know where the main ALSA configuration file is located.

The other issues mentioned on the forum haven't been eaxct to this and the inherant solutions sort of moved passed the question: "Where is the main ALSA configuration file?"

I'm adamant that if I know the settings for my sound driver that I should be able to configure ALSA via the [www.tldp.org](www.tldp.org) website.

One last thing, is that I'm using a customized Compaq Deskpro computer. I don't know the exact model and there fails to be model numbers and the like on the computer (obviously it is second hand) -- anyhow, I have gotten on a few occasions a message at bootup telling me, "If you are running Linux you will have to configure your system. Use the Compaq User Diagnostics Diskette." I found such a diskette on the web, but where the DMA and IRQ settings are outlined in my BIOS, and according to the protocol of this system they are "hardened" into the BIOS so that this diskette is not needed, I may need to alter some of these settings if Linux is attempting to use different DMA/IRQ from that listed. 
There are options, and where I don't see this being a very large possibility (as mentioned before), I suppose Linux trying to use different settings is possible so I'm looking for another configuration file, particuarly -- one outlining the use of IRQ and DMA alotments. 

Any help on these three issues would be much appreciated, thanks!

---

### Post by bodhi.zazen on 2007-10-05
In terms of your root question, init=/bin/bash gives you access as root. To start X just type ```
startx
```

To log in as root via GDM, first set a root password, then go to System -> Administration -> Login window ...

Go to the "Security" tab, tic "Allow local system administrator login"

Boot normally (not with init=/bin/bash)

=====

Normally for root access one opens a terminal and either :

sudo su -
sudo -i
gksu

 [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by iconicmoronic on 2007-10-05
Thanks for that answer.

I have to divert attention more toward wine though, because I have to use it in order to emulate an environment for the Compaq Diagnostic Diskette program that I mentioned.

I used the command 

wine /home/user/Desktop/file,

this is the output:

root@adsl-79-431-126-11:/home/user# wine /home/user/Desktop/sp8126.exe
Warning: unprotecting memory to allow real-mode calls.
         NULL pointer accesses will no longer be caught.
fixme:int:DOSVM_Int10Handler Get Font Information - Not Supported
fixme:int:DOSVM_Int10Handler Get Font Information - Not Supported
fixme:int:DOSVM_Int10Handler Select Active Display Page (0) - Not Supported
fixme:int:DOSVM_Int10Handler Write String - Not Supported
fixme:int:DOSVM_Int10Handler Write String - Not Supported
Computer Setup/VP and PC Diagnostics
VERSION: 1.76 Rev A and 10.28 Rev A
LANGUAGE: US English

F10 Setup/VP, with Personal Computer Diagnostics, supports Compaq Deskpro
2000MMX, 4000, 6000, Deskpro EP, SB, and EN Series of personal computers.
Three (3)-1.44 MB diskettes are created by this Softpaq. Diskette one
contains Personal Computer Diagnostic programs which can test and inspect
the state of the computer and its devices.  This diskette can be used to
upgrade the Diagnostics that are preinstalled on the system partition of
the hard drive for the Deskpro 2000MMX, 4000, and 6000 Series only.
Diskettes 2 and 3 contain software which involves configuration, security
and power management.

SOFTPAQ COMMAND LINE OPTIONS:

<path>   - A <path> switch indicates the directory to unpack the softpaq
              files into. The default value of <path> is the current working
              directory. This directory must already exist.

-H or -?   - Displays additional information.


Does someone have a link to a more in depth wine tutorial? The howto @ winehq is lacking to say the least.

---

### Post by yabbadabbadont on 2007-10-05
That error message is not from WINE, but from the setup program you ran *with* WINE.  :)

Apparently, the program needs you to supply some parameters.  Try running it again with the "-?" like it suggested to see what parameters are needed.

---

### Post by iconicmoronic on 2007-10-05
I supplied wine with the -? option, it doesn't work. Wine is assuming that it is part of the filename, and telling me it cannot open the location because it was not found. I both preceded and followed the filename with -?.

that also is not an error message from the program, the program runs to make floppy disks, wine is relaying that it cannot continue because of --- ? 

I don't know.

---

### Post by JKyleOKC on 2007-10-05
Try issuing your wine command like this:
      wine "/home/user/Desktop/sp8126.exe -?"

The double-quotes will pass the command and its argument to wine as a single parameter.

If that does not work, try this way:
     wine /home/user/Desktop/sp8126.exe "-?"

This will hide the "-" character, which denotes an argument, from the initial shell parse so that instead of going to wine, it will go to the sp8125.exe program you are launching.

Personally I don't use wine; I find that installing VMWare and then installing Windows in one of its virtual machines is much more bullet proof.

The message you are getting definitely comes from the sp8126.exe program and is telling you how to use the program. It's quite possible that the version you found may be for some other model of Compaq machine, and is also possible that your machine's disk was wiped clean by the previous owner and no longer has that special Compaq partition anywhere on it. In any event, the configuration data in that partition will be for Windows, only, and ought not have any effect at all on your Linux operation...

---

### Post by der_joachim on 2007-10-06
> **iconicmoronic said:**
> One other question I had is regarding ALSA. I'm using the dapper drake edition of Ubuntu, and have used edgyand feisty --- both of those did have proper configuration for ALSA and sound was enabled and where I'd just as soon disable the feature, being that the sound driver is integrated to the motherboard there isn't much point to it, plus I get a few annoying warning! messages about sound devices and things.

Where can I locate a file for configuring ALSA. I sort of want to do this on my own, but I don't know where the main ALSA configuration file is located.

The other issues mentioned on the forum haven't been eaxct to this and the inherant solutions sort of moved passed the question: "Where is the main ALSA configuration file?"

I'm adamant that if I know the settings for my sound driver that I should be able to configure ALSA via the [www.tldp.org](www.tldp.org) website.

[The ALSA wiki]("http://alsa.opensrc.org/index.php/Main_Page") may be a valuable source of information. IIRC, the ALSA config file is /etc/asound.conf .

---

