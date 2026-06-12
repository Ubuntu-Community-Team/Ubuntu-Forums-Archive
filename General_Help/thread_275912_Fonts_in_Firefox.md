---
title: "Fonts in Firefox"
date: 2006-10-12
forum: General Help
---

### Post by riksweeney on 2006-10-12
Hi,

I was wondering how I can solve a problem with some of my fonts being aliased in Ubuntu. If you take a look at my attached screenshot, you'll see that all the fonts except for the topic names are anti-aliased. The new Yahoo! Mail is the same, with most of the fonts being aliased.

Does anyone know what I can to fix this problem? I'm using the Microsoft Core Fonts in Firefox.

Thanks

Richard

---

### Post by JonahRowley on 2006-10-12
Some websites absolutely insist on some fonts.  If these fonts are installed, Firefox will use it, but X doesn't antialias all fonts.  I believe you can force them to be antialiased, but they look really blurry and gross (they're not being antialiased for a reason).  I don't really see this on any sites I go to, but when I do, it just doesn't bother me much.  Web developers that have a clue leave the fonts to font families (use a "serif font", not use "times new roman").

---

### Post by ayoli on 2006-10-12
type about:config in firefox url bar, then find this key:

font.FreeType2.enable

turn it to true

---

### Post by riksweeney on 2006-10-12
Thanks guys, I'll give it a try when I get in from work this evening!

Richard

---

### Post by dagnabit dang doohickey on 2006-10-12
Save the following code as .fonts.conf in your Home directory, then log out and log back in.

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

<!-- the cathectic LCD tweaks, from linuxquestions.org,
http://www.linuxquestions.org/questions/showthread.php?postid=1361098#post1361098
-->

<fontconfig>

<!-- Disable sub-pixel rendering. X detects it anyway, and if you set
this as well, it just looks really horrible  -->
<match target="font" >
 <edit mode="assign" name="rgba" >
  <const>none</const>
 </edit>
 </match>
 <match target="font" >
 <edit mode="assign" name="hinting">
  <bool>true</bool>
 </edit>
 </match>
 <match target="font" >
 <edit mode="assign" name="hintstyle">
  <const>hintfull</const>
 </edit>
 </match>

<!-- The first part of the 'magic.' This makes the fonts start to look
nice, but some of the shapes will be distorted, so hinting is needed
still -->
 <match target="font" >
 <edit mode="assign" name="antialias">
  <bool>true</bool>
 </edit>
 </match>

<!-- Autohinter is not turned on automatically. Only disable this if
you have recompiled Freetype with the bytecode interpreter, which is
run automatically. Although to be honest, Freetype are right, there
isn't much difference between the two. Note that OpenOffice is built
against the bytecode interpreter, so even if you have compiled it and
override it with the autohinter, OOo will still use the bytecode
interpreter -->
 <match target="pattern" >
 <edit mode="assign" name="autohint">
  <bool>true</bool>
 </edit>
 </match>

<!-- Helvetica is a non true type font, and will look bad. This
replaces it with whatever is the default sans-serif font -->
 <match target="pattern" name="family" >
 <test name="family" qual="any" >
  <string>Helvetica</string>
 </test>
 <edit mode="assign" name="family" >
  <string>sans-serif</string>
 </edit>
 </match>
 <dir>~/.fonts</dir>
</fontconfig>
```

---

### Post by Irony on 2006-10-12
That's interesting, could I use;

[PHP]about:config[/PHP]

to correct widely spaced fonts which I get on some webpages now that I'm using Microsoft fonts. These widely spaced fonts show up correctly in Opera but in Firefox they have a space between each letter

---

### Post by riksweeney on 2006-10-12
> **dagnabit dang doohickey said:**
> Save the following code as .fonts.conf in your Home directory, then log out and log back in.

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

<!-- the cathectic LCD tweaks, from linuxquestions.org,
http://www.linuxquestions.org/questions/showthread.php?postid=1361098#post1361098
-->

<fontconfig>

<!-- Disable sub-pixel rendering. X detects it anyway, and if you set
this as well, it just looks really horrible  -->
<match target="font" >
 <edit mode="assign" name="rgba" >
  <const>none</const>
 </edit>
 </match>
 <match target="font" >
 <edit mode="assign" name="hinting">
  <bool>true</bool>
 </edit>
 </match>
 <match target="font" >
 <edit mode="assign" name="hintstyle">
  <const>hintfull</const>
 </edit>
 </match>

<!-- The first part of the 'magic.' This makes the fonts start to look
nice, but some of the shapes will be distorted, so hinting is needed
still -->
 <match target="font" >
 <edit mode="assign" name="antialias">
  <bool>true</bool>
 </edit>
 </match>

<!-- Autohinter is not turned on automatically. Only disable this if
you have recompiled Freetype with the bytecode interpreter, which is
run automatically. Although to be honest, Freetype are right, there
isn't much difference between the two. Note that OpenOffice is built
against the bytecode interpreter, so even if you have compiled it and
override it with the autohinter, OOo will still use the bytecode
interpreter -->
 <match target="pattern" >
 <edit mode="assign" name="autohint">
  <bool>true</bool>
 </edit>
 </match>

<!-- Helvetica is a non true type font, and will look bad. This
replaces it with whatever is the default sans-serif font -->
 <match target="pattern" name="family" >
 <test name="family" qual="any" >
  <string>Helvetica</string>
 </test>
 <edit mode="assign" name="family" >
  <string>sans-serif</string>
 </edit>
 </match>
 <dir>~/.fonts</dir>
</fontconfig>
```

Thanks, that worked a treat!

---

