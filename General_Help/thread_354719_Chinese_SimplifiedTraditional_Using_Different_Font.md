---
title: "Chinese Simplified/Traditional Using Different Fonts"
date: 2007-02-06
forum: General Help
---

### Post by ushaba on 2007-02-06
I've read all the how-tos and whatnot on Chinese fonts here, and even though my Chinese is good, spending eight hours on the Chinese forums with a dictionary may be a bit above my level. I'm noticing that while typing in Chinese using scim under fluxbox/ubuntu, the fonts generally change when there is a switch from a character whcih is the same in simplified and traditional, this is the straight zenkai font, i think, to a sort of italicized font when a simplified character appears. for instance, if I were to type "Wo3 he2 ta1 yi2 yang4 cong1 ming2" I'd get &#25105;&#21644;&#20182;&#19968;&#26679;&#32874;&#26126;. On my screen, "yang4" and "cong1" appear in the weird ugly italicized font. I noticed that ayisu and others who claimed to have no problems with chinese fonts were using only traditional characters, so I imagine this is a problem with simplified character input, and possibly with input using pinyin.

If I could find a way to only type traditional characters using pinyin, I would gladly do so, if it would make everything readable, but at present I prefer pinyin as my common input method. I noticed the local.conf suggestion given by some users, but when I tried that I just got syntax errors, and at this point, since the problem is not one of font preference so much as switching of fonts between traditional and simplified characters, I'm not sure changing local.conf would help at all either. 

If anyone has successfully managed to get *simplified* characters displaying correctly, please let me know. Ideally I'd be able to get both working, but I've looked through all these how-tos about fonts online and here and I'm pretty confused now as to what could actually be causing this to happen. Does the system treat Traditional Chinese and Simplified Chinese as separate languages entirely? Where are the configuration files that specify which language environment uses which font? 

I am using scim, fluxbox (built from source), ubuntu 6.10 edgy (with most of the gnome stuff removed). I noticed that controlling applications works very differently depending on the types of apps too. If someone knows how to get GTK apps working, for instance, using text files, that information will be welcome. Right now trying to type in open office, gaim, on firefox, in abiword, etc. produces interesting results. Also, applications such as gaim display a mixture of "i don't understand Chinese" square boxes and strange symbols for the titles, as does firefox (GTK problem??).

---

### Post by ushaba on 2007-02-08
i wasn't aware that scim allows me to use pinyin to type traditional characters, but that part is solved at least. i am still unsure why the fonts change when i use traditional characters though. i'm not sure if scim thinks that the encoding is changing when it views a character in simplified form after viewing several which have the same form in both traditional and simplified characters. basically, i don't know if this is a flaw with a) the fonts i'm using; b) scim, c) my font configuration in fonts.conf. 

again if anyone has managed to get *simplified* characters looking ok in ubuntu, let me know.

---

### Post by ushaba on 2007-02-08
problem temporarily solved by making all fonts the same... but i'm mostly curious why the problem exists in the first place?

---

### Post by precinto on 2007-03-04
How did you make all the fonts the same? I'm having the same problem. Although I like better the simplified ones style.

About searching forums with a dictionary you'd better off install Chinese Perakun extension for Firefox. It's a popup dictionary of Chinese. It's really useful for exploring the net and for learning.

---

### Post by JcZndeR on 2007-06-06
mine used to do that too..
i think i fixed by changing the system wide fonts while using gnome
i followed these instructions below and added the AR PL ZenKai Uni font (it makes them all cursivey, u can change to another one)
[http://ubuntuforums.org/showthread.php?t=338991](http://ubuntuforums.org/showthread.php?t=338991)
i dunno whether this actually has an effect on firefox or if i just got lucky =P
i also changed the language font settings in firefox which didnt seem to help

---

### Post by wth_china on 2007-06-27
I think you need install chinese font.

Ubuntu&#65306; 
1
sudo apt-get install language-pack-zh

2
&#37197;&#32622;&#23383;&#20307;&#65292;&#20351;&#20013;&#25991;&#30475;&#36215;&#26469;&#26356;&#28418;&#20142;&#65288;&#21487;&#36873;&#65289; 
sudo fontconfig-voodoo -f -s zh_CN

3
scim&#36755;&#20837;&#27861;&#23433;&#35013;&#21450;&#35774;&#32622;
&#22914;&#26524;&#24744;&#35201;&#22312;&#38750;CJK&#65288;&#20013;&#26085;&#38889;&#65289;&#30340;locales&#19979;&#20351;&#29992;scim,&#35831;&#22312;&#32456;&#31471;&#25191;&#34892;&#22914;&#19979;&#21629;&#20196;&#65288;&#22914;&#26524;&#40664;&#35748;&#26159;&#20013;&#25991;&#29615;&#22659;&#19981;&#38656;&#35201;&#36825;&#19968;&#27493;,&#31995;&#32479;&#24050;&#32463;&#35774;&#32622;&#22909;&#20102;&#65289;&#65306; 
sudo apt-get install scim scim-modules-socket scim-modules-table scim-pinyin scim-tables-zh scim-gtk2-immodule im-switch libapt-pkg-perl
sudo im-switch -s scim -z default

---

