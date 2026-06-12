---
title: "Getting a Canon MG2920 to work wirelessly."
date: 2014-12-26
forum: General Help
---

### Post by Apprentice Rand on 2014-12-26
Installing a MG2920 wirelessly.  Any ideas how to make system find the printer?

Oh, and when *scangearmp2* is run...what is the output in terminal?

Thanks.

---

### Post by pdc on 2014-12-27
Hi Apprentice Rand

so to be wireless, 

1) the printer needs to be able to talk to your router; that is the route; 

here is a guide on how to do this [http://ugp01.c-ij.com/ij/webmanual/Tutorial/MG2900%20series/EN/TRL/top.html](http://ugp01.c-ij.com/ij/webmanual/Tutorial/MG2900%20series/EN/TRL/top.html)

have a read through; see how it goes; 

come back to the forum when you have either got that section completed: or you are stuck .................

________________

2) once stage 1) is done, we can tell you how to install the canon drivers

---

### Post by Bucky Ball on 2014-12-27
*Post moved to own thread. *

While your issue is similar, it is not the same. Different configuration and different printer. Please do not hijack threads. Post a new thread with a descriptive title and outline your issue. There is plenty of space here. Just gets confusing trying to fix two different issues on the same thread (and unfair to the original poster). 

Good luck. ;)

---

### Post by Apprentice Rand on 2014-12-27
How do I get the computer to talk to the printer?  I have been trying to figure out CUPS.

I'm going to have get it recognized hard connected (USB cable) first, aren't I?

---

### Post by pdc on 2014-12-28
the computer "talks" to the printer using the printer drivers; and it is set up in what is called *lpadmin* that ...................when you use a named printer,     ...................then the system knows which driver to use to "talk" to the printer;

__________________________

if opting for a wireless connection, then the printer needs to be recognised by the router; the instructions were in the previous link

_________________________

if you are happy to use a usb cable, then if I list the instructions below:

go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100626502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100626502.html) and click the big "DOWNLOAD NOW" button and select the SAVE option as the download starts please; by default, downloaded files are saved to the [COLOR="#0000FF"]Downloads[/COLOR] directory (unless you have changed it ...........)

If you open a terminal; (press the control and alt and t keys down together) and then if you copy the commands that are listed below; line by line; and PASTE them into the terminal: if you use your mouse, and the top line of the terminal; ie file along to edit and down to paste .. and hit the enter key after each paste ............)

```
cd Downloads
```

```
tar -zxvf cnijfilter2-5.00-1-deb.tar.gz
```

```
cd cnijfilter2-5.00-1-deb
```

```
./install.sh
```

the last command runs the install script; it will ask you for your sudo password, so if you have that ready;

____________________

Canon offer [COLOR="#0000FF"]ScanGearMP[/COLOR] to run the scanner and I can offer instructions for that if you need those

---

### Post by Apprentice Rand on 2014-12-28
There is supposed to be a way for the computer to talk directly to the printer without going through an outside router.  I already verified that the printer is recognized using a USB cable (sent test page).  Unfortunately, 16-foot USB cable is currrently a garrotting hazard.
The 2920 is supposed (if I understand the manual correctly) to link to computer, tablet, smartphone, etc.  [I understand that there are several points of potential failure involved here, just trying to make sure  *my* Linux skill (or lack, thereof) is the least llikely.]
Are there terminal commands I need to explore to verify my computer's wireless is working (probably does, since you are reading this), it can look for wireless signals, etc.?  Especially as it relates to installing  printes, scanners, etc.

Btw, pdc, thanks for the code. It is nice to know that I found the right commands.  I appreciate it. I feel a little less bereft of hope.  I need it coming home to command line after all these years.

---

### Post by pdc on 2014-12-29
> There is supposed to be a way for the computer to talk directly to the printer without going through an outside router.   .................ok.................. are you asking us to research this for you and give you the answer? 

