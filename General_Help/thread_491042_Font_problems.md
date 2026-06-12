---
title: "Font problems"
date: 2007-07-03
forum: General Help
---

### Post by igm on 2007-07-03
I recently upgraded to feisty and have a bunch of font problems now that I haven't had before.

Pigiarniq from [http://www.gov.nu.ca/font.htm](http://www.gov.nu.ca/font.htm) comes in several weights. I installed it by dragging the .ttfs into the font folder. They are all messed up in Gnome, Inkscape, and Krita, but not in Scribus. Regular and light look now like bold (or heavy?), bold and heavy look like regular. In edgy they were just fine. Furthermore, some kernings are really bad. For example Tr for most sans-serif fonts are much too tight.

Any ideas?

Ingo

---

### Post by donmiguel on 2007-07-03
Did you install them properly?? Take a peak on this site : [http://www.wikihow.com/Install-Ttf-Fonts-on-Ubuntu](http://www.wikihow.com/Install-Ttf-Fonts-on-Ubuntu)

good luck

---

### Post by igm on 2007-07-03
I presumed that I installed them properly. They worked in Edgy. The font weight problem exists for the Pigiarniq fonts which I installed again after the upgrade just to make sure. I installed them by dragging them to the fonts:// folder as described here: [http://ubuntuforums.org/showthread.php?t=275202](http://ubuntuforums.org/showthread.php?t=275202). I even ran "sudo fc-cache -fv" even though i did not need it in Edgy.
The "Tr problem" exists not only for fonts I installed myself but also for others such as Bitstream Vera Sans, for example.

Ingo

---

### Post by igm on 2007-07-03
I just checked several apps regarding Pigiarniq font weights and Tr kerning with sans-serif fonts like Corbel (for some fonts it is a general kerning problem: T followed by any letter without ascenders has not enough space in-between, Ty, Tr, Tg, ...)

Scribus: everything fine
Open Office, qtconfig, Krita: Pigiarniq weight messed up (bold is lighter than regular), Corbel Tr is fine
Inkscape, Gimp, Gnome font prefs: both messed up

To illustrate the Tr problem, I attached a screenshot of Inkscape.

Ingo

---

### Post by Hatchetfish on 2007-10-29
I've had the same problem, with a huge variety of different fonts, Type1, TTF, OTF, doesn't matter, it's happened with one or another in any of the formats.  It's especially common with 'Pro' fonts, the ones that come with a wider range of weights than just regular and bold, but it's also happened with plenty of of the usual 'Regular/Italic/Bold/Bold-Italic' sets.

The symptoms I've seen range from one weight being identical to another (especially common is that Regular and Bold are both bold, or Black/Heavy if it exists, and the Italic versions do the same) to the weirdest yet: one set of four (R/I/B/BI) that shows up in font selection dialogues as having Regular, Itallic, and two each of Bold and Bold Italic.  I've checked, hand to god there's only four font files there, and when I move them out of the searched fonts directory, all six variants disappear.

Incidentally, this has been happening to me with every version of ubuntu yet, from pre-warty through now gutsy.

It is a mystery, no?

---

### Post by Hatchetfish on 2007-10-29
The other thing I've noticed is that the only gtk+ program that doesn't do this is the gnome font viewer, opening individual fonts directly.  Looking at its rendering, it appears to use some other system than fontconfig/freetype, so not exactly surprising that it doesn't share the bug with the rest of the system  (I haven't actually ever tried it with QT; I just really don't use any QT programs I can think of except Opera, and it has font issues all its own...)

---

### Post by bit-a on 2008-04-06
Hi folks.

As there was no satisfying solution to this thread i decided to think about OOo@ubuntu and the lovely Pigiarniq font. As I can see there are three solutions.

1. the dumb proof way: As long as you can abstain from the heavy and the light series, only copy regular, bold and italic to your font path. As soon as heavy or light is seen in font path, everything gets messed up.

2. the impossible way: So far I know how fonts work, I guess, that if you opened heavy or light with fontforge or so (attend the conjunctive, as the copyright says, that you must not do so!) there might be some warnings about inconsistent parameters or so... you know, I must not try this way.

3. the long way: Ask the guys at [tiro]("http://www.tiro.com/syllabics/resources/index.html") to fix their bug.

Hope this helped. See ya soon folks.

---

