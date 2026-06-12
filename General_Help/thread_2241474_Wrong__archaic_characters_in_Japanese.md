---
title: "Wrong / archaic characters in Japanese"
date: 2014-08-26
forum: General Help
---

### Post by nanosecond2 on 2014-08-26
Hi,

this question was asked before, but I didn't found a solution.
I can't display the correct version of the word &#12379;&#12435;&#12426;&#12423;&#12358;&#12288;&#21344;&#38936;.
The last character is wrong. 
I allready installed font-vlgothic, ttf-kochi-mincho and ttf-kochi-gothic.
I also use the IBUS + Anthy input method.
What else can I do?

Thanks for your help!
Steffen

---

### Post by nanosecond2 on 2014-08-26
I solved it!

I put the following to my home folder file ".fonts.conf"

<?xml version="1.0"?>
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
 <bool>true</bool>
 </edit>
 </match>
</fontconfig>

---

