---
title: "Good-looking Japanese fonts and good-looking Chinese fonts: conflict?"
date: 2008-03-09
forum: General Help
---

### Post by FleurDuMal on 2008-03-09
Hello, I apologize in advance if the question sounds stupid or doesn't make much sense, I am a complete newbie with Ubuntu, so please bear with me.

I am running the latest version of Ubuntu, and being a student of both Japanese and Chinese, I needed to install support and input for both languages. After a bit of trouble I did. However, the fonts looked mixed and mismatched, and after finding out that it was a common problem, I found a guide which successfully made the Japanese fonts look alright (that is, only 1 type of font was being used at last).

However, Chinese fonts still looked "mixed", and so I followed another guide to solve the problem. After some trying, it did work alright, but now the Japanese fonts went back to being mixed, and I am wondering if there is an "incompatibility" between having decent-looking fonts for both languages. If not, how could I solve the problem?

In case it helps, this is how my .fonts.conf file looks like:

```
<?xml version="1.0"?>
<fontconfig>
 <alias>
 <family>serif</family>
 <prefer>
 <family>Times New Roman</family>
<family>AR PL UMing CN</family>
<family>AR PL ShanHeiSun Uni</family>
<family>AR PL UKai CN</family>
<family>AR PL ZenKai Uni</family>
 <family>&#65325;&#65331; &#26126;&#26397;</family>
 <family>IPAPMincho</family>
 <family>Sazanami Mincho</family>
 <family>Kochi Mincho</family>
 <family>DejaVu Serif</family>
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
 <family>Verdana</family>
<family>AR PL UMing CN</family>
<family>AR PL ShanHeiSun Uni</family>
<family>AR PL UKai CN</family>
<family>AR PL ZenKai Uni</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAPGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>DejaVu Sans</family>
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
 <family>Courier New</family>
<family>AR PL UMing CN</family>
<family>AR PL ShanHeiSun Uni</family>
<family>WenQuanYi Bitmap Song</family>
<family>AR PL UKai CN</family>
<family>AR PL ZenKai Uni</family>
 <family>&#65325;&#65331; &#12468;&#12471;&#12483;&#12463;</family>
 <family>IPAGothic</family>
 <family>Sazanami Gothic</family>
 <family>Kochi Gothic</family>
 <family>DejaVu Sans Mono</family>
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
```

Thanks in advance.

---

### Post by davarino on 2008-03-10
I assume that you are speaking of the fonts when they are being used in OpenOffice.org. Or are you?

What do you mean by "mixed"? Do you have screenshots? There *are* slightly different renderings between fonts that on the surface seem identical. 

I personally have noticed no problems with either Japanese fonts or Chinese (T or S) either in OO.o or with Firefox. (However, I am running 6.06.)

---

### Post by cbsim on 2008-05-01
I have the same problem with my Hardy too as I can only make either the Chinese font or Japanese font look good but not both.

---

