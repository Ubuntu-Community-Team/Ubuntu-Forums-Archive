---
title: "f-spot 4x6 borderless printing..."
date: 2008-06-10
forum: General Help
---

### Post by casagan on 2008-06-10
Hi all.

Recently there was an update for f-spot and new options appeared for border less printing. The issue I have is that I cannot get it to print to the 4x6 inches size of my photo paper. In the printing options there seems not to be a place for the paper size. I currently use the crop tool inside f-spot to get the correct aspect ratio, but as soon as I try to print, my printer (HP Photosmart c4280) tells me that the size  of paper is not correct. If I press OK on the printer, it starts to print as if the paper was A4, instead of 4x6 photo paper. I tried everything: changing options in f-spot, in CUPS control panel and in HP own linux tools control panel, with no results. I will appreciate any help. Thanks in advance.

Omar P.

---

### Post by rob martin on 2008-06-11
Can confirm this with C6180 - very annoying!

---

### Post by David Valentine on 2008-09-28
And with C7280, too.  You can use the HPLIP Toolbox to go around this issue, but you sacrifice all of the convenience of working in F-Spot.

---

### Post by nbagi on 2008-10-24
:( Also with HPC5280.I am printing with gimp

---

### Post by mgmiller on 2008-10-24
The way I got around this is by defining several different printers in the Printer configuration gui.  System > Administration > Printing.

Set up your first printer and in the Printer Options tab, tell it US letter borderless or A4 or whatever your full size sheet is.  You can also define this as plain paper in the Media Type.

Then define another printer and name it HP 4x6-photo (or whatever) and on the Printer Options tab, select 4x6 borderless and then pick the photo paper option on media type, etc.

You can define as many as you want.  I have us letter plain paper as my default printer and have also defined 8.5 x 11 photo paper and 5x7 photo and 4x6 photo.

When you are in F-spot or whatever you like to print from, when you click the print button, you will see the list.  Just select the printer you have set up from the list for the paper size you want.    I do this from Picasa and gimp and g-thumb and it really simplifies everything.

---

### Post by RodentsOfUnusualSize on 2008-11-08
> **mgmiller said:**
> The way I got around this is by defining several different printers in the Printer configuration gui.  System > Administration > Printing.

Set up your first printer and in the Printer Options tab, tell it US letter borderless or A4 or whatever your full size sheet is.  You can also define this as plain paper in the Media Type.

Then define another printer and name it HP 4x6-photo (or whatever) and on the Printer Options tab, select 4x6 borderless and then pick the photo paper option on media type, etc.

You can define as many as you want.  I have us letter plain paper as my default printer and have also defined 8.5 x 11 photo paper and 5x7 photo and 4x6 photo.

When you are in F-spot or whatever you like to print from, when you click the print button, you will see the list.  Just select the printer you have set up from the list for the paper size you want.    I do this from Picasa and gimp and g-thumb and it really simplifies everything.

Hello,

I tried this but it hasn't worked for me - I'm trying to print to 4x6 photo paper on a Epson Photo R310... If I do a test print through  printer configuration it prints a perfect 4x6 test print. Through F-Spot it prints part of an A4 sized print on the 4x6 paper.

Any other suggestions?


Thanks

---

### Post by mgmiller on 2008-11-08
I do virtually all my photo printing through picasa.  I recently tried photo printing from gthumb and eog and found I did not get the consistently reproducible results for paper size that I get in picasa.  I suspect you are having the same dificulty in f-spot.

Not a perfect solution, because you are relying on a 3rd party, non-native ap to do your printing, but try installing picasa and see what happens.

Add the following to /etc/apt/sources.list by editing the file:
```
gksu gedit /etc/apt/sources.list
``` and adding the following to the bottom of the file:
```
## Google Picasa for Linux repository
## GPG key   wget -q -O - http://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
deb http://dl.google.com/linux/deb/ stable non-free
```Then, add the GPG key by pasting the following into a terminal:
```
wget -q -O - http://dl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
```Once all this is done, picasa will be in synaptic package manager and can be installed and updated like any other app.

---

### Post by RodentsOfUnusualSize on 2008-11-09
Thanks for that - I've installed Picasa and it works a treat. Have you discovered any gotchas with Picasa? I like the look and feel of it over F-spot. Getting the colour balance right is the hassle I'm having now but I like the easy one button click to 'tune' the image.

I setup the printer to use RGB but the print colours don't seem as punchy as the prints I did using iPhoto in OSX to the same printer. Any suggestions for improving the colour balance / look of the prints?

Thanks for your help!

---

### Post by mgmiller on 2008-11-09
Glad it's working.  I happen to love using it.  

To make the colors more intense, you may have controls directly in your printer driver.  I am using turboprint for my Canon i960 and it allows me to tune each color channel independently.  

For the regular gnome printer driver, adjust it as follows:
Click on System > Administration > Printing to bring up the list of your defined printers. 
Chose one by right clicking it and select Properties.
On the left side, click on "Printer Options".
On the right side, scroll down and you may have the option to control all the color channels and ink use and other things.

I have found this most useful to tune the printer for different brands of ink that may skew a little to the cyan, for example, so I just turn that channel down a bit.

Before experimenting with the printer driver, I would probably try using picasa to tweak the image.  Over the last few years, I have found myself setting the printer driver back to it's stock settings most of the time.

So, in Picasa, once you have selected a picture for editing,  you will see 3 tabs, "Basic Fixes", "Tuning" & "Effects"

Go to the "Effects" tab and click on "Saturation".  There is a slider that will let you make the colors more intense, but you can't select sub color independantly.

In the "Tuning" tab, the bottom slider will let you adjust the Color temperature.

In the same tab, the highlights and shadows sliders can manually increase the contrast for you to give you a little more punch.

While you are in the Tuning tab, there are 2 small icons on the right side that look like magnifying glasses.  The top one does automatic lighting correction and the bottom one does automatic color correction.

Between these  tweaks, you should get pretty close to what you want.

There are lots of fun settings to play with, especially in the "Effects" tab.  The more you use it, the more useful stuff you will find.

If you really need to do something serious to the image, open it in gimp first and do the changes there, save it and then open it in picasa to finish it off.

Gimp is fairly complex, but can do a lot of neat things.  It's beyond the scope of this thread to describe them in any detail, but you can easily search the forums for help with it.

Full Circle Magazine has been running a nice series of tutorials on using gimp, as well as other interesting Ubuntu facts.
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by RodentsOfUnusualSize on 2008-11-11
I've been testing a few things - I tried the colour saturation and automatic lighting in picasa and ended up reducing the green highlights of most of the images in gimp before printing through picasa.

This has dramatically improved the look of the prints...although I can make some incremental improvements with a bit more experimentation...

I've subscribed to full circle magazine so thanks for the tip.

Cheers!

---

### Post by Raval on 2009-02-08
Same issue with HP C4480

---

