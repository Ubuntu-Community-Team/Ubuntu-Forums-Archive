---
title: "HP PSC 1410 Printer Problems[Resolved]"
date: 2007-01-28
forum: General Help
---

### Post by Goober on 2007-01-28
Hello Ubuntans!

Well, I have got everything working successfully on my new install of Edgy except for the printer.  I have a HP PSC 1410, (cheap printer, I don't reccomend it), and I am having some issues with it.  When I installed Edgy, it was recognized, and it took 2 seconds using the Admin -> Printer to get it all installed - or so I thought.

The printer is installed, and prints just fine, the only problem is that it refuses to print in greyscale, the black ink cartridge, which I am 99% certain is full, doesn't work. When it prints, it prints in colour, usually red. So my question is how do I get it the black cartridge working?  I have tried to read about CUPS, and PPD and such, and gotten terribly confused.  I was wondering if anybody could give me a hand with this?  

Thanks in advance.

---

### Post by fragos on 2007-01-28
I have the same one and have noticed that the black cartrige isn't used unless you configure Printout Mode to Greyscale.  This can be  done in System-> Administration-> Printing or perhaps with the applications you're printing from.  Applications treat printer setup differently from each other.  Once set to Greyscale, it stays that way until changed to Color.

---

### Post by Goober on 2007-01-28
> **fragos said:**
> I have the same one and have noticed that the black cartrige isn't used unless you configure Printout Mode to Greyscale.  This can be  done in System-> Administration-> Printing or perhaps with the applications you're printing from.  Applications treat printer setup differently from each other.  Once set to Greyscale, it stays that way until changed to Color.

Well ... that is interesting ... I had done exactly what you mentioned, in fact, I did that when I first went through the Wizard.  I've not used this printer in Colour for ... well, probably a year, just because of how expensive it is, and me and my folks are too cheap to buy a new one.  I had set the "Printout Mode" to Grayscale, but not the "Resolution, Print Type" etc right about it.  I just changed that to "300 dpi, Grayscale, Black Cart.", and it worked!!!

So ... ya, problem solved.  Thanks!!!

---

### Post by Buck2348 on 2007-01-28
[http://ubuntuforums.org/showthread.php?p=2024363](http://ubuntuforums.org/showthread.php?p=2024363)
[http://www.ubuntuforums.org/archive/index.php/t-322088.html](http://www.ubuntuforums.org/archive/index.php/t-322088.html)

The threads I found with google seem mostly to talk about trying different drivers.

Buck

---

### Post by Goober on 2007-01-28
Hi Buck, 

Ya, the Driver wasn't the problem, apparently I just needed to set up the printer to print off only my Black Cartridge, which is what I did.  Linux automatically installed the driver, which is highly impressive for a free program.

---

### Post by Buck2348 on 2007-01-28
Glad it's working.  I may be resurrecting an old HP psc soon--this thread might help.

Buck

---

### Post by Nightknight83 on 2007-02-11
Talking about Issues with the PSC 1410 I have some Questions:

1.- The "Check Cartridge" dot wont's stop blinking, even when I just replaced them (And they do Work) Any thoughts?
2.- How do I set up - tune up- the printer? Align Cartridges and Stuff.
3.- Is it me, or the buttons on the printer are useless on Linux? 
4.- Why in the friggin hell HP does not release official Linux Drivers?!?! 

Thanks! :-)

---

### Post by fragos on 2007-02-12
1.  I haven't seen this.
2. When you install new cartriges a page is printed.  This sheet gets scanned and then the printer is setup for the new cartriges.
3. The buttons may be intended for off line use like copy which works fine.  I always initiate scans from Linux.  I don't think that the scan button initiates anything in Linus.
4. HPLIP ships with most Linux distros and the latest version is always available on hp.com.  HP supports the driver and provides excellent instructions.  I don't understand what more they can do.

---

### Post by Nightknight83 on 2007-02-12
I know the process on Windows is just to print the test page, then Scan it with the printer using the "Scan" button, but that button is useless in Linux (Well, for me it is)
I have to scan using "Xsane", That works too? (Forgive me please, I am new at ubuntu)

I scan using Xsane, The buttons on the printer, for me (On linux) are useless (Dunno how to fix this)
About HP, I went to the page ([www.HP.com](www.HP.com)) and there are not Linux Drivers for this printer. :-(

---

### Post by Tumpster on 2007-05-07
If I can tip everyone, go to you're local walgreens, if they do this, check online first. They refill cartridges now. I have a PSC 1410 and to refil both my color and black cartridge's is like $15 w/ tax. Thats cheap when compared to a brand new cartridge!! :) Sweetness!!

---

### Post by fragos on 2007-05-07
Check out the HP toolbox GUI Administration that comes with Ubuntu 7.04.  I never had luck getting it to work in prior releases but it does now supporting my PSC 1410 and A510.  It has a supplies tab that tells you how much ink is left in eack cartrige.  The first time I used it I'd already set up my 1410 but needed to let the toolbox go out and look for printers for it to register.  When I added the A510 with Gnome printer admin it was automatically discovered by the HP toolbox.  Toolbox also interacts with the scanner on the PSC 1410.  HP toolbox is very handy if you haven't tried it yet.

---

### Post by ramjet_1953 on 2007-05-08
As a side issue, I have noticed that Feisty installs the HPLIP package by default, but doesn't install python-qt3 which is needed to run hp-toolbox.

Regards,
Roger :cool:

---

### Post by Sef on 2007-05-08
> As a side issue, I have noticed that Feisty installs the HPLIP package by default, but doesn't install python-qt3 which is needed to run hp-toolbox.


True.  However, a message popped up telling me I needed to install it via Synaptic or the Terminal.   It was nice that the message popped up, so I knew what to do.

I have a PSC 1610.

---

