---
title: "[SOLVED] ugly kanji in japanese fonts"
date: 2008-05-19
forum: General Help
---

### Post by ZapalacX on 2008-05-19
So, I updated my fonts.conf to make my j-fonts render sexier. The kana looks absolutely gorgeous. The kanji are still ugly as sin, however. Anybody else having problems with this? A fix perhaps? Thanks a million in advance.

---

### Post by ZapalacX on 2008-05-20
Here's an example.

---

### Post by ZapalacX on 2008-05-22
nothing, eh?

---

### Post by BandD on 2008-05-23
Is it just in firefox, or other programs as well?

---

### Post by ZapalacX on 2008-05-23
It's also in other programs, like xchat and such. If I'm looking at a japanese site they all render properly, but western sites have the problem. it worked fine in gutsy.

---

### Post by Zorael on 2008-05-23
Tagging for interest, this irks me as well. It's like common kanji and kana are antialiased, even ending up fuzzy at times, where others are knife-sharp and pixely. I'd rather have them all pixely if the alternative is the fuzziness.

---

### Post by chinchilla2392 on 2008-05-23
i know what you mean
katakana, hiragana look good and smooth
but kanji/hanja look awful and pixelated

i dont think theres a fix. unfortunately

---

### Post by gsmanners on 2008-05-23
I'm not sure why, but it looks like two different fonts there:

---

### Post by Zorael on 2008-05-23
May be that *some* and not all cjk fonts are excluded from antialiasing and hinting, and that it somehow accesses one such font for the non super-common kanji and kana?

---

### Post by ZapalacX on 2008-05-23
Japanese encoded sites look fine...it's weird.

---

### Post by Zorael on 2008-05-23
Conjecture:

I *think* it has to do with the western font not having enough unicode characters. On Western pages it'll load the standard font (sans-serif, DejaVu Sans, or whatever you've set it up to use). DejaVu Sans, for instance, has some ~5k characters, which doesn't cover everything. Arial Unicode MS has 38k (according to [http://en.wikipedia.org/wiki/Unicode_typefaces](http://en.wikipedia.org/wiki/Unicode_typefaces)).

Try typing some kanji in DejaVu Sans and then convert it to Arial Unicode MS (if you have the msttcorefonts package installed). The difference is obvious. Having Arial Unicode as your standard font in your whole desktop environment makes things crazy ugly though.

