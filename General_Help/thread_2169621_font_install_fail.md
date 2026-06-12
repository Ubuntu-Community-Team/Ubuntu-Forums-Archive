---
title: "font install fail"
date: 2013-08-22
forum: General Help
---

### Post by Buntu Bunny on 2013-08-22
I had some trouble installing a font today. Several others installed easily with the "install font" button on the font viewer. For the last one, I got an "install failed." All are opentype fonts. 

Following the instructions at [Ask Ubuntu ]("http://askubuntu.com/questions/18357/how-to-install-otf-fonts")and [Wikihow]("http://www.wikihow.com/Install-TrueType-Fonts-on-Ubuntu"), I used Terminal to create an opentype directory in /usr/share/fonts/ and then copied the .oft file to it. That was successful, but the font doesn't show up in LibreOffice. 

Next I searched the Forums and found [this thread]("http://ubuntuforums.org/showthread.php?t=2158455&page=2&highlight=libreoffice+fonts"). Following it's advice, I ran 

```
fc-cache -fv
```

and 

```
sudo fc-cache -fv
```

both reported

```
fc-cache: succeeded
```

I also learned about the .fonts directory in my home folder and checked there. I discovered the problem font was indeed there, but it *still* isn't showing up in LibreOffice. 

Any suggestions of what else I can do?

Edit: I just checked Gimp, Inkscape, and Scribus and it's listed there. It's listed twice in Gimp, in fact. However, a similar font that I also installed *is not *in any of these but is in LibreOffice.

---

### Post by vasa1 on 2013-08-22
What is the source of this font? Others could try to reproduce your issue if you shared that information.

---

### Post by Buntu Bunny on 2013-08-22
Thank you vasa1. That might be helpful. I downloaded it from Font Squirrel, [EB Garamond]("http://www.fontsquirrel.com/fonts/eb-garamond"), though it appears to be widely available. 

The only place it hasn't show up has been LibreOffice.

---

### Post by vasa1 on 2013-08-23
> **Buntu Bunny said:**
> ...
The only place it hasn't show up has been LibreOffice.
If you don't get help here, try over here: [http://nabble.documentfoundation.org/Users-f1639498.html](http://nabble.documentfoundation.org/Users-f1639498.html)
That site is dedicated to LibreOffice and offers "User to User support for LibreOffice suite applications: Writer, Calc, Draw, Impress and Base."

Then there's also [http://ask.libreoffice.org/en/questions/](http://ask.libreoffice.org/en/questions/).

---

### Post by Buntu Bunny on 2013-08-23
Thanks vasa1! I will have to do that.

To add to the mystery, the problem font showed up in LibreOffice this morning, but another one disappeared. :confused:

---

### Post by Dennis N on 2013-08-23
Downloaded your font, extracted the two font files to ~/.fonts, opened Libreoffice and there it was in the drop down list. Doesn't solve your mystery, but verifies the font is ok. No it isn't - see below.

Edit: Tested it some more, and something is strange. I only have the small caps font - I think this is the EBGaramondSC.otf file (SC for small caps). The other choices do not show for me in the LO dropdown font list, so comfirms your issue there. I looked at them in Specimen Font Previewer, and the other varieties (with lower case letters) are selectable and display ok, but the SC variety displays as regular (with lower case). Some incompatability with LO?

---

### Post by Dennis N on 2013-08-23
Additional test: Abiword and Gnumeric display the regular EBGaramond (with lower case) but not the EBGaramondSC (it is not listed as an option). Just the opposite of LO. I won't be keeping this one.

---

### Post by Buntu Bunny on 2013-08-23
> **Dennis N said:**
> Downloaded your font, extracted the two font files to ~/.fonts, opened Libreoffice and there it was in the drop down list. Doesn't solve your mystery, but verifies the font is ok.

That was something I wondered about so thank you for that!

