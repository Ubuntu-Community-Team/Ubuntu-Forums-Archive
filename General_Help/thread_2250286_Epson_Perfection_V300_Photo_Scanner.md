---
title: "Epson Perfection V300 Photo Scanner"
date: 2014-10-27
forum: General Help
---

### Post by afrancis-ozonline on 2014-10-27
I have an Epson Perfection V300 Photo Scanner. When I open Simple Scan it says "No Scanners Detected". When I open Skanlite it says "The Sane System could not find any devices".
Is there a program that will work with my scanner? Or is there another way around this problem?

---

### Post by sammiev on 2014-10-27
Try the Epson site [here]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX") and type in v300 in the search box and select your driver.

---

### Post by Mike_Walsh on 2014-10-27
> **afrancis-ozonline said:**
> I have an Epson Perfection V300 Photo Scanner. When I open Simple Scan it says "No Scanners Detected". When I open Skanlite it says "The Sane System could not find any devices".
Is there a program that will work with my scanner? Or is there another way around this problem?

Hi, there.

I have an Epson SX218 all-in-one, but the procedure will be the same for your scanner, as you have to install printer and scanner drivers separately on these things. Despite their printers using quite a range of different drivers, just about all Epson scanners use pretty much the same driver package.

First of all, look on Epson's download site:-

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

When you enter the product name, DON'T start with 'Epson'; just enter 'Perfection V300'. Then enter 'Linux' for yr OS.

Hit the search button. After a few seconds, you'll be presented with a short list of choices. Choose the 'core package & data package'.

This will take you to another page, with an enormous list of supported products; (your scanner IS among them). Scroll to the bottom, and click on 'Accept'.

The next page will present you with a list of filter programs.....they're not called drivers in Linux. Depending on whether you've got the 32- or 64-bit version of Ubuntu, you will want EITHER the 'i386' OR 'amd64' versions of the '2.30.0-1~usb0.1.ltdl7.deb' package. (Not the .rpm package!) You will also need the 'iscan.data.....all deb' data package.

When you install them, by simply clicking on them in your 'Downloads' folder, THIS IS VERY IMPORTANT. You MUST install the 'data' package BEFORE the scanner package.....otherwise it all throws a wobbly, and just refuses to work! They will install through the Ubuntu Software Centre.

And that's it! You should find that it will work quite satisfactorily. I've had to do this a number of times over the last few months; I can nearly do it blindfolded by now.....

Let us know how you get on, please.

Regards,

Mike. ;)

---

### Post by afrancis-ozonline on 2014-10-28
Mike,
Thanks for your help, my system is 64bit. I downloaded and tried to install the packages you suggested. The "data" package installed through the Ubuntu Software Centre as you said. The scanner package that I tried however seems to want me to extract it and I do not know what to do after extracting. Sorry to be so dumb but can you offer any further advice. Very grateful for your prompt response.
Regards,
Alwyn.

---

### Post by Mike_Walsh on 2014-10-28
Hi, Alwyn.

Which of the scanner packages did you try? Without knowing precisely which one you tried, I can't advise much further! ;)

I can't say as I had any problem with installing mine. If you have a 64bit system, you should have downloaded the 'amd64' package; don't worry about this if you have an Intel system.....it's still the one you want. It's called that for historical reasons; funnily enough, it's named after the very processor that I myself use!

Let me know which one you downloaded, please. You say you HAVE extracted it....or you don't know how to?

Regards,

Mike.

---

### Post by afrancis-ozonline on 2014-10-28
Hi Mike,
The package I downloaded was "iscan_2.30.0-1-usb0.1.ltdl7-amd64.deb" I clicked on "Extract" but I don't know what should do next next.

Regards,
Alwyn.

---

### Post by sammiev on 2014-10-28
> **afrancis-ozonline said:**
> Hi Mike,
The package I downloaded was "iscan_2.30.0-1-usb0.1.ltdl7-amd64.deb" I clicked on "Extract" but I don't know what should do next next.

Regards,
Alwyn.

Hi,

You do not extract a .deb file. Select open with Software Center. It will install on its own.

---

### Post by afrancis-ozonline on 2014-10-29
I have tried opening both files with Software Center but scanner programs still do not detect my scanner. Ready to give up and just use Windoze when I want to scan something.
Thanks for all your help.

---

### Post by sammiev on 2014-10-29
You are downloading 2 files I hope. The amd64 and the all_deb file.

---

