---
title: "[SOLVED] Citrix Client Printing Problem"
date: 2007-05-25
forum: General Help
---

### Post by dranockcir on 2007-05-25
Hi Everyone,

I have been using Fiesty for a couple of weeks now exclusivly at home (dual boot XP, hardly ever booting to XP) and on a second machine at work. I would love to convince my company to use Fiesty in locations where we could. Some things we do require Windows and I wouldn't even reccommend using emulation or VM's in those circumstances where we have to have Windows. But I could see us using Fiesty on a lot of desktops if I could get the Citrix Client (the latest, 10.0) to print. We use a custom app written using Fox Pro that we publish on Citrix Presentation Server. I have tried modifying the .ini files like the Admin manual says to do but I cannot get the thing to print. The local client printer (an HP Laserjet by the way) doesn't get autocreated on the server and I need this to print before I can even attempt to show the bosses that we could use Fiesty. Actually they are impresed with Fiesty, so far I haven't let on that I can't get our published app to print to the local client.

Does anyone have any experience with this issue or any suggestions? 

Thank you 

Rick

---

### Post by stefan.hattrell on 2007-10-15
I am having the exact same issue!! I am forced to use a different distro (Arch Linux btw which is really great but Ubuntu has better printing support). Have you found a solution to this problem? Has anybody else out there experienced this problem?

---

### Post by dranockcir on 2008-02-22
Hi,

Sorry, I never got a reply for the longest time and gave up on it. You have probably already figured out that it works fine in Gutsy though right? :-)

I did have interest stirred where I work to deploy Ubuntu on a bunch of desktop machines but couldn't get printing to work using the Citrix client. A must have where I work. Now that it is working in Gutsy, I haven't tried talking everyone into yet, I'm going to wait until Hardy. I use Gutsy every day at work and the Citrix client as well so if it works well in Hardy then I'm going to try again. 

Good luck!

Rick

---

### Post by dranockcir on 2008-04-02
Ok, well this isn't good. I had tried Fiesty and could not get printing to work with the Citrix Client for Linux  (see first post), then Gusy came out and it worked. I just tried Hardy Beta and guess what?? Back to the exact same problem I had with Fiesty! 

Does anyone else use Citrix Client? I really was hoping that the problem (whatever it was) was solved in Gutsy and would continue to work in Hardy but no joy. 

Thanks for any help!

Rick

---

### Post by DMaCATO on 2008-04-25
I can confirm that Citrix printer mapping doesn't work in Hardy. Been using it since release, and I still have not been successful with getting Citrix to map any of the printers.

Presentation Server 4.5 (Win 2003)
Ubuntu Hardy 8.04
HP Laserjet 4050T (Test Printer)

Modifying the wfclient.ini and adding:

DefaultPrinter=(cups printer name)
DefaultPrinterDriver=Citrix Universal Driver

Nada. I'm pretty new to Ubuntu, so hopefully its just my issue.

Thanks!

---

### Post by dranockcir on 2008-04-26
I have tried Hardy release and still the same problem, the local printer does not autocreate.Something changed in Hardy because it worked fine in Gutsy. I have a machine that I have been using to load Ubuntu on, fresh clean loads by the way, no upgrades, want to be able to just load from the CD and go. So,on this one test machine Fiesty did not work, Gutsy did, and now Hardy doesn't (just like Fiesty). To top it off I tried Linux Mint (nice by the way) Daryna and printing worked fine. Daryna is built from Gutsy and I suspect when Elyssa is released next month and being built from Hardy, printing won't work in it either. 

It's a shame really, a real show stopper for us. The more people that are exposed to Ubuntu (and Linux in general) at work, the more people are aware. We could have deployed this on a couple hundred desktops around the US and had that much more awareness about Linux and Ubuntu. Oh well, now MS is talking about extending the life of XP (to fight off Linux while they try to make up for Vista???) so we'll have to use that.

Rick

---

### Post by DMaCATO on 2008-04-27
Found my issue with printing. 

It appears that the default installation of CUPS in Ubuntu 8.04 doesn't create the "/etc/printcap" file. Found a technote on Citrix Support 'http://support.citrix.com/article/CTX110450' that references this issue and it is needed before anything can/will be mapped.

For anyone else who needs this, you just need to shutdown the CUPS printing system, edit the /etc/cups/cupsd.conf file and add 'Printcap /etc/printcap" to the file. Restart CUPS and you are good to go!

