---
title: "Canon Pixus iP5200r - Color problem"
date: 2007-04-26
forum: General Help
---

### Post by siaco on 2007-04-26
Hi all!

I'm a new user of Ubuntu, and I must say I have fallen in love. After using Windows all my life, I now feel home ;)

There is just one problem I cant figure out and that is the printer. I have a [Cannon pixma iP 5200r]("http://www.canon.co.uk/For_Home/Product_Finder/Printers/Bubble_Jet/PIXMA_iP5200R/") which I didnt manage to get to work under Edgy (I cant remember if I tried that hard either..) .. But when 7.04 came out and I really needed to print something so I decided to give it a try.

And it was -really- simple! I have read some places around the net that this printer, connected over a wireless connection was hard to get to work.. But I just went into the printer setup, double clicked on new printer (gnome cups add started), I chose network printer, a TCP/socet printer, entered the IP in the host field, pressed next, selected the correct driver, next one more time and then I was able to print a 100% correct test page.

**...but then, here comes my problem:**
Despite that the test page was seems 100% correct, I get some wrong colors when printing out from applications like GIMP and OpenOffice. The color red (or light red as as I used in OpenOffice) becomes yellow when I print it out. And when I in GIMP fills an image up with gradient colors (Full saturation spectrum CCW), it doesnt print out well at all. The first specter from red-orange-yellow-green prints out well, but after that the colors is no good. I will try to get a scanned image of the print so it would be easier to see how it is.

Does anyone have an idea of why the colors comes out badly, and what I can do to try to fix it?

Thans for you answer! :-)

---

### Post by siaco on 2007-04-26
Hi again, this is the result of printing:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=30931&stc=1&d=1177602554[/IMG]

Hope this helped to get a clue of what is wrong here :)

---

### Post by phidia on 2007-04-26
I always recommend [www.linuxprinting.org](www.linuxprinting.org) for printing problems because that site has a lot of resources.
Check it out. It does sound like OO.o and gimp are not integrated with your printer well. 
There is a gimp print program [http://gimp-print.sourceforge.net/](http://gimp-print.sourceforge.net/) . I don't use OO.o much so I can't help with that.

---

### Post by siaco on 2007-04-27
Thank you. I will take a look there.

If anyone have even more concrete suggestions, feel free to post them and I'll be glad :-)

---

### Post by siaco on 2007-04-27
I figured this one out myself :popcorn:

I guess I have overlooked a setting called "Color Model". This was set to RGB, but I changed it to CMYK which is what this printer uses, and now it works :)

---