### Post by rbmorse on 2014-10-29
Having the same issue with my Photo 4490.  Worked fine in 12.4 but with 14.4/14.10 even though the Epson software is properly installed (in my case, all three packages...the 4490 requires a proprietary firmware blob), the scanner front-end software can't see the scanner itself.  Acts like some sort of permissions issue. 

LSUSB detects the scanner properly
scanimage -l    detects the epkowa interperter but fails to open with an unspecified error during I/O. 
 
THat's as far as I've gotten so far.

---

### Post by Mike_Walsh on 2014-10-30
Hmmm; very strange.

I've never yet come across an Epson package that wants you to extract it BEFORE installing. Have you tried installing it via Synaptic? You may need to install Synaptic first:-

```
sudo apt-get install synaptic
```

and enter your password (you may know this already). 

I don't use Synaptic as much as some people, but I believe that if you use the little magnifying glass ( 'Search' at the top) and then enter 'printer drivers', it should bring up your driver in the list if you scroll through it.....then right-click (to highlight; this 'marks' it for installation), then click on Apply at the top (the big green tick). As I understand it (I'm willing to be corrected on this!), if any extraction is required, Synaptic will take care of it.

Regards,

Mike.

---

### Post by rbmorse on 2014-10-30
Mike, Epson doesn't work via Synaptic. Their driver is no-cost but still proprietary and is therefore excluded from the distribution file sets.  It must be obtained from the Epson download site. 

Not sure what about the issue with the .deb file requesting extraction. Should be a double click and go.

---

### Post by Mike_Walsh on 2014-10-30
@rbmorse;

Thanks for putting me right on that! I wasn't sure; as I said, I don't use Synaptic as much as some people (I'm one of the current, modern generation of Ubuntu users, and always look for the easiest way to do things!) But I would have thought that if you'd already downloaded the required .deb file from Epson's site, then Synaptic would pick it up and incorporate it into the 'printer drivers' list.....as I understand it, it not only reads the lists from the repositories, but will also scan the system in order to see if there's anything there that will fit the bill.  Or am I wrong on that score?

It's only been 6 months so far; I've still got a LOT to learn..! :D

Regards,

Mike.

---

### Post by rbmorse on 2014-10-30
No, you've almost got it....Synaptic works like you describe _after_ a non-repository package has been installed.  

For example, I can find the Epson scanner front-end, iScan, in Synaptic, but it wasn't there until after the fact.  Unfortunately, Synaptic isn't smart enough to find packages that have been downloaded but not fully installed.

---

### Post by Mike_Walsh on 2014-10-30
Huh!

I've got a feeling I came across a blog post on this very point some weeks ago (I forget where now); it seems there IS something else that does the same job as Synaptic, but it's smart enough to look for downloaded files as well.....but I CANNOT remember what it was called now.

But of course, this isn't helping the OP...! :)

Regards,

Mike.

---

### Post by afrancis-ozonline on 2014-11-02
Just tried lsusb in Terminal and as well other results also received "Bus 001 Device 008: ID 04b8:0131 Seiko Epson Corp. GT-F720 [GT-S620/Perfection V30/V300 Photo]"
Don't know if this helps at all.
Alwyn.

---

### Post by rbmorse on 2014-11-02
Alwin, what happens if you put this in a terminal:

```
scanimage -l 
```          

the "l" is a lower case letter "L" not the numeral 1.

---

### Post by afrancis-ozonline on 2014-11-03
I receive the following: "scanimage: no SANE devices found"

---

### Post by rbmorse on 2014-11-04
Ok...the scanner is powered and connected as indicated by the lsusb output, but scainimage can't detect the scanner. It's likely the Epson backend software (the iScan and iScan-data packages) still are not loading.  Short of trying to re-install them again I'm coming up short of ideas.

---

### Post by afrancis-ozonline on 2014-11-12
BIG BREAKTHROUGH - Just tried re-installing as you suggested and now both Simple Scan and Skanlite actually work. Many thanks for your patience and continued support.
THANKS AGAIN,
Regards Alwyn.

---

### Post by Mike_Walsh on 2014-11-12
Nice one, Alwyn.

Just goes to show; computers are not as straight-forward as many people would have you believe. But that's why forums like these exist.....so we can ALL help one another out. With the number of members the Ubuntu forums have, you can almost guarantee that whatever your problem is, SOMEBODY, somewhere, has come up against exactly the same 'brick wall' (and like as not felt like banging their heads against it, too)!

Well done.

Regards,

Mike. ;)

---

