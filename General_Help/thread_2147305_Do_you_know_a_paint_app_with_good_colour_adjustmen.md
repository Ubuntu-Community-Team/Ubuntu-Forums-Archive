---
title: "Do you know a paint app with good colour adjustment utilities?"
date: 2013-05-21
forum: General Help
---

### Post by Mariane on 2013-05-21
Hi, 

First of all: if you are reading this the chances are you have struggled with colour adjustment at some point. Please tell me about it even if you are not certain it would help me. 

I've been using a lot of ink trying to get the colours of a picture the way I would want them to be. There is a HUGE difference between the colours displayed on the screen and the colours of the printed page. In KolourPaint I have in "Balance": Brightness, Contrast and Gamma. This can be applied to all channels or to one of the channels: Red, Green, Blue. There is also "Hue, Saturation, Value". But it is very hard for me to guess what the effect of any change will be once printed out. 

I cannot do much with my printer, but maybe there is some program out there which I could tune to get "True Colors" the way we have "True Type" (the printer knows the displayed fonts)? I imagine something where I would start by printing out some colour palette, then put the paper next to the screen and tune the display until the colours on the screen exactly match the colours on the paper. If you have ever heard about such utility, please tell me about it. 

Another question, is there any paint program which allows the user to tune colours as if they were real paint? I mean, blue + yellow = green, etc. I find this RGB stuff completely counter-intuitive. I would also need some kind of slider "Bright colours" <----------> "Pastel colours". 

All suggestions welcome :)

---

### Post by coldraven on 2013-05-21
Although I have never done it, I guess that you would have to calibrate your screen first.
It could be that the printed colours are correct and your screen is wrong.
Search for "colorimeter".

