---
title: "Cyrillic fonts in Firefox"
date: 2005-09-26
forum: General Help
---

### Post by Joloc on 2005-09-26
When I use Firefox to access a Russian page (like [http://mail.ru/](http://mail.ru/)) I get lots of squares with hex humbers in them instead of the actual characters.

I assume I do not have the correct font package installed for the needed characters to be displayed.

What package go I need?

---

### Post by Limulus on 2005-09-26
Hmm... I dunno if you actually need to install anything so much as poke at Firefox's settings.  I'm using FF 1.0.7 on Breezy and it shows the characters just fine ^_^;

Maybe go View -> Character Encoding -> Customize List... and check for Cyrillic (KOI8-R) which is what FF is telling me that page is.

---

### Post by Limulus on 2005-09-26
Oh and if its not there, I just noticed that if you go into Synaptic and right-click "firefox" it suggests installing "latex-xft-fonts" so maybe try installing that package too? (just click on it after right-clicking "firefox" and it should mark it for installation)

---

### Post by Joloc on 2005-09-26
Yes, I am sure I do not just need to tweak the settings. When the wrong encoding is selected characters come out looking wrong, but are usually proper characters, just look like [http://en.wikipedia.org/wiki/Image:Letter_to_Russia_with_krokozyabry.jpg]("http://en.wikipedia.org/wiki/Image:Letter_to_Russia_with_krokozyabry.jpg")

Are you sure you get proper characters that look like [http://www.friends-partners.org/oldfriends/language/russian-alphabet.html]("http://www.friends-partners.org/oldfriends/language/russian-alphabet.html")
?
When Cyrillic (KOI8-R) is selected with mail.ru I get characters that say 043F 043E 0447 0442 0430, 043D 043E... in little squares. Whilst I can get out a character map and work out what the letters mean it is not very practical.

IIRC in Slackware the problem was fixed by installing an extra Slackware package. What is the Ubuntu equivalent?

---

### Post by Joloc on 2005-09-26
"latex-xft-fonts" does not seem to work either. :(

---

### Post by Limulus on 2005-09-26
[QUOTE=Joloc]Are you sure you get proper characters that look like [http://www.friends-partners.org/oldfriends/language/russian-alphabet.html]("http://www.friends-partners.org/oldfriends/language/russian-alphabet.html")
?
When Cyrillic (KOI8-R) is selected with mail.ru I get characters that say 043F 043E 0447 0442 0430, 043D 043E... in little squares.[/QUOTE]

Yes; for example, on the right where there are little icons, some of them are like (ASCII rough-equivalent)

[heart with arrow through it] 3HAKOMCTBa
[red car] ABTO
[shovel] Pa6OTa

When I go View -> Character Encoding
it looks like this:

Auto-Detect -> * (Off)
More Encodings -> [lots and LOTS of types listed in sub-menus]
Customize List...
---------------------
* Western (ISO-8859-1)
[and then several more types]

If you click "More Encodings" you get a little window popping up that has two lists: "Available Character Encodings" (which has a LOT in it) and "Active Character Encodings" (which only has Western (ISO-8859-1) and Unicode (UTF-8 ) in it).

Does "Cyrillic (KOI8-R)" appear anywhere in the list of "Available Character Encodings"?

Also, under Edit -> Preferences -> Fonts & Colors...

Is there a check by "Always use my: Fonts"?  If so, try unchecking it and see what happens.

---

### Post by Joloc on 2005-09-27
OK, I guess I will not do away without posting a screenshot of the problem.

[http://antz.uwcs.co.uk/ff.png]("http://antz.uwcs.co.uk/ff.png")

My firefox settings are OK. I am missing the fonts and want to know what package they are in.

---

### Post by Limulus on 2005-09-27
:/  Not sure... as a wild stab at the problem, do you have the package "xfonts-base" installed?

Also, since you didn't mention it earlier and I forgot to ask, are you running FF 1.0.7?

---

### Post by Joloc on 2005-09-27
Yes, running 1.0.7.

These are the font-related packages have already installed from ubuntu + universe, they do not seem to butter the muffin for Firefox.

$ dpkg-query -l | grep font
ii  console-data   2002.12.04dbs- Keymaps, fonts, charset maps, fallback table
ii  console-tools  0.2.3dbs-55ubu Linux console and font utilities
ii  defoma         0.11.8ubuntu2  Debian Font Manager -- automatic font config
ii  fontconfig     2.2.3-4ubuntu7 generic font configuration library
ii  latex-xft-font 0.1-5          Xft-compatible versions of some LaTeX fonts
ii  libconsole     0.2.3dbs-55ubu Shared libraries for Linux console and font 
ii  libfontconfig1 2.2.3-4ubuntu7 generic font configuration library (shared l
ii  libfreetype6   2.1.7-2.3      FreeType 2 font engine, shared library files
ii  libxft2        2.1.2-6ubuntu1 FreeType-based font drawing library for X
ii  ttf-opensymbol 1.1.3-8ubuntu2 The OpenSymbol TrueType font
ii  xfonts-100dpi  6.8.2-10.1     100 dpi fonts for X
ii  xfonts-75dpi   6.8.2-10.1     75 dpi fonts for X
ii  xfonts-base    6.8.2-10.1     standard fonts for X
ii  xfonts-cronyx- 2.3.8-4        100 dpi Unicode Cyrillic fonts for X (Cronyx
ii  xfonts-cronyx- 2.3.8-4        75 dpi Unicode Cyrillic fonts for X (Cronyx 
ii  xfonts-cronyx- 2.3.8-4        100 dpi CP1251 encoded Cyrillic fonts for X 
ii  xfonts-cronyx- 2.3.8-4        75 dpi CP1251 encoded Cyrillic fonts for X (
ii  xfonts-cronyx- 2.3.8-4        Character-cell CP1251 encoded Cyrillic fonts
ii  xfonts-cronyx- 2.3.8-4        100 dpi ISO 8859-5 encoded Cyrillic fonts fo
ii  xfonts-cronyx- 2.3.8-4        75 dpi ISO 8859-5 encoded Cyrillic fonts for
ii  xfonts-cronyx- 2.3.8-4        Character-cell ISO-8859-5 encoded Cyrillic f
ii  xfonts-cronyx- 2.3.8-4        100 dpi KOI8-R encoded Cyrillic fonts for X 
ii  xfonts-cronyx- 2.3.8-4        75 dpi KOI8-R encoded Cyrillic fonts for X (
ii  xfonts-cronyx- 2.3.8-4        Character-cell KOI8-R encoded Cyrillic fonts
ii  xfonts-cronyx- 2.3.8-4        100 dpi KOI8-U encoded Cyrillic fonts for X 
ii  xfonts-cronyx- 2.3.8-4        75 dpi KOI8-U encoded Cyrillic fonts for X (
ii  xfonts-cronyx- 2.3.8-4        Character-cell KOI8-U encoded Cyrillic fonts
ii  xfonts-cronyx- 2.3.8-4        Character-cell Unicode Cyrillic fonts for X 
ii  xfonts-cyrilli 6.8.2-10.1     Cyrillic fonts for X
ii  xfonts-scalabl 6.8.2-10.1     scalable fonts for X

---

### Post by Limulus on 2005-09-27
Here's what I got when I did the same:

$ dpkg-query -l | grep font
ii  console-data                          2002.12.04dbs-49ubuntu4              K eymaps, fonts, charset maps, fallback table
ii  console-tools                         0.2.3dbs-56ubuntu4                   L inux console and font utilities
ii  defoma                                0.11.8ubuntu2                        D ebian Font Manager -- automatic font config
ii  fontconfig                            2.3.2-1ubuntu1                       g eneric font configuration library
ii  gsfonts                               8.14+v8.11+urw-0.2                   F onts for the Ghostscript interpreter(s)
ii  gucharmap                             1.4.4-1ubuntu1                       U nicode character picker and font browser
ii  latex-xft-fonts                       0.1-5                                X ft-compatible versions of some LaTeX fonts
ii  libconsole                            0.2.3dbs-56ubuntu4                   S hared libraries for Linux console and font
ii  libfontconfig1                        2.3.2-1ubuntu1                       g eneric font configuration library (shared l
ii  libfontenc1                           1.0.0-1                              X 11 font encoding library
ii  libfreetype6                          2.1.7-2.4ubuntu1                     F reeType 2 font engine, shared library files
ii  libt1-5                               5.0.2-3                              T ype 1 font rasterizer library - runtime
ii  libxft2                               2.1.7-1ubuntu5                       F reeType-based font drawing library for X
ii  mplayer-fonts                         3.5-2                                F onts for mplayer
ii  msttcorefonts                         1.2ubuntu1                           I nstaller for Microsoft TrueType core fonts
ii  ttf-arabeyes                          1.1-1                                A rabeyes GPL TrueType Arabic fonts
ii  ttf-arphic-bkai00mp                   2.10-6                               " AR PL KaitiM Big5" Chinese TrueType font by
ii  ttf-arphic-bsmi00lp                   2.10-6                               " AR PL Mingti2L Big5" Chinese TrueType font
ii  ttf-arphic-gbsn00lp                   2.11-6                               " AR PL SungtiL GB" Chinese TrueType font by
ii  ttf-arphic-gkai00mp                   2.11-6                               " AR PL KaitiM GB" Chinese TrueType font by A
ii  ttf-baekmuk                           2.2-1ubuntu1                         B aekmuk series TrueType fonts
ii  ttf-bengali-fonts                     0.4.4ubuntu2                         F ree TrueType fonts for the Bengali language
ii  ttf-devanagari-fonts                  0.4.4ubuntu2                         F ree TrueType fonts for languages using the
ii  ttf-freefont                          20031008-1.1ubuntu1                  F reefont Serif, Sans and Mono Truetype fonts
ii  ttf-gujarati-fonts                    0.4.4ubuntu2                         F ree TrueType fonts for the Gujarati languag
ii  ttf-indic-fonts                       0.4.4ubuntu2                         M etapackage for free Indian language fonts
ii  ttf-kannada-fonts                     0.4.4ubuntu2                         F ree TrueType fonts for the Kannada language
ii  ttf-kochi-gothic                      1.0.20030809-3                       K ochi Subst Gothic Japanese TrueType font wi
ii  ttf-kochi-mincho                      1.0.20030809-3                       K ochi Subst Mincho Japanese TrueType font wi
ii  ttf-malayalam-fonts                   0.4.4ubuntu2                         F ree TrueType fonts for the Malayalam langua
ii  ttf-mgopen                            1.1-1                                M agenta Open Truetype fonts
ii  ttf-opensymbol                        1.9.129-0.1ubuntu2                   T he OpenSymbol TrueType font
ii  ttf-oriya-fonts                       0.4.4ubuntu2                         F ree TrueType fonts for the Oriya language
ii  ttf-punjabi-fonts                     0.4.4ubuntu2                         F ree TrueType fonts for the Punjabi language
ii  ttf-tamil-fonts                       0.4.4ubuntu2                         F ree TrueType fonts for the Tamil language
ii  ttf-telugu-fonts                      0.4.4ubuntu2                         F ree TrueType fonts for the Telugu language
ii  x-ttcidfont-conf                      17ubuntu2                            C onfigure TrueType and CID fonts for X
ii  xfonts-100dpi                         6.8.2.1-3                            1 00 dpi fonts for X
ii  xfonts-75dpi                          6.8.2.1-3                            7 5 dpi fonts for X
ii  xfonts-base                           6.8.2.1-3                            s tandard fonts for X
ii  xfonts-scalable                       6.8.2.1-3                            s calable fonts for X
ii  xfonts-utils                          6.8.2.1-3                            u tilities for X font packages
ii  xfontsel                              0.99.0-1                             X  client - xfontsel
ii  xlsfonts                              0.99.0-1                             X  client - xlsfonts

The packages I have that you don't:

ii  gsfonts                               8.14+v8.11+urw-0.2                   F onts for the Ghostscript interpreter(s)
ii  gucharmap                             1.4.4-1ubuntu1                       U nicode character picker and font browser
ii  libfontenc1                           1.0.0-1                              X 11 font encoding library
ii  libt1-5                               5.0.2-3                              T ype 1 font rasterizer library - runtime
ii  mplayer-fonts                         3.5-2                                F onts for mplayer
ii  msttcorefonts                         1.2ubuntu1                           I nstaller for Microsoft TrueType core fonts
ii  ttf-arabeyes                          1.1-1                                A rabeyes GPL TrueType Arabic fonts
ii  ttf-arphic-bkai00mp                   2.10-6                               " AR PL KaitiM Big5" Chinese TrueType font by
ii  ttf-arphic-bsmi00lp                   2.10-6                               " AR PL Mingti2L Big5" Chinese TrueType font
ii  ttf-arphic-gbsn00lp                   2.11-6                               " AR PL SungtiL GB" Chinese TrueType font by
ii  ttf-arphic-gkai00mp                   2.11-6                               " AR PL KaitiM GB" Chinese TrueType font by A
ii  ttf-baekmuk                           2.2-1ubuntu1                         B aekmuk series TrueType fonts
ii  ttf-bengali-fonts                     0.4.4ubuntu2                         F ree TrueType fonts for the Bengali language
ii  ttf-devanagari-fonts                  0.4.4ubuntu2                         F ree TrueType fonts for languages using the
ii  ttf-freefont                          20031008-1.1ubuntu1                  F reefont Serif, Sans and Mono Truetype fonts
ii  ttf-gujarati-fonts                    0.4.4ubuntu2                         F ree TrueType fonts for the Gujarati languag
ii  ttf-indic-fonts                       0.4.4ubuntu2                         M etapackage for free Indian language fonts
ii  ttf-kannada-fonts                     0.4.4ubuntu2                         F ree TrueType fonts for the Kannada language
ii  ttf-kochi-gothic                      1.0.20030809-3                       K ochi Subst Gothic Japanese TrueType font wi
ii  ttf-kochi-mincho                      1.0.20030809-3                       K ochi Subst Mincho Japanese TrueType font wi
ii  ttf-malayalam-fonts                   0.4.4ubuntu2                         F ree TrueType fonts for the Malayalam langua
ii  ttf-mgopen                            1.1-1                                M agenta Open Truetype fonts
ii  ttf-oriya-fonts                       0.4.4ubuntu2                         F ree TrueType fonts for the Oriya language
ii  ttf-punjabi-fonts                     0.4.4ubuntu2                         F ree TrueType fonts for the Punjabi language
ii  ttf-tamil-fonts                       0.4.4ubuntu2                         F ree TrueType fonts for the Tamil language
ii  ttf-telugu-fonts                      0.4.4ubuntu2                         F ree TrueType fonts for the Telugu language
ii  x-ttcidfont-conf                      17ubuntu2                            C onfigure TrueType and CID fonts for X
ii  xfonts-utils                          6.8.2.1-3                            u tilities for X font packages
ii  xfontsel                              0.99.0-1                             X  client - xfontsel
ii  xlsfonts                              0.99.0-1                             X  client - xlsfonts

BTW, I have no idea why I have some of those TTFs as I only read English and a little German ^_^;  Excluding those, we have:

ii  gsfonts                               8.14+v8.11+urw-0.2                   F onts for the Ghostscript interpreter(s)
ii  gucharmap                             1.4.4-1ubuntu1                       U nicode character picker and font browser
ii  libfontenc1                           1.0.0-1                              X 11 font encoding library
ii  libt1-5                               5.0.2-3                              T ype 1 font rasterizer library - runtime
ii  mplayer-fonts                         3.5-2                                F onts for mplayer
ii  msttcorefonts                         1.2ubuntu1                           I nstaller for Microsoft TrueType core fonts
ii  ttf-freefont                          20031008-1.1ubuntu1                  F reefont Serif, Sans and Mono Truetype fonts
ii  ttf-mgopen                            1.1-1                                M agenta Open Truetype fonts
ii  x-ttcidfont-conf                      17ubuntu2                            C onfigure TrueType and CID fonts for X
ii  xfonts-utils                          6.8.2.1-3                            u tilities for X font packages
ii  xfontsel                              0.99.0-1                             X  client - xfontsel
ii  xlsfonts                              0.99.0-1                             X  client - xlsfonts

Hope that helps...

---

### Post by Joloc on 2005-09-29
Yes it did! :)

Thanks a lot.

For any other people suffering from the same problem, above is a package list of font packages you want installed. I'm sure you only need one of them for it to work, but I'm not sure which one.

Just sudo apt-get install them (or use synaptic) and Firefox will like you!

---

### Post by kmiller on 2006-04-27
Hi!

In your post you said that there is a package for Slackware, that solves the problem. Could you please tell me which one it is?
I'm trying since days to make my firefox showing cyrillic web pages correctly, but I just can't find it out!

Thanks lot

Konstantin

[QUOTE=Joloc]Yes, I am sure I do not just need to tweak the settings. When the wrong encoding is selected characters come out looking wrong, but are usually proper characters, just look like [http://en.wikipedia.org/wiki/Image:Letter_to_Russia_with_krokozyabry.jpg]("http://en.wikipedia.org/wiki/Image:Letter_to_Russia_with_krokozyabry.jpg")

Are you sure you get proper characters that look like [http://www.friends-partners.org/oldfriends/language/russian-alphabet.html]("http://www.friends-partners.org/oldfriends/language/russian-alphabet.html")
?
When Cyrillic (KOI8-R) is selected with mail.ru I get characters that say 043F 043E 0447 0442 0430, 043D 043E... in little squares. Whilst I can get out a character map and work out what the letters mean it is not very practical.

IIRC in Slackware the problem was fixed by installing an extra Slackware package. What is the Ubuntu equivalent?[/QUOTE]

---

### Post by Joloc on 2007-03-04
Heh, me mentioning Slackware probably told Google to direct everyone here.

OK, so for Slackware systems, first of all, [SIZE=3]there is a cyrillic fonts package in slackware/x/ , it will work for many of the websites.

Some web designers use strange fonts or specify fonts incorrectly, and in those cases you want 
[http://www.linuxpackages.net/pkg_details.php?id=9788](http://www.linuxpackages.net/pkg_details.php?id=9788)
[/SIZE]

---