this link [http://support-asia.canon-asia.com/contents/ASIA/EN/0301574601.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0301574601.html) will allow you to download the pdf file that is quite extensive in its explanations; 

_______________________________

> Are there terminal commands I need to explore to verify my computer's wireless is working (probably does, since you are reading this), it can look for wireless signals, etc.? Especially as it relates to installing printes, scanners, etc.

_______________________________

can I say again that .....................................I understand that you need to have the printer recognised by the router; .........................I think Canon are siding with me on this one ............ please see attached thumbnail ..............

I gave you the link for how to do this in post #2; .............please tell us if you have read that; ........................................and please tell us if you have done any of that; .......................................................................

_______________________________

if you read the Canon pdf (line 2 above) that they provide you when the click the top link; you can access without the router but it is a one-only step; 

_______________________________

which city are you in? I ask that because many, many cities have LUG (linux users groups) and such groups have enthusiasts who I am sure are willing to help those in need of help

---

### Post by lizardboy862 on 2014-12-30
PDC can you tell me how to make the scanner work? I followed your instructions for working with usb and it worked flawlessly. Thank you I just need help configuring for [COLOR=#0000FF]ScanGearMP.[/COLOR]

---

### Post by Apprentice Rand on 2014-12-30
Lizardboy862:

Have you gotten the unit to be wireless-ly recognized by the computer?

---

### Post by Apprentice Rand on 2014-12-30
pdc:

I know the printer should be able to talk to the computer.  I worry my issue is that I'm missing how to get my computer to find the printer.  I go back to my application's screen (CUPS) and stall.  I'll keep searching basic wireless issues, too.

---

### Post by Bucky Ball on 2014-12-30
@lizardboy862: Please post a new thread with a descriptive title regarding your support request. It doesn't belong here. Gets confusing working on two unrelated issues on the same thread and is unfair to the original poster. You'll often be ignored because of this. Thanks.

Good luck. ;)

---

### Post by lizardboy862 on 2014-12-30
I did get my computer to see the printer wirelessly. My only suggestion is try to setup through a tablet or smartphone to at least get that side setup and registered. Use youtube becuase canons directions are not that great in my opinion. Then I would first install it by usb first on a computer you will leave on. Then you would take another wirless computer and see if you can set it up through there and see if it gets recongized by the computer. I am using mint on my laptop and ubuntu on my desktop so I cannot really walk you through. But it somehow just set it up on my computer.

---

### Post by Apprentice Rand on 2014-12-31
Update: Had to resort to connecting through the router using CUPS.  It took several tries to get the handshake to work.  Garroting issue solved.
It's acceptable-for now.

Still feeling very "dog with a bone," about direct-connecting from my Linux box. It won't grow up to be a server (print, or otherwise) if it has to keep going upstream to connect to downstream things.

 Life is learning, right?

---

### Post by Apprentice Rand on 2014-12-31
MG2920 is an MFP, so it might be a bit disconcerting to chase the related functions if they might be having related (or worse, unrelated) problems.  Kind of a "6 of...half dozen of..." thing.  I don't know how it would work best.  But, I'll keep track of lizardboy862's post, just in case Bucky needs to move it.

In any case, this is definitely going to be my go-to site for a good long while.

---

### Post by Bucky Ball on 2014-12-31
lizardboy's fine and thanks for the input LB. Their first post was about getting scanning to work, not related to this, which is why I suggested they post a new thread regarding that. 

If the ball is rolling on this support request, all good. ;)

---

### Post by pdc on 2015-01-01
so AR: you say > I worry my issue is that I'm missing how to get my computer to find the printer.

..................... yes................important step.........................first step is install printer drivers; so when the time comes the computer can talk to the printer..............and second step is tell the computer which printer you want the instructions to be sent to: 

..............how to do that? 

1) CUPS 

2) ```
system-config-printer
``` in a terminal opens a click-box and you click on "ADD  A NEW PRINTER"  and off you go getting things set up 

3) PRINTERS from the admin in the Menu

_____________________________________________

did you ever read the link I gave you on how to connect the printer to the router? The thumbnail gave you the picture of what you do:

---

### Post by Apprentice Rand on 2015-01-04
> **pdc said:**
> so AR: you say 

..................... yes................important step.........................first step is install printer drivers; so when the time comes the computer can talk to the printer..............and second step is tell the computer which printer you want the instructions to be sent to: 

..............how to do that? 

1) CUPS 

2) ```
system-config-printer
``` in a terminal opens a click-box and you click on "ADD  A NEW PRINTER"  and off you go getting things set up 

3) PRINTERS from the admin in the Menu


Done, done, and done.  Using my cable provider's wireless router, that is.
_____________________________________________

> did you ever read the link I gave you on how to connect the printer to the router? The thumbnail gave you the picture of what you do:

Sorry, I already had that page, just couldn't get the direct link (computer-printer) to work wirelessly.  I must be having a "senior" issue with that procedure.  I'll try again when I have my windows laptop rebuilt and can use the included windows-only disk.

By the way, I am checking out local LUGs and trying to get in to a local college's LINUX class (my last LINUX class was 13 years ago).

---

