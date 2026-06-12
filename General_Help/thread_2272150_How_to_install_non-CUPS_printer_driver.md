---
title: "How to install non-CUPS printer driver?"
date: 2015-04-04
forum: General Help
---

### Post by 2CV67 on 2015-04-04
I just replaced my good old Canon iP4300 by a new iP7250.  :(

Ubuntu rapidly "Added" this printer, with CUPS+Gutenprint driver & it works straight off!
So I should just leave it alone, right?

But I actually want to try the Canon drivers via Michael Gruz's ppa.
[https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk](https://launchpad.net/~michael-gruz/+archive/ubuntu/canon-trunk)

I did this in the past for the iP4300 but I forget how & I can't see up-to-date instructions.

So far:
I added the PPA to my repertories OK.
I installed "cnijfilter-common-64" & "cnijfilter-ip7200series-64" OK via synaptic.

I "Added" the printer again, with a new name & expected to be offered a choice of driver, but just got CUPS+Guten again.

I went to localhost:631/printers/ & looked to modify the driver, but only found a long list of CUPS+Guten's.

How do I point it at the cnijfilter drivers?

Thanks!

PS - yes, I know there are a lot of threads about problems with old Canon printers using genuine Canon drivers, but I haven't reached those problems yet!

---

### Post by pissedoffdude on 2015-04-04
Hi there,

That canon driver is meant to be used with CUPS.  The driver simply allows the printer to communicate with the CUPS server.  The PPD simply describes the features available for a specific printer.  It's most likely the case canon has not provided a specific one for your printer, or maybe they didn't include a PPD with their drivers (I couldn't find any mention of one on their website).  If there is specific functionality not described by your current PPD that you know your printer has, you can search for a PPD which contains this functionality and choose it when configuring your printer through the CUPS web interface or through Ubuntu's interface.

---

### Post by pdc on 2015-04-04
Hi there 2CV67; 

can we just check that the Canon drivers are installed please? If you can copy this command ```
dpkg -l | grep cnijfilter
``` and paste it into a terminal, and then copy the result and paste it back here please?

______________________

I often feel it is much better to go to get the Canon drivers directly ....... from a Canon site as a printer install requires three things

1) establish a connection 
2) install the drivers
3) register the printer on one's system

_________

Canon (and Brother) supply install scripts; so the install script does 2) and 3) for you; whilst you sip a nice relaxing cup of tea; ..............whereas the instructions I have seen for the ppa you cite; is that one has  to do a manual registration of the printer .........after step 2)

_________

so if I was suggesting how one would get an ip7200 series printer going, I would point to the Canon Asia website; [http://support-asia.canon-asia.com/contents/ASIA/EN/0100465502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100465502.html) and if one clicks here to download the compressed file is [COLOR="#008000"]cnijfilter-ip7200series-3.80-1-deb.tar.gz[/COLOR]

.............even though you say the device is brand-new, I see Canon issued the drivers in November 2012 and they were version 3.8 and any Canon **driver < 4.0** needs [COLOR="#0000FF"]libtiff4[/COLOR] to allow the registration............Ubuntu removed libtiff4 from its repositories last year in its relentless march forward into the future. 

so you need [COLOR="#0000FF"]libtiff4[/COLOR] and you can get it from the Debian repository [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and if you go 14 (quatorze) down the list, there is 64bit version you need..........clicking to download should wake up Ubuntu Software Center and if it offers to install it there and then; all the better

__________________

as a comment here, if one were to have used the Canon install script; the script would have stopped when it recognised libtiff4 was needed; and it would have printed that out in the terminal............so one is alerted to this issue.

_______

if the Canon drivers are installed; and libtiff4 is installed, then one should be able to register the printer directly through CUPS or with the command ```
system-config-printer
``` that opens a GUI dialogue box and it has a big ADD button in it; that should allow the system now to approve the registration of the ip7200 series printer that you have; from the reviews I read, it seems like a great printer with "superb" prints according to one reviewer

____________

for anyone coming after; who wants to install a driver for the ip7200, get it from the link above; **SAVE** it as the download option; and the four sequential commands in a terminal would be:

```
cd Downloads
```
```
tar -zxvf cnijfilter-ip7200series-3.80-1-deb.tar.gz
```
```
cd cnijfilter-ip7200series-3.80-1-deb
```
```
./install.sh
```

and that should do steps 2) and 3) automatically

---

### Post by pissedoffdude on 2015-04-04
> **pdc said:**
> Hi there 2CV67; 

can we just check that the Canon drivers are installed please? If you can copy this command ```
dpkg -l | grep cnijfilter
``` and paste it into a terminal, and then copy the result and paste it back here please?