Also, how many ink cartridges does your printer have? If less than six you probably need a new printer.
You can reduce your ink costs by searching for "CISS" and the model of your printer.
I had the tank and flexible pipe system for several years, it worked great but makes moving the printer difficult.
[http://www.ebay.co.uk/itm/CISS-SYSTEM-FOR-EPSON-R200-R220-R300-R320-R340-RX500-RX600-RX620-RX640-WITH-INK-/221080856436?pt=UK_Computing_Ink_Refills_Kits&hash=item3379722774](http://www.ebay.co.uk/itm/CISS-SYSTEM-FOR-EPSON-R200-R220-R300-R320-R340-RX500-RX600-RX620-RX640-WITH-INK-/221080856436?pt=UK_Computing_Ink_Refills_Kits&hash=item3379722774)

 Now I use re-fillable cartridges similar to this.
[http://www.ebay.co.uk/itm/REFILLABLE-CARTRIDGE-FOR-EPSON-R200-R220-R300-R320-R340-RX500-WITHOUT-INK-/221054731239?pt=UK_Computing_Other_Computing_Networking&hash=item3377e383e7](http://www.ebay.co.uk/itm/REFILLABLE-CARTRIDGE-FOR-EPSON-R200-R220-R300-R320-R340-RX500-WITHOUT-INK-/221054731239?pt=UK_Computing_Other_Computing_Networking&hash=item3377e383e7)

---

### Post by Mariane on 2013-05-21
Thank you. Maybe I need a new printer, mine has 4 cartriges (black, purple, blue and yellow). 

It looks like a colorimeter is a physical object you have to buy (eg colorhug):
[http://www.hughski.com/](http://www.hughski.com/)
[http://ubuntuforums.org/showthread.php?t=2102686&highlight=colorhug](http://ubuntuforums.org/showthread.php?t=2102686&highlight=colorhug)

I don't have one but I will keep this option in mind.

---

### Post by zero2xiii on 2013-05-21
Hay,

Your issue is NOT your screen.

Sigh.. It is also not "black, purple, blue and yellow". It is Cyan, Magenta, yellow and black.

See here for details as to why RGB images and CMY printers have issues.

[http://photoshop4artists.blogspot.com/2009/04/cmyk-vs-rgb-knowing-which-color-space.html](http://photoshop4artists.blogspot.com/2009/04/cmyk-vs-rgb-knowing-which-color-space.html)
[http://www.cruxcreative.com/rgb-vs-cmyk-when-to-use-which-and-why/](http://www.cruxcreative.com/rgb-vs-cmyk-when-to-use-which-and-why/)
[http://marvin.mrtoads.com/rgb_vs_cmyk.html](http://marvin.mrtoads.com/rgb_vs_cmyk.html)

Once you have read all the above... You shall be enlightened.

Then next up you will want to know: "So how to convert RGB images to CMYK format".
See here for a rather amusing, but still informative, discussion on the matter:
[http://ubuntuforums.org/showthread.php?t=2138517](http://ubuntuforums.org/showthread.php?t=2138517)

Hope this clears (pun intended on that :D) things up haha.

Cheers

---

### Post by Mariane on 2013-05-22
You certainly didn't lie, these links did enlight me! :D 

So now it looks as though I will have to use gimp or imagemagick to convert my files from RGB to CMYK and then try to readjust the colours in CMYK format before printing. I'll post again, either to give hints to the next person or because I got stuck. Which is more likely is anybody's guess.

---

### Post by coldraven on 2013-05-22
I bow to zero2xiii's superior knowledge :)

---

### Post by zero2xiii on 2013-05-22
> **coldraven said:**
> I bow to zero2xiii's superior knowledge :)

:lolflag:

Please there is no need haha.. I just had to share that info since it is such a common mistake. Who knows WHY printer and software manufacturers never sat down and decided on a standard. Coming from a production company's point of view (stage and theater) the issue even deepens when using RGB lighting, with cameras, and then trying to convert and print in CMYK. A true nightmare! haha.


@Mariane glad I could help, and good luck with your journey, this is one thing GIMP, even 2.8, still lacks in and that is proper support for both color spaces...

Cheers :D

---

### Post by Mariane on 2013-05-22
I already had Gimp, so I started with:
```

sudo apt-get install gimp-plugin-registry
sudo apt-get install icc-profiles

```

In Gimp: "Image/Separate/Separate" offered me many baffling options. Which is the source colour space? I picked the first one on the list, sRGB. I ticked "preserve pure black", because this was something I could understand and it sounded desirable. Some copy appeared, which looked like my image in black and white and inverted. If I had not read that: 
[http://askubuntu.com/questions/114858/how-to-convert-image-to-cmyk-in-gimp](http://askubuntu.com/questions/114858/how-to-convert-image-to-cmyk-in-gimp)
I would have closed this horror on sight. 

In "Image/Separate/Export" I chose the default CMYK profile, saved under a new name, and hopefully opened back in KolourPaint. The printout was much paler than before, the colours were still off, only in a different way. After some mods I saved, I tried opening it back in Gimp. Gimp did not even see the file, and unlike KolourPaint it does not have a text field in the "open file" window where you can type the name. I tried closing Gimp and re-opening it, hoping it would refresh its file list. I didn't. So I found the file with Konqueror and did "Open with/Gimp". This worked but... Big deception! The file is back in RGB, one layer. 

Now I'll try again, and this time I'll try to export it layer by layer, hoping to get 4 files with adequate transparency, so that if I manually superimpose them I'll get my original picture back.

---

### Post by Mariane on 2013-05-22
Image/Properties says "Colour space = greyscale". Print preview displays something very similar to what is displayed on the screen, a nearly black picture.
I tried Image/Export and reopening. Now I have something which says it is in greyscale, 5 layers. Looks like I'll soon reach 50 shades of grey... Why am I in greyscale, what did I do wrong?

---

### Post by Mariane on 2013-05-22
Following advice here: [https://wiki.archlinux.org/index.php/CMYK_support_in_The_GIMP#About_CMYK_color_and_Gimp](https://wiki.archlinux.org/index.php/CMYK_support_in_The_GIMP#About_CMYK_color_and_Gimp)

I got:
[http://download.adobe.com/pub/adobe/iccprofiles/win/AdobeICCProfiles.zip](http://download.adobe.com/pub/adobe/iccprofiles/win/AdobeICCProfiles.zip)
[http://www.blackfiveservices.co.uk/linux_resources/separate-gimp2-0.3_linux.tar.gz](http://www.blackfiveservices.co.uk/linux_resources/separate-gimp2-0.3_linux.tar.gz) 
From: [https://aur.archlinux.org/packages.php?do_Details=1&ID=11438](https://aur.archlinux.org/packages.php?do_Details=1&ID=11438)

In uncompressed separate-gimp2-0.3_linux, there is a Makefile but no configure. Typing "make" says "nothing to be done for 'all'". It needs to be compiled with makepkg, which is not Ubuntu. I looked at the Makefile, you apparently need gccmakedep, and in the source code there is no main function, only a gtk_main (). 

```

make install

```

Said:
gimptool-2.0 --install-bin separate
make: gimptool-2.0: Command not found

```

sudo apt-cache search gimptool

```

Said:
libgimp2.0-dev - Headers and other files for compiling plugins for GIMP

```

sudo apt-get install libgimp2.0-dev
make install

```

Said:
gimptool-2.0 --install-bin separate
cp separate /home/kub/.gimp-2.6/plug-ins

```

gcc separate.c

```
Said: "separate.c:25:21: fatal error: gtk/gtk.h: No such file or directory"

In other words, this command returns "Forget it". ArchLinux stuff, not Ubuntu. I could get this lib, then it would miss other dependencies, which I also could get, etc. A very good way of going nowhere. I've been there, tried it, bought the T-shirt...

In subdirectory sRGB there is a file called sRGB Color Space Profile.icm which might be useful. In (uncompressed) Adobe ICC Profiles, there are 2 subdirectories called "CMYK Profiles"  and  "RGB Profiles". Both contain several .icc files. If I listed them here it would sound as a bad case of calligraphical hiccups. They might be useful, though.

---

### Post by Mariane on 2013-05-22
I think I understand why I get greyscale layers. Is it something like that:

---

### Post by Mariane on 2013-05-22
If I am not mistaken, which program could I use to access the layers one by one, please? For example, to get more intense blue I could try to make the blue layer darker before reassembling the 4 layers. OK, I would be working blind (I would have to find the correct settings by trial and error), but it still might do the trick if I'm patient enough :)

I tried to do it in Gimp, Scribus and Inkscape. Scribus and Inkscape seems to think the tiff file created by Gimp is one single layer...

---

### Post by Mariane on 2013-05-22
I've given up trying to separate layers and then tuning the picture layer by layer: I didn't find any way to access the individual layers. Tuning from KolourPaint is OK, and then finetuning with Gimp, using the "Color/Hue-Saturation" option which allows to play on the saturation of 6 different colours (which I'm not going to try to name).

One way to try and get it right from the start is to print out loads of palettes in the shades you are going to use and to tag all the squares according to their RGB values. Then you pick the closest match from the printouts. If you increment the values by 1, you have 16,777,216 possibilities. I wonder if someone out there has big books with all the 16,777,216 little squares printed out...

---

### Post by Mariane on 2013-05-22
I tested the RGB colours are additive vs CMYK colours are substractive.
The first picture was taken online. The second one shows what actually happens when you mix RGB colours together. White never appeared in the center. Magenta came up between red and blue. Green and red gave brown instead of yellow, green and blue gave emerald instead of cyan. And I was careful to start with the exact colours given in the RGB example... 

Puzzled.

---

### Post by zero2xiii on 2013-05-22
Hay,

Those ICC profiles are the problem uh solution.

See they exist for a reason, every image has a different profile based on the program and colour space originally worked in and then for printing the ICC profile is used to match this to the printer/paper used. And yes it will be paler. Just as you can greyscale an image based on 3 properties (Lightness, Luminosity, Average) in gimp, the way gimp processes it inside it different than let us say photo shop.

Those profiles is similar, you need to find one the closest match to the paper, and printer you are going to use.

here are two links going in more depth:
[http://graphicssoft.about.com/od/aboutgraphics/f/printedcolors.htm](http://graphicssoft.about.com/od/aboutgraphics/f/printedcolors.htm)
[http://www.colorwiki.com/wiki/How_To_Get_My_Monitor_To_Match_My_Printer](http://www.colorwiki.com/wiki/How_To_Get_My_Monitor_To_Match_My_Printer)

The important section is found in the second link:
> "Canned" profiles

Each printer driver comes with ICC color profiles that are specifically designed for the papers that the printer manufacturer sells. For example: An Epson printer will come with profiles like "Epson Premium Luster". These are designed to correctly print color onto this same kind of paper in your printer. If you are printing with Epson Premium Luster paper, then you would choose this profile when you print.

Another problem you MIGHT face, with regards to the "it is still off, but differently so" issue is this:
> Is the color within your device's ability to reproduce?

Due to gamut differences between your image, monitor and printer, colors on the monitor may not be printable (e.g., saturated blues, greens and reds) and colors not visible on the monitor may appear on the print (often cyans).

Again, having an RGB display, means you can not see the CMY, and other way around. For a full true colour display you will need 8 pixels (6 printer heads have been mentioned earlier if I recall correctly) namely Red, Green, Blue, Cyan, Magenta, Yellow, White, Amber. And even then you might still miss something but it will be MUCH better... Adding the different screen display types in the mix, (such as pentile), things truely gets messy. 

It is for this reason pro printing shops spends thousands of bucks on getting everything matched. It is starting to boil down to "How important is the EXACT color really".

Hope this helps a bit, trail and error is the best way to go here, try and buy a paper which profile you have if you can not find a profile for the paper you use.

Cheers and really good luck!

---

### Post by Impavidus on 2013-05-22
> **Mariane said:**
> 
One way to try and get it right from the start is to print out loads of palettes in the shades you are going to use and to tag all the squares according to their RGB values. Then you pick the closest match from the printouts. If you increment the values by 1, you have 16,777,216 possibilities. I wonder if someone out there has big books with all the 16,777,216 little squares printed out...
I don't have the book in print, but you can use this PostScript file and print it yourself:```

%!PS
/red 0 def
/green 0 def
/gencolour {red 255 div green 255 div blue 255 div setrgbcolor} def
/Helvetica 0.6 selectfont
/numerals [(0) (1) (2) (3) (4) (5) (6) (7) (8) (9) (a) (b) (c) (d) (e) (f)] def
/printhex { %print integer < 256 in hexadecimal
dup 16 lt {numerals exch get show}{dup 16 idiv numerals exch get show 16 mod numerals exch get show} ifelse} def
/makepage {28.35 dup scale 2.5 15 translate %Set scale in cm
maketable
/green green 1 add def
0 -12.5 translate
maketable
/green green 1 add def
showpage
} def
/maketable {0 0 0 setrgbcolor /blue 0 def
%Print labels
0 11 moveto (R=) show red printhex (, G=) show green printhex
0 10 moveto (B=) show
0 1 15 {dup 1 add 10 moveto (x) show printhex} for
0 1 15 {dup 0.6 mul 0 exch moveto 15 exch sub printhex (x) show} for
%Print table
15 -1 0 {gsave 0.6 mul 1 exch translate
16 {/blue blue 1 add def gencolour
0 0 moveto 0.8 0 lineto 0.8 0.5 lineto 0 0.5 lineto closepath fill 1 0 translate} repeat
grestore
} for } def
256 {/green 0 def 128 {makepage} repeat /red red 1 add def} repeat

```
Careful! Don't send this file to your office's PostScript printer without first consulting the IT department! The printer will happily process it for you and produce 32768 pages of full colour output. If you convert it to pdf, keep in mind it will expand by a factor of 100000.

Just kidding.

Printers use white paper with light-absorbing inks, so by their very nature they use subtractive colours. Monitors have coloured dots sitting in columns next to each other, which you can view blended to all those mixed colours, so by their very nature they use additive colours. In principle, the amount (=fraction of the surface covered) of yellow ink to get the same colour as on the screen is one minus the amount of blue light, reason why the primary colours of one system are the secondary colours of the other, but in practice this is far from accurate. For some colours you just need a negative amount of ink.

---

### Post by zero2xiii on 2013-05-22
> **Mariane said:**
> I tested the RGB colours are additive vs CMYK colours are substractive.
The first picture was taken online. The second one shows what actually happens when you mix RGB colours together. White never appeared in the center. Magenta came up between red and blue. Green and red gave brown instead of yellow, green and blue gave emerald instead of cyan. And I was careful to start with the exact colours given in the RGB example... 

Puzzled.

That is wrong.

Let us assume the following:
R G B
0 0 0

This means the colour is black (no red, green or blue).

Now if we take red:
R G B
9 0 0

And add Blue for example:
R G B
0 0 9

We get:
R G B
9 0 9

Which is purple-ish. It is a math (computer and literal lighting) thing.
Mixing (subtractive) is done differently, for explanation we will use binary:
Bin   Dec
01 = 1
10 = 2
11 = 3

What happens when you add lets say 01 + 01 = 10 NOT 02 (a different color not darker).

This is true for subtractive coloring.

Remember this is how nature works:
White passing through a light blue filter (or bouncing of a light blue object in real life)
R 9 > 0
G 9 > 4
B 9 > 8

Thus passing white light through 3 filters will cause no light to stay behind:
     B    G    R
R 9 > 0 > 0 > 0
G 9 > 0 > 0 > 0
B 9 > 9 > 0 > 0

 In GIMP, if you create 3 layers, make their mode additive and colour each layer EXACTLY Red, Blue, Green, you will get white. FF+FF+FF = FFFFFF. Subtractive, you will get black FF-FF-FF=000000
Simply adding colors on one layer together will not work in the same way.

Look at the photo printing shops where they use the 4 step machines. The image comes out, Cyan coloured ONLY, then Cyan and Magenta, and finaly fully coloured. It is truely amazing when you get into the science of light and colour and see how everything we want to "just work" simply cant do to the laws of nature and some designers not talking to each other.

This topic truely facinates me, and I can write books on how amazing it is that it has come so far already, but, sadly, it still have a loooong way to go and might never even get there.

Have fun and really good luck.

EDIT:D
ig through wikipedia if this interests you:
[http://en.wikipedia.org/wiki/Color](http://en.wikipedia.org/wiki/Color)
[http://en.wikipedia.org/wiki/Color_theory](http://en.wikipedia.org/wiki/Color_theory)
[http://en.wikipedia.org/wiki/Color_mixing](http://en.wikipedia.org/wiki/Color_mixing)
[http://en.wikipedia.org/wiki/Additive_color](http://en.wikipedia.org/wiki/Additive_color)
[http://en.wikipedia.org/wiki/Subtractive_color](http://en.wikipedia.org/wiki/Subtractive_color) (Has a section on the printing process which after all the above will make sence)

---

### Post by Mariane on 2013-05-23
Thank you both. I know light is important. To check colour I look at the printouts in sunlight or under a strong halogene lamp. If it's good when seen like that, it will also be good when viewed in ambient light but the reverse is not true. 

We see in RGB, don't we? I mean, what our eyes perceive are photons, no matter whether they come from light reflected on some ink or from a computer screen. 

A computer screen gives off light, a printout can only reflect a portion of the light which is already here. Even if no visible wavelength is missing from the light received by the paper, it cannot reflect perfectly. People say that light is evenly reflected by pure white paper, and that this is why it seems white. But if it reflected everything, it would not seem to be white, would it? It would be a mirror. So, what is happening? If white paper does not reflect everything, then it must absorb something. Now a computer screen, which does not absorb light but emits light, can maybe do stuff with the wavelengths that no paper can ever match. Is this what Impavidus means by "negative colours"? 

@zero2xiii 

If I do have to buy a new printer, which one would you advise? (Taking into account the necessity of having a Ubuntu driver for it). I test on the cheapest A4 around, and after that I use smooth 90 grams per square meter paper. Please let me know if you ever do write this book.

@Impavidus 

You both made me smile and had me baffled :).

---

### Post by HiImTye on 2013-05-23
we don't see RGB, we see a difference of blue/yellow, red/green, white/black
companies such as Disney exploit it in their parks by making vibrant red paths to make the green grass seem greener. you should read up on 'impossible' colours ;)
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Impavidus on 2013-05-23
Our eyes see RGB-white,* which is transformed to yellow/blue, red/green, black/white by the neurons in the retina, and after that wavelet transformed and compressed before being send onto the optical nerve. This is almost identical to JPEG compression, and therefore JPEG compression is so effective. It even leaves the same artefacts, like dark spots on the intersections of the white bars in a field of black squares. Colour television also uses this colour conversion to make a colour TV signal compatible with black and white TV sets.

Mathematically speaking, colour is a 3 dimensional space. Any 3D space unbounded in every direction can be transformed into any other 3D space unbounded in every direction using coordinate transforms, which allows RGB to be converted to CMY, with K being dependent on CMY. The problem now is that the colour space is not unbounded, as a colour with a negative amount of let's say green doesn't exist. Therefore colour transformations don't always work out. To get better approximations the number of inks or pigments on a screen has to be increased, so we sometimes have six or more cartridges in our printers and there are TV sets with red, green, blue and yellow dots.

Sunlight and halogen lamps have continuous spectra. Incandescent lamps miss the blue part, making them unsuited to working with blue colours, energy saving lamps have line spectra, making them unsuited to any fine colour working. And the difference between a mirror and perfectly white paper is that for a mirror angle of reflection=angle of incidence, but for paper angle of reflection=random. Both can reflect all wavelengths

Really, fascinating subject.

*Three kinds of colour-sensitive cells and one kind of grey sensitive cells. The grey sensitive ones are saturated in bright light condition, the colour sensitive ones stop working in low light conditions, so only three work at the same time, with a gradual transition. In fact, the gene for the green sensitive pigment is rather variable and present on the X chomosome, so women have two versions and if sufficiently different from each other and from the red one, they may see four channels. Men, when unlucky, may only have one almost identical to the red sensitive type and then see only two channels.

---

### Post by zero2xiii on 2013-05-27
> Really, fascinating subject.

I whole heartily agree with that!


Sorry about the delay in my posting, I had a few shows and then I do not get near the computer.


The long and the short of it all comes down to: "The chances of getting the RGB image you see on screen reprinted PERFECTLY by a CMY source, is very close to impossible." You might get it close, but never perfect. If it is truly important to be perfect, try a printshop, as they might be able to recreate the image in a CMY format to begin with, and this will take away some of the issues.

Kind regards and very much good luck.

---