Happy Printing!

---

### Post by dranockcir on 2008-04-27
DMaCATO,

That worked perfectly! Thank you, you have made my weekend! 

I have spent that last year messing with this and I thought I had read every piece of Citrix documentation there was about printing with Linux clients.

Thanks again!

Rick

---

### Post by DMaCATO on 2008-04-28
Glad I could help out Rick! Good luck with the push to Ubuntu, that sounds like a fun undertaking!

Thanks,
Drew

---

### Post by existential3977 on 2008-05-23
> **DMaCATO said:**
> Found my issue with printing. 

It appears that the default installation of CUPS in Ubuntu 8.04 doesn't create the "/etc/printcap" file. Found a technote on Citrix Support 'http://support.citrix.com/article/CTX110450' that references this issue and it is needed before anything can/will be mapped.

For anyone else who needs this, you just need to shutdown the CUPS printing system, edit the /etc/cups/cupsd.conf file and add 'Printcap /etc/printcap" to the file. Restart CUPS and you are good to go!

Happy Printing!
___________________________________________________________________

Can anyone help with the above? I'm a bit of a newb to Linux and am trying to setup printing to my local, default printer from a Citrix environment. I am running Hardy 8.04 and have tried to amend the cupsd.conf file as per above instructions. The thing is, these instructions do not state where to place the extra command. Can anyone confirm where this line should go in the file? Thanks in advance!

---

### Post by dranockcir on 2008-05-23
> **existential3977 said:**
> ___________________________________________________________________

Can anyone help with the above? I'm a bit of a newb to Linux and am trying to setup printing to my local, default printer from a Citrix environment. I am running Hardy 8.04 and have tried to amend the cupsd.conf file as per above instructions. The thing is, these instructions do not state where to place the extra command. Can anyone confirm where this line should go in the file? Thanks in advance!

Hi,

I put it right at the top of the file, looks like this:

> #
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

Printcap /etc/printcap


of course there is more in this file but I just made it the first line after the comments at the beginning. 

Rick

---

### Post by existential3977 on 2008-05-27
Rick - many thanks!!

---

### Post by existential3977 on 2008-05-27
> **dranockcir said:**
> Hi,

I put it right at the top of the file, looks like this:



of course there is more in this file but I just made it the first line after the comments at the beginning. 

Rick

Hi All,

Unfortunately, still having issues....just don't get it!
OK, I have put the line in where Rick kindly suggested. I restarted cups, login to Citrix and STILL no default printer. What am I doing wrong? Any help on this would be greatly appreciated!!

Thanks.

---

### Post by dranockcir on 2008-05-28
> **existential3977 said:**
> Hi All,

Unfortunately, still having issues....just don't get it!
OK, I have put the line in where Rick kindly suggested. I restarted cups, login to Citrix and STILL no default printer. What am I doing wrong? Any help on this would be greatly appreciated!!

Thanks.

Are you using Hardy? Have you already setup a printer and made it your default? The reason I ask if you are using Hardy is that I noticed that the firewall in Gutsy would block port 931 and the printer wouldn't show up. I didn't notice that problem in Hardy however.

Edit: Oh, also, did you edit the file as root? 
Rick

---

### Post by jentschke on 2008-06-03
> **DMaCATO said:**
> Found my issue with printing. 

It appears that the default installation of CUPS in Ubuntu 8.04 doesn't create the "/etc/printcap" file. Found a technote on Citrix Support 'http://support.citrix.com/article/CTX110450' that references this issue and it is needed before anything can/will be mapped.

For anyone else who needs this, you just need to shutdown the CUPS printing system, edit the /etc/cups/cupsd.conf file and add 'Printcap /etc/printcap" to the file. Restart CUPS and you are good to go!

Happy Printing!

Excellent! It works!:KS

---

### Post by eudemus on 2008-07-24
According to the Citrix document referenced ([http://support.citrix.com/article/CTX110450](http://support.citrix.com/article/CTX110450)) this fix forces CUPS to create the printcap file in /etc rather than in its usual location (/var/run/cups/printcap, on my system).

Will this cause problems elsewhere to force this file to a different location? I understand it helps for Citrix, but will it cause difficulties for other apps/processes?

Cheers, Eudemus

---