I don't think the problem here is related to drivers.  From what he said, his hardware is perfectly capable of interacting with the O/S, so we don't have a driver issue.  What it sounds like he's asking for is a canon CUPS PPD file, which I couldn't find online, but I could be mistaken. 

That PPD file != driver. Most likely it's the case that by default, Ubuntu has an open source canon driver that's capable of interacting with CUPS. But, he can choose to use the canon one if he wants.  Choosing the canon one isn't the same as using a PPD to describe his printer's functionality.  All the drivers do is provide a way for the printer to interact with the O/S.  He's asking for a canon PPD, but I don't think they have one (again, I could be totally mistaken), and this isn't what the repo he linked provides.  All it provides is the driver so that his printer can use CUPS.

---

### Post by pdc on 2015-04-04
thanks for your feedback; I believe you have raised some very important issues there; a valuable feedback from you and we all need commitment to solve these issues. 

what I saw cv say was [SIZE=4]> But I actually want to try the Canon drivers[/SIZE]

..........and all I was suggesting was that ......................if that was the case.....................that he wanted to try the Canon driver...................................that the Canon driver for the ip720 needs libtiff4 if it is all to work ............... that's all ...............................

---

### Post by 2CV67 on 2015-04-05
> **pdc said:**
> Hi there 2CV67; 

can we just check that the Canon drivers are installed please? If you can copy this command ```
dpkg -l | grep cnijfilter
``` and paste it into a terminal, and then copy the result and paste it back here please?

```
chris@AcerTC:~$ dpkg -l | grep cnijfilter
ii  cnijfilter-common-64                                 3.90-76~ubuntu14.10.1                    amd64        IJ Printer Driver for Linux.
ii  cnijfilter-ip7200series-64                           3.90-76~ubuntu14.10.1                    amd64        IJ Printer Driver for Linux.
chris@AcerTC:~$ 
```

Thanks for your interest.

Maybe I need libtiff4?
The discussion about PPD is over my head at the moment.

Some background/explanation:
When I got my previous iP4300 (2007?) it did not work just with CUPS.
I installed drivers from Canon Australia & eventually got it working well.
Every Ubuntu update required jumping through many hoops to get it working again (see my dozens of posts... 2CV67/iP4300).
Later, I discovered the Gruz ppa & had instant success!
Later still I found Ubuntu now handled that printer reasonably with CUPS/Gutenprint.
"Reasonably" included I needed to set color to CMYK, papersize to A4, I didn't get ink-level info (until installing "ink" etc), I didn't get maintenance options like head cleaning & nozzle check etc.

With the new iP7250, I first installed it in my Windows 8 partition to show the printer itself worked OK.
Then I switched to 14.10 & "Added" the printer by simple GUI.
To my surprise & pleasure, it installed (CUPS/Gutenprint) & worked immediately.
Not even needing to shift the color settings from RGB or to correct paper size from Letter to A4 - EXCELLENT!!
I get ink level info via terminal with "ink" + "libinklevel5".

So I can live with that.

But I always like to have a safety net & I think that Canon drivers probably still provide some advantages (automatic ink level indication, maintenance options...).
So I am interested in trying that too.
I saw that Canon did offer iP7250 drivers on the Canon Europe site (good point at last!) but my previous experience had been that installation was simpler via the Gruz ppa.
In any case, I strongly prefer installing stuff via Synapt rather than ad-hoc which reminds me too much of MS!

First impressions of the iP 7250 are that it is noisier than the iP4300 & sadly lacks the upper-rear paper feed hopper, so printing A4 photo is less convenient.
Unfortunately a new print head for the iP4300 was going to cost 100&#8364; whereas a complete new iP7250 was 80&#8364;.
I could rant over that, but won't...

Thanks again for your help!

---

### Post by pdc on 2015-04-05
> Maybe I need libtiff4?

........ you absolutely need libtiff4 for any Canon pixma driver < 4.0

---

### Post by 2CV67 on 2015-04-06
Thanks again for your help!

I installed libtiff4 from Debian as you indicated, via Software Center.

I then "Added" my new printer again, from System-settings > Printers window, but was not offered a choice of driver (just "Searching for driver" or something like that, as previously, with no possibility to select anything).
Afterwards, I went to localhost:631 > Printers > NewPrinter > Administration > Modify Printer > Model.
There I could scroll down to "Canon iP7200 series Ver.3.9.0" which is the Canon driver from Gruz PPA, and use that one.

The good news is that it works OK, including getting color right & has Maintenance options "Print Test Page / Print Self-Test Page / Clean Print Heads"
The bad news is that it does not automatically show ink levels.
I can get ink levels via terminal with "ink", so it's not a disaster.

So - I will use Gutenprint as default, and Canon/Gruz just for self-test & head-cleaning...

Thanks again!

---

