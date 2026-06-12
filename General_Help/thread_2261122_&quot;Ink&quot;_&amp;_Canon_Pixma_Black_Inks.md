---
title: "&quot;Ink&quot; &amp; Canon Pixma Black Inks?"
date: 2015-01-16
forum: General Help
---

### Post by 2CV67 on 2015-01-16
My old Canon Pixma iP4300 printer has 5 inks including 2 blacks.
There is a small CLI-8BK & a large PGI-5BK.

I know it uses a "Pigment" black for text & a "Dye" black to mix with the other 3 CLI-8C/M/Y colours, but am not sure which is which.
(the "P" could be Pigment or Photo...)

Oddly, the cartridges don't specify which black is which either.
I did a lot of browsing & found both answers!
I could not find anything signed Canon.

So I contacted Canon & they tell me the PGI is Pigment & the CLI is Dye.
I assume I can trust that answer, even though other parts of their response seem wrong...

In Ubuntu, I use "Ink" & "libinklevel5" applications to tell me ink levels.
This gives me a readout as follows:
Black
Photoblack
Yellow
Magenta
Cyan
which corresponds nicely with the order of the cartridges in the printer EXCEPT for the 2 blacks, the order in the printer being:
CLI-8BK/PGI-5BK/CLI-8Y/CLI-8M/CLI-8C.

So, 2 questions:
Which black cartridge is really Pigment & which is Dye?
Which black cartidge does "Ink" consider Black & which Photoblack?

I would really like facts, not opinions!

Thanks!

---

### Post by 2CV67 on 2015-01-17
This is (part of) the reply I received very rapidly from Canon & which I thought very satisfactory:

> Your printer runs on a 5 INK SYSTEM, 4 DYE BASED AND 1 PIGMENTED INK BASED (the large black) cartridges. 

The PGI-5BK cartridge (pigmented based) is used for a pure black printing. This cartridge will only be used when printing black text on plain paper (the paper type is the driving point for the selection of ink, if you are printing on photo-paper, then the dye based ink will be used), the PGI-5BK cartridge cannot be used for mixing colours.

The CLI-8BK cartridge (dye based) will kick in when:
1. The application prints it as an image.
As it will then need to mix colours to obtain the correct colour, it will use the CLI-8BK set.

2. The colour isn’t a pure black colour.
It will then use the CLI-8BK set of cartridges to obtain the correct taint of colour.

3. Greyscale printing is enabled.
Every colour will have a certain taint of grey, even black. Meaning that on every print, it will use the colour cartridges to obtain the correct shade of grey.

But I doubted the Greyscale explanation, so ran a couple of tests, using LibreOffice Draw with a small rectangle of Grey-2 color on plain paper & looking at the results with a magnifying glass.
In Ubuntu, my default printer color mode is CMYK & using this, the grey is printed as very fine dots of various colors.
Forcing Greyscale color mode, the grey is printed as fewer & bigger & visibly superficial black dots.
I wondered if this was a quirk of Ubuntu printer drivers.
I also have Windows 8.1 with a genuine Canon driver, so tried that too.
In default mode - fine multicolor dots.
In forced Greyscale mode - coarse black dots.

Conclusion - you can't blindly believe anybody!

---

