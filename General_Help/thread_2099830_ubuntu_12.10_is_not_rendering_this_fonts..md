---
title: "ubuntu 12.10 is not rendering this fonts."
date: 2012-12-30
forum: General Help
---

### Post by Joao Lacerda on 2012-12-30
Hi friends!

This fonts are not being rendering in this version of Ubuntu.
OpenLogos.ttf
Webdings.ttf
Windings.ttf

This fonts are used in conky, I have looked in /usr/share/fonts/
and I see only squares in this fonts.
Can someone help on this.
Thanks in advance.

João

---

### Post by xc3RnbFO8P on 2012-12-30
Did you try to put them in your home folder ?
~/.font

---

### Post by Joao Lacerda on 2012-12-30
Hi friend thank you for answering.
I did it and it still no working.
any other idea?

João

---

### Post by xc3RnbFO8P on 2012-12-30
In terminal try this:
> sudo fc-cache -f -v

---

### Post by Juniorr on 2012-12-30
Hi. Have you tried to install "Ubuntu restricted extras"? It has all the fonts i guess.

---

### Post by Joao Lacerda on 2012-12-30
[ATTACH]229357[/ATTACH]

I have done and it still not working.

Thank you.

---

### Post by xc3RnbFO8P on 2012-12-30
Restart your computer

---

### Post by Joao Lacerda on 2012-12-30
I forgot to mention that on my laptop I have the same problem, and it was not so with 12.04. I really do not understand, how this is possible.
Thank you for your time.

---

### Post by xc3RnbFO8P on 2012-12-30
Do you have **ubuntu-restricted-extras** installed?

---

### Post by stinkeye on 2012-12-30
It's a 12.10 problem.
Have the same thing with certain downloaded fonts that worked with conky in 12.04.
Although **OpenLogos** displays fine.


Pics show difference between Precise and Quantal using ConkySymbols font.

---

### Post by Joao Lacerda on 2012-12-30
yes I do have it, and also apt-get install ttf-mscorefonts-installer,etc etc.
and none of this is working. The problem is not the font, the problem is that ubuntu 12.10 is not rendering this fonts. I have search it a lot on google, on forums, etc , but till now I have not found any solution.
But thank you for spend your time with this. It is high appreciated.

all the best.

João

---

### Post by Juniorr on 2012-12-30
Is your video card updated? What brand is it?

---

### Post by Joao Lacerda on 2012-12-31
Hello Friend. I do not believe that it has to with the Video card.
But this is my GPU, the f nvidia drivers do not work for me with ubuntu 12.10 [ATTACH]229371[/ATTACH]

---

### Post by Joao Lacerda on 2012-12-31
Can maybe some friends give some help on this?

---

### Post by artek150 on 2013-01-08
I have the same problem and I think this is not graphic card issue, because in libre office this font working normal, and only with it. In system font manager i see rectangles - not font symbols. When I choose webdings font in gimp there is only a,c,d c characters (I think this is default font). 

ps.
ubuntu 12.10 is worst version ubuntu ever :[

---

### Post by Joao Lacerda on 2013-01-16
Hi Friends,

That is what I have done to fix this problem, I hope it will work for you too.

Download Install FontForge from Ubuntu Software Center:
Open de font:
Reencode de font Glyph Order:
Generate the font:
Choose trueType, and TrueType (only) see pictures
Save as .ttf and replace the original
and that is it.
For Openlogos. download it and install it again.
[http://www.dafont.com/openlogos.font](http://www.dafont.com/openlogos.font)

Have a nice day. :-)

João

---

### Post by stinkeye on 2013-01-16
Thanks for this fix.

---

### Post by BillySastard on 2013-04-08
Thanks João,

same problem on Mint Nadia, your fix worked like a charm.

Chris

---