Is it possible to change which font it defaults to when a unicode character is missing from the given font? So that when it realizes DejaVu Sans is missing stuff it'll show the Arial Unicode ones instead of whatever it's showing now (that's obviously not getting antialiased and hinted).

---

### Post by ZapalacX on 2008-05-23
I've tried several different fonts in my western section all to no avail. :confused:

---

### Post by Zorael on 2008-05-23
If I change the standard font to Arial Unicode MS then google pages show up fine, not at all like in your screenshot. I also set the default character encoding to Unicode UTF-8.

What we want to find out is *where* you define which font to it falls back to when the current font lacks a given unicode character. Then we can set that to Arial Unicode MS (for instance) and use DejaVu Sans, sans-serif or whatever we want.


edit: see attachment

---

### Post by ZapalacX on 2008-05-23
I don't have arial unicode MS in my MSTT folder. Any idea where to find it? I wonder what changed between hardy and gutsy to cause them to render so poorly.

---

### Post by Zorael on 2008-05-23
Package name is [FONT="Courier New"]msttcorefonts[/FONT], it's not free-as-in-freedom though. And the truetype rendering is constantly under development as well, I guess, so it's not too surprising stuff gets changed.

I wouldn't mind the sharp fonts much if it weren't for the dots getting misplaced. See screenie. (That's DejaVu Mono and not Arial Unicode.)

It seems like it's switching between two fonts, and only one of them gets antialiased.

edit: And doh, I see I wrote &#24185;&#20107; in my haste instead of &#28450;&#23383;, heh. Well, it's 01:30 so I guess I'm sort of excused.

---

### Post by ZapalacX on 2008-05-23
Yeah, I have msttcorefonts, though only arial is there, not arial unicode. Anyway, I'll keep playing with it. I appreciate the help.

---

### Post by Zorael on 2008-05-23
See [http://ph.ubuntuforums.com/showthread.php?t=684469](http://ph.ubuntuforums.com/showthread.php?t=684469), looks very interesting.
```
So, save the file and reboot xwindows (CTLR+ALT+Backspace). Now with any luck the order of fonts should have been updated so that the default Japanese type face is actually a clean one first and foremost instead of the ugly first serving. Also it disables the built in bitmap font which can really make kanji's look odd next to anti aliased hiragana etc. For most people this setting will be fine. If you're not happy, by all means leave out the embeddedbitmap setting.
```
That sounds like exactly what we want to do.


I'll try it tomorrow, getting way too tired now (02:08). Let me know if you tried it and it worked.

---

### Post by ZapalacX on 2008-05-23
It works, but it changes all the other fonts, making them look worse in my opinion. It seems I'm just going to have to live with it. It's really frustrating to me, as i look at jp sites quite often. I want my gutsy rendering back...

---

### Post by tacutu on 2008-05-24
I don't use the Sazanami fonts. Instead, I installed the MS fonts Gothic and Mincho (from the windows partition --- they made my buy Vista, d'oh!) and everything renders nice. So if you have a Japanese Windows available, you might want to try that.

Of course, this is not a real solution, but maybe it helps.

---

### Post by Zorael on 2008-05-24
> **ZapalacX said:**
> It works, but it changes all the other fonts, making them look worse in my opinion. It seems I'm just going to have to live with it. It's really frustrating to me, as i look at jp sites quite often. I want my gutsy rendering back...
It works for me now, even in other programs. I modified that .fonts.conf file and put my preferred font (DejaVu Sans) up top, so no fonts changed for me. Of course, the kanji font did; that was the whole purpose of it.
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>


 <alias>
 <family>serif</family>
 <prefer>
 <family>DejaVu Serif</family>
 <family>Times New Roman</family>
 <family>&#65325;&#65331; &#26126;&#26397;</family>
 <family>IPAPMincho</family>
 <family>Sazanami Mincho</family>
 <family>Kochi Mincho</family>
 <family>Bitstream Vera Serif</family>
 <family>Thorndale AMT</family>
 <family>Luxi Serif</family>
 <family>Nimbus Roman No9 L</family>
 <family>Times</family>
 <family>Frank Ruehl</family>
 <family>MgOpen Canonica</family>
 <family>AR PL SungtiL GB</family>
 <family>AR PL Mingti2L Big5</family>
 <family>FreeSerif</family>
 <family>Baekmuk Batang</family>
 </prefer>
 </alias>
 <alias>
 <family>sans-serif</family>
 <prefer>
 <family>DejaVu Sans</family>
 <family>Verdana</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAPGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>Bitstream Vera Sans</family>
 <family>Arial</family>
 <family>Albany AMT</family>
 <family>Luxi Sans</family>
 <family>Nimbus Sans L</family>
 <family>Helvetica</family>
 <family>Nachlieli</family>
 <family>MgOpen Moderna</family>
 <family>AR PL KaitiM GB</family>
 <family>AR PL KaitiM Big5</family>
 <family>FreeSans</family>
 <family>Baekmuk Dotum</family>
 <family>SimSun</family>
 </prefer>
 </alias>
 <alias>
 <family>monospace</family>
 <prefer>
 <family>DejaVu Sans Mono</family>
 <family>Courier New</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>Bitstream Vera Sans Mono</family>
 <family>Andale Mono</family>
 <family>Cumberland AMT</family>
 <family>Luxi Mono</family>
 <family>Nimbus Mono L</family>
 <family>Courier</family>
 <family>Miriam Mono</family>
 <family>FreeMono</family>
 <family>AR PL KaitiM GB</family>
 <family>Baekmuk Dotum</family>
 </prefer>
 </alias>
 <match target="font" >
 <edit mode="assign" name="embeddedbitmap" >
 <bool>false</bool>
 </edit>
 </match>


 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```
Move the &#65325;&#65331; &#12468;&#12471;&#12483;&#12463; font farther down and move up another unicode font if you want it to become the kanji standard. I'm going to try it with that Arial Unicode font later.

edit: Setting Arial Unicode as the standard font in Firefox made it work on all non-Japanese-encoded pages, so you could try something similar with Sazanami or similar.


Send me a PM with contact information if you want me to, uh, smurf you that Arial Unicode.

---

### Post by gsmanners on 2008-05-24
Also note that:

gksudo gedit ~/.fonts.conf

Should actually be:

gedit ~/.fonts.conf

That file doesn't really need to be owned by root.

---

### Post by Zorael on 2008-05-24
Test to see how it looks: &#12394;&#12395;&#12396;&#12397;&#12398;&#12290;&#39640;&#25152;&#24656;&#24598;&#30151;&#12290;


Okay. My final [FONT="Courier New"]~/.fonts.conf[/FONT] looks like the following:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

 <alias>
 <family>serif</family>
 <prefer>
 <family>DejaVu Serif</family>
 <family>Sazanami Mincho</family>
 <family>Arial Unicode MS</family>
 </prefer>
 </alias>

 <alias>
 <family>sans-serif</family>
 <prefer>
 <family>DejaVu Sans</family>
 <family>Sazanami Gothic</family>
 <family>Arial Unicode MS</family>
 </prefer>
 </alias>

 <alias>
 <family>monospace</family>
 <prefer>
 <family>DejaVu Sans Mono</family>
 <family>Sazanami Gothic</family>
 <family>Arial Unicode MS</family>
 </prefer>
 </alias>

 <match target="font" >
 <edit mode="assign" name="embeddedbitmap" >
 <bool>false</bool>
 </edit>
 </match>

 <match target="font" >
  <edit mode="assign" name="rgba" >
   <const>rgb</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintfull</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="antialias" >
   <bool>true</bool>
  </edit>
 </match>
</fontconfig>
```

Like so. Full hinting, antialiasing enabled, subpixel rendering: rgb, bitmap fonts disabled. The primary font is DejaVu Serif for serif, DejaVu Sans for sans-serif and DejaVu Mono for monospace.

**Think of serif, sans-serif and monospace as virtual fonts;** picking them in Firefox or any other program will make it go through that priority order in [FONT="Courier New"]fonts.conf[/FONT]. Meaning in my case; it'll first try the DejaVu font. If a given character is missing, it'll try Sazanami. If it's missing in there too, it'll try Arial Unicode. Monospaced kanji will likely look weird, since I don't think Sazanami nor Arial Unicode are monospaced. Kana look slightly different from kanji (since they're DejaVu Sans instead of Sazanami), but this is only on western encoded pages; Japanese ones look great. But then, they always did. Even if you don't have Arial Unicode, you're likely well enough off with Sazanami or similar. Setting default encoding in Firefox doesn't seem to matter.

Grab some more Japanese unicode fonts here: [http://www.wazu.jp/gallery/Fonts_Japanese.html](http://www.wazu.jp/gallery/Fonts_Japanese.html). There's also a package in the repositories named **ttf-mikachan**, which has a handwritten-ish look. It suits documents more than browsers though; you need bigger font size to make out what the characters are.


See attached screenie for my settings. Those are along with the [FONT="Courier New"].fonts.conf[/FONT] file supplied above.

---

### Post by ZapalacX on 2008-05-24
That works for me! I just changed Sazanami to my preferred JP font. Thanks alot everyone.

---

### Post by ryukent on 2008-05-30
For a complete solution (Hardy) please see:

[http://ubuntuforums.org/showthread.php?t=812552](http://ubuntuforums.org/showthread.php?t=812552)

The reason your fonts look strange is that your font setup is using a combination of bitmap and vector rendered fonts.

The solution, as detailed in the above post, is to install the Ricoh fonts which contain a superior bitmap set (compared to Ubuntu defaults), then setup your font ordering to draw characters from the font files in the correct order. Finally you need to turn bitmapping on.

Most Japanese characters cannot be rendered as vectors correctly at very small sizes. This is because there simple aren't enough pixels to show all the strokes. This is usually rectified by using alternative bitmaps that actually miss out some strokes and stop antialiasing so as to improve readability. This approach is adopted by Windows and MacOS. Decent Japanese true type fonts contain a mix of vectors and bitmaps (at common small sizes) in order to achieve this affect. It's commonly accepted that readability takes preference over actual shapes. If you own a Japanese mobile phone you'll be used to it.

As for the other fonts on your system looking strange, if you follow the above guide and make sure that autohinting is off (was good for previous versions of Ubuntu but not hardy), you should achieve the desired effect.

Any queries, please ask. Good looking Japanese fonts are not a luxury, they are essential!!!!!!!!

---

