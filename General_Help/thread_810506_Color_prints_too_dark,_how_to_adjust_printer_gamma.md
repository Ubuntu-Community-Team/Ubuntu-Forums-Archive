---
title: "Color prints too dark, how to adjust printer gamma?"
date: 2008-05-28
forum: General Help
---

### Post by wkulecz on 2008-05-28
Hi, installed 8.04 on my wife's computer this weekend which had been running 7.04.  Clean install to a second hard drive, then copied what she needed from her old home folder to the new.  Went very smooth, she's very happy.

The built-in drivers for the Samsung CLP-300 color laser printer give much better text quality than did the Samsung drivers on 7.04.  But the test page grayscale and color gradients and image printouts are way too dark (the Samsung drivers had the same issue but had adjustment tabs, although the text quality made the printer unusable so I didn't really look into it further). 

I can't find any settings to adjust to lighten the printout.  Turning off ICM lightened the printout barely noticably so color "management" is having some effect.

How to adjust the "gamma" for the foomatic printers and CLP-300 in particular?

Do I need to find some specific Windows ICM or PPD file for this printer?

--wally.

---

### Post by wkulecz on 2008-05-29
Bump!

This the wrong place for printer issues??


I see a gamma adjustment in the properties tab for our Dell 3100 color laser here at work, but its broke again so I cant try it :(  

I'm not well versed in postscript, but it appears the PPD file controls what is displayed in the properties tab so I'll see if I can find a PPD file for my CLP-300 that supports gamma adjustments.

--wally.

---

### Post by prshah on 2008-05-29
> **wkulecz said:**
> 
I can't find any settings to adjust to lighten the printout.  Turning off ICM lightened the printout barely noticably so color "management" is having some effect.

Open [http://localhost:631](http://localhost:631) in your browser; this open the CUPS management utility. From this, find your printer, and you'll find a button "Set printer options" (You may have to scroll to the right for this). Under that you will find various settings including Brightness, Contrast, etc. Adjust that to your satisfaction.

---

### Post by wkulecz on 2008-05-29
Thanks, it was worth a try, but this only shows the same options I get in the Printer Configuration panel Printer Options tab.  Which lacks any gamma or brightness controls.

--wally.

---

### Post by chill on 2008-05-29
Same problem. Bit disappointed in CLP-300.

... and it lists "Linux" on the box. Watta shame... :)

Hope it prints images better (lighter) on next Ubuntu version.

---

### Post by prshah on 2008-05-30
> **wkulecz said:**
> Which lacks any gamma or brightness controls.

> **chill said:**
> Same problem. Bit disappointed in CLP-300

(Grasping at straws) ```
cups-calibrate
``` ?

---

### Post by wkulecz on 2008-06-03
At least with 8.04 we are reasonably happy with the color/monochrome text and graphics print quality, using 7.04 with the Samsung drivers was pathetic in all regards.

When the toner is gone from this one well be getting an HP!


It looks like cups-calibrate only works with Gutenprint or some other drivers which doesn't appear to be what the CLP-300 is using.

--wally.

---

### Post by FeliciaW on 2009-02-12
Any new insight on this situation...I got the Samsung CLP 300 two months before ditching Windows, 8.10 still produces colors way too dark.  Would it be conceivable that a repair shop could "tweek" my printer to be compatible with Ubuntu...or am I stuck? Thank You

---

### Post by wkulecz on 2009-03-24
I'm afraid like me, you are still stuck.  I got the CLP-300 after reading reports here that it "worked great with the foomatic drivers".  Obviously their definition of "works" and ours differs greatly :(

I toyed with the idea of installing it in Windows and trying to find its ICM or ICC file to rip off for Linux, but just haven't bothered, as the paper feed has not been reliable enough to bother with, so we'll be junking it when the toner runs out.  

We don't print a tremendous amount and hence have trouble with Epson inkjets clogging, but it worked nicely once it unclogged, but I got tired of wasting expensive ink cleaning.

I'm going back to HP printers, either color laser or inkjet, TBD.  At least with HP printers if it clogs you get new print heads when you replace the cartridge.

--wally.

---

### Post by Pa Blum on 2009-09-05
I am having a similar problem with a new CLP-315, but for me only ONE of the colors is too dark.  In the Ubuntu test page, red and green are pretty much okay, but blue is just plain black all the way across.  I can't find any color balancing controls anywhere.

Everything else seems to be okay, and the blues in the printer's own self-test page are superb.  Drat!

---

### Post by Darin722 on 2009-09-26
I'm running jaunty and a canon i850 printer using gutenprint + cups and I'm having a printer too dark issue too. lemon yellow was coming out as ochre, lime green looked more like olive etc.  I made a test print page in gimp and used to color controls to print a dot of cyan, one of Magenta, and one of yellow.  Cyan came out as dark blue, Magenta came out as a rather dark purple.  The total area of color I was putting on a page varied from the size of a dime, to about 1 1/2 square inches.  

I would try to adjust the saturation and intensity levels, etc. in the printer driver, then do a test print.  Most of the attempted adjustments yielded no change, and after about 20 or so prints my color cartridges were empty.  Sheesh!

I downloaded turboprint based on some advice I saw on this forum.  The colors now print more or less correctly.  Is Gutenprint broken?  
Can anyone suggest a way to fix this.  I'm not sure if the adjustments I'm trying are the wrong ones or if they simply have no effect on the canon i850.


I must say, the idea of proprietary, closed source, >>pay for license<< software being on my computer really gives me the creeps after using linux for so long.  Do I now have to admit to friends and family that open source software is of lower quality than commercial products?

Seriously though, My hat is off to all those people who've made open source products available to the masses and given us a viable alternative Micro$.  Your efforts are appreciated!

---

