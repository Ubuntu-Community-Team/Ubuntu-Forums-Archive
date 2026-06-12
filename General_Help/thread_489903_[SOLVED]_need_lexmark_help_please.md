---
title: "[SOLVED] need lexmark help please"
date: 2007-07-01
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2007-07-01
Good evening all!
Today I bought a lexmark printer 1200 series. It's the all in one x1270 model. When I go to add it detects lexmark 1200 but I do not know where to go from there. The list does not show x1270 model. Please some one hopefully can assist me.
Thanks, 
Sally

---

### Post by pedrogl on 2007-07-01
Hi,
It's probably not supported. I have a dell printer, which is a Lexmark one with a different name, and I could not find any suitable driver.
I've read that lexmark printers are usually not supported in Linux. If you search [here]("http://www.cups.org/ppd.php"), your printer is not listed (CUPS is the printing system that Ubuntu uses).
But, if your printer is postscript compatible (only some -expensive- laser printers are), then maybe you can choose a Generic Postcript driver. Look on your printer's manual for that.

---

### Post by IusedTObeSOMEONEelse on 2007-07-01
Thanks for reply.
As I have said, it does see it as the 1200 series which it is but the model isn't listed.:(

---

### Post by linuxwizard on 2007-07-02
According to this it should work perfectly. As long as the system picked it up as a 1200 leave it finish setting it up and try to print.
[http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-x1270](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-x1270)

If you look at this under notes a 1200 is X1270 like printer.
[http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-1200](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-1200)

---

### Post by IusedTObeSOMEONEelse on 2007-07-02
Thank you very much for your words of encouragement :D
It is hooked through USB and was detected. I click forward and now I have box listing models for drivers but I do not know what to pick. It says "lm1100 recommended". So what do I select for model?. Then when I click forward what shall I type** exactly** for **"Description" **and  **"Location"**/ 
I am really not to bright with all this :(
Thanks

Sally

---

### Post by phidia on 2007-07-02
The description entry can be anything you choose-it's probably helpful to make it something that is descriptive like the printer model e.g lm1200. I don't think you need to put anything in location.

---

### Post by linuxwizard on 2007-07-02
It is ok just take your time. You need to learn it. Can take time but worth it in the end.
Description > type in Lexmark x1270
Location > is there a drop down menu should be USB
lm1100 recommended > is this the driver, if it is that is what you want.
if it ask about model number 1200 or x1270 
let me know how it goes be around for awhile

---

### Post by IusedTObeSOMEONEelse on 2007-07-02
Thank you, I'm really trying my best. My brother (DougieFresh4U) set this machine up and  usually helps me out but is nowhere to be seen tonite on the forum and I am very happy with any help you are giving me.
Here is what I'm getting:

---

### Post by linuxwizard on 2007-07-02
on step 2 of 3 printer driver is their z600 driver to choose from

---

### Post by IusedTObeSOMEONEelse on 2007-07-02
Do I need to download that driver as I don't see it any where

---

### Post by linuxwizard on 2007-07-02
nomally you take the recommended driver when setting the printer up i don't understand why  it is picking lm1100 when it should z600
here shows recommended driver z600
[http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-1200](http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-1200)

not sure why it is not offered and where you can get it. I know more about HP than Lexmark.

---

### Post by scottrob12 on 2007-07-03
To install this printer I used the instructions at

[http://helicell.net/blog/2007/01/03/lexmark-x1270-printer-under-kubuntu/](http://helicell.net/blog/2007/01/03/lexmark-x1270-printer-under-kubuntu/)

You have to install 2 files and then install via kde. You should find the 2 Z600 installer files in Synaptic and the kde printer menu.If you follow the instructions exacly as in the tutorial you should succeed.

Best of luck. My own thread is on 

[http://ubuntuforums.org/showthread.php?t=490133&highlight=lexmrk+1270](http://ubuntuforums.org/showthread.php?t=490133&highlight=lexmrk+1270)

---

