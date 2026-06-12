---
title: "Prefer Japanese fonts over Chinese ones"
date: 2014-02-23
forum: General Help
---

### Post by kufii on 2014-02-23
As you may or may not know, due to han unification, Chinese and Japanese characters share the same unicode code points. 
By default, Ubuntu displays these characters using a Chinese font. I want to switch it to a Japanese one. Is there any way I can change the order fonts are selected, and put a Japanese one first? Thanks in advance!

---

### Post by llamabr on 2014-02-23
I have no idea, but here's the first hit on google for "ubuntu default font":
[http://askubuntu.com/questions/351595/change-default-font-in-ubuntu-13-04](http://askubuntu.com/questions/351595/change-default-font-in-ubuntu-13-04)

give it a go, and if you get stuck, let us know.

---

### Post by kufii on 2014-02-23
The thing is, I didn't want to change the default font, I wanted to change the fallback font.

Your reply made me think of googling "ubuntu fallback font" though and I found what I was looking for. So thanks!

What I did was edit /etc/fonts/local.conf and set it to prefer Japanese fonts.

If anyone else was having this issue wants the content of my local.conf here it is:
```
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
```

---

