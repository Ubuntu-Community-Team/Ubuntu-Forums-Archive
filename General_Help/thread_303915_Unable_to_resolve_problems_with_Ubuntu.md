---
title: "Unable to resolve problems with Ubuntu"
date: 2006-11-21
forum: General Help
---

### Post by jrz on 2006-11-21
About 6 weeks ago a friend asked my help in purchasing his first computer. I suggested he use a Linux OS as he was primarily interested in reliability, and as a result he purchased a Compaq V3042AU notebook which came with Ubuntu 6.06 LTS installed. We had a little difficulty at first as we live a great distance from the supplier in a very remote area of S.E. Asia, and no login info was provided. Once we acquired the login name and password we were able to login and use the system. We immediately found several things that did not work well, or did not work at all. The touchpad is too sensitive and no matter what we tried we can't find any means of allowing us to adjust sensitivity to an acceptable value. The microphone, both internal and external will not record, and the wireless connection, which is very important does not work at all. The provider is unable to answer any questions, and Compaq now tells us they don't support Linux, Broadcom who is the manufacturer of the wireless chip says they only make the chip and provide no support. The Ubuntu forum has resulted in a dead end, googling for help gives numerous confusing solutions, none of which work for us, and as a final attempt I installed irc software on my computer, running WinXP, and tried several channels, including #ubuntu where we were able to communicate with a live body, but no one seemed able to provide answers to any questions we have, or in some cases we received responses such as "call 911", " Lots of luck", "no way", or after creating a worse problem, left us hanging and apparently logged out.
I don't know where else to turn at this point and all I have been asking lately is for someone to provide a list of commands that would allow us to remove all things that might have been installed going through the numerous attempts that have failed, and what commands we should use to confirm we have no files remaining that may interfere with future attempts to get the wireless card to work.
As I am not a Linux guru, I have no idea what ndiswrapper, bcm43xx-fwcutter, blacklist bcm43xx, modprobe, and such commands have installed or where and how to undo and get everything back to original. The only response to this question received so far is to do a clean install, which we find unacceptable, as I don't have to go that far even with WindowsXP, which would also make our reasoning for choosing a Linux OS appear to be flawed.
I am still feeling that there must be a source for competent support but am unaware of where to find it.
Any information of where to seek out help, other than try this and try that, would be greatly appreciated.
Thank you, and we have not given up on Ubuntu yet.

---

### Post by Jussi Kukkonen on 2006-11-21
> 
I don't know where else to turn at this point and all I have been asking lately is for someone to provide a list of commands that would allow us to remove all things that might have been installed going through the numerous attempts that have failed, and what commands we should use to confirm we have no files remaining that may interfere with future attempts to get the wireless card to work.
As I am not a Linux guru, I have no idea what ndiswrapper, bcm43xx-fwcutter, blacklist bcm43xx, modprobe, and such commands have installed or where and how to undo and get everything back to original. The only response to this question received so far is to do a clean install, which we find unacceptable, as I don't have to go that far even with WindowsXP, which would also make our reasoning for choosing a Linux OS appear to be flawed.
Ubuntu, just like Windows, is able to go back to a clean configuration if you have defined one before installing stuff (via backing up, ghosting the drive, etc.). If you have not done that, Ubuntu (or Windows) cannot guess which configuration you want.

If you have only installed stuff through the package manager, then you probably will be able to salvage things. If you've installed stuff 'by hand', you must remove it by hand (unless you have a backup), that should be pretty logical.

I'm sorry you've had problems, but the OS cannot guess what you want...

EDIT: you probably know this already, but you should complain to the seller: they are responsible for the product they sold you (Compaq and Broadcom unfortunately never promised you linux-compatibility). If you feel they sold you a Ubuntu-laptop with non-linux-compatible parts, at least name the shop so other people will be warned.

---

### Post by jrz on 2006-11-21
Thanks for a response, but what I have been asking is how to be sure I have removed everything associated with previous attempts to install software for the wireless card, and nothing else as we have installed numerous other things that work properly and don't want to remove things that work properly. Following How-To's from this Forum we have tried to install about 5 or 6 different wireless drivers, blacklisted bcm43xx, and I'm not sure if we have created entries elsewhere from the commands executed, but would just like to know what commands to use to remove everything associated with the wireless how-to's and what commands to use to show everything is clean prior to trying to install new drivers each time. It appears that some hardware is trial and error until you get lucky and find the software that works with a particular machine.

At the same time it would be nice to have some point of contact with persons who can confidently answer questions. I have received help several times and in one case when things went from bad to worse the helper disappeared, and no further help came to the rescue, so now we are just trying to get to a point where we can begin from scratch installing wireless drivers.

As I am not familiar with .inf files, I am suspicious that it may require making some changes in them in our case as we are running a 386 version of Ubuntu on an AMD 64 CPU, and possibly wrongly, I was thinking I found where it checks to see the architecture of the machine you are installing on and trying to install for a 64 bit machine rather than a 32 bit. I have tried to get this question answered also but no response. Various outputs to commands we have executed give info that leaves us wondering if the card is recognized properly. lspci, the first command we entered has a suspicious output which appears that it finds a Broadcom Corporation piece of hardware, but says Device unknown, and then displays the 4311 chip. No one has been able to assure us this is OK or not. At one point we ran a command that displayed HW installed and SW installed, I believe was the output, but I haven't got the system right now to confirm that, but the wireless did not work or appear in any other command outputs. Additional help acquired removed that and now we no longer receive a message that the HW is present or found and the bcmwl5.sys output shows it as incompatable or something like that.

So in the end if someone can provide a good list of commands that  are necessary to use in removing, verifying, and installing the wireless, I will be perfectly happy to try it alone.

The machine with problems is not my own so I only get to look at it and try things for a short period of time each day when it is not being used.

---

### Post by Jussi Kukkonen on 2006-11-21
> Thanks for a response, but what I have been asking is how to be sure I have removed everything associated with previous attempts to install software for the wireless card, and nothing else as we have installed numerous other things that work properly and don't want to remove things that work properly.

Like I said, if you installed/modified something by hand (as in, without using dpkg/apt/synaptic), you must also remove the modifications by hand... There is not an expert on this planet that could just guess what kind of modifications you have done -- unless of course you have the full command history you used, in that case someone might be able to help you.

---

### Post by fragos on 2006-11-21
If all else fails do a clean install.  Broadcom has more than one chip and I don't know if that makes a difference.  I setup an Acer Aspire for a frient which had a broadcon chip.  I used the chip number to Google for help.  There was some specific stuff available and I was directed to use ndiswrapper which worked well.  I also used wifi-radar to manage connections.

---