> **Dennis N said:**
> Edit: Tested it some more, and something is strange. I only have the small caps font - I think this is the EBGaramondSC.otf file (SC for small caps). The other choices do not show for me in the LO dropdown font list, so comfirms your issue there. I looked at them in Specimen Font Previewer, and the other varieties (with lower case letters) are selectable and display ok, but the SC variety displays as regular (with lower case). Some incompatability with LO?

Additional test: Abiword and Gnumeric display the regular EBGaramond (with lower case) but not the EBGaramondSC (it is not listed as an option). Just the opposite of LO. I won't be keeping this one.

That's exactly what I'm running into; not all programs list both regular and SC, except for Scribus (which is actually the program I need these fonts for). So it can't necessarily be LO, or GIMIP, or Abiword; it must have something to do with the fonts themselves (?)

---

### Post by Buntu Bunny on 2013-08-23
Okay, I just sent an email to the fonts' creator, explaining the problem. If I get some feedback, I'll post it here.

---

### Post by vasa1 on 2013-08-24
> **Dennis N said:**
> Additional test: Abiword and Gnumeric display the regular EBGaramond (with lower case) but not the EBGaramondSC (it is not listed as an option). Just the opposite of LO. I won't be keeping this one.
Out of curiosity, I too installed the fonts but I only see the regular one as an option in LibreOffice (Writer and Draw), Firefox, Chrome, Gedit, lxterminal, geany, medit and Leafpad. I don't see EBGaramondSC as an option anywhere.

I don't have Abiword or Gnumeric installed.

---

### Post by Buntu Bunny on 2013-08-24
> **vasa1 said:**
> ....and Leafpad.

I didn't even know Leafpad offered font options, LOL, see what one learns by asking questions?

My version of Leafpad lists EB Garamond and offers SC under style, but if selected, still only types in regular. 
Opera only shows SC.
GIMP lists regular twice.

Scribus is the only program that recognizes both.

So what would cause this? Some quirk in the code?

---

### Post by vasa1 on 2013-08-24
> **Buntu Bunny said:**
> ...
My version of Leafpad lists EB Garamond and offers SC under style, but if selected, still only types in regular. 
...
Now that you point it out, I see that as well. I was looking for SC in the actual font name column.

([FONT=Comic Sans MS]Apropos nothing at all, I've started viewing some web sites in Comic Sans MS[/FONT])

---

### Post by Buntu Bunny on 2013-08-24
[FONT=Comic Sans MS]I heard back this morning from the designer of EB Garamond, Georg Duffner. He recommended that I download the fonts from [Bitbucket]("https://bitbucket.org/georgd/eb-garamond/downloads"), as other sources are outdated. I did that and am happy to report that it resolved *some* of my issues. LO now recognizes and offers both regular and SC. No change with Leafpad (which I don't need it for anyway), but GIMP now lists EB Garamond *three* times, all regular. 

LO and Scribus are the two programs for which need this font, so for now, I reckon I'll have to be satisfied with the way things are.

This all started as a search for open source fonts for a print project. Who knew that book designers were snooty about fonts, and that it is expected to pay for them. Me? Open source all the way!!!!

P.S. @ vasa1, isn't that the fun of fonts? ;)[/FONT]

---

### Post by Dennis N on 2013-08-24
B.B., 
Thanks for the information. I admit I don't know much about fonts, except that I have too many listed in the selection dialogs. Abiword has a way to customize (or restrict) the listed items to the ones you want to actually use - I wish LO would do the same.

---

### Post by Buntu Bunny on 2013-08-24
> **Dennis N said:**
> Abiword has a way to customize (or restrict) the listed items to the ones you want to actually use - I wish LO would do the same.

That would be extremely useful and I wish LO would do that as well. I have Abiword, but started with OO which was replaced by LO, so that's what I'm used to. I pulled Abiword up just to see, but found what you already mentioned, it only offers EB Garamond regular.

---

### Post by Dennis N on 2013-08-24
I go with LO too. Was using Abi regularly before the LO came along, as OO took forever to start up on my first Ubuntus and Abi was quick. However, when the unready and unusable version of AW was distributed a while back (11.10?) I switched.

---

