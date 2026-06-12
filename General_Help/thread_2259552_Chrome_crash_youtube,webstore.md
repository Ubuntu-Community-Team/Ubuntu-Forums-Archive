---
title: "Chrome crash youtube,webstore"
date: 2015-01-05
forum: General Help
---

### Post by FRAGnat on 2015-01-05
[COLOR=#000000]Hello. I have some problem within two month. Previously I had Ubuntu 14.04 and my chromium crashed when the video in youtube is over. Also i have 100% crash when try to open some link in chromium webstore. Two days ago I bought new hard disk (SSD) and install new distributive linux (Linux Mint) but problem is not solved. I didn't copy any files from old system. Also I check my RAM and try to change strap. But it is not solved my problem again. Please help me [/COLOR]

[COLOR=#000000]Result lshw
[/COLOR][ATTACH]259012[/ATTACH][COLOR=#000000]

P.S I read this post and it is not helping to me [/COLOR]http://ubuntuforums.org/showthread.php?t=2247572

---

### Post by kerry_s on 2015-01-05
does it only happen with chromium? tried other browsers?

---

### Post by FRAGnat on 2015-01-05
Yes, I try Mozila Firefox and Mozila didn't crash. But I am a web-developer and I like Chromium. And I don't understand why Chromium crash, because I reinstall system and this didn't help me

---

### Post by kerry_s on 2015-01-05
fair enough.

check: chrome://gpu
make sure acceleration is turned on. i had to do mine manually. ps: i'm using chrome, so same thing, i needed the google extras. :)

---

### Post by FRAGnat on 2015-01-05
acceleration ON
[https://imageshack.com/i/pd7k9rr1p](https://imageshack.com/i/pd7k9rr1p)
acceleration OFF 
[https://imageshack.com/i/f0tCAlQYp](https://imageshack.com/i/f0tCAlQYp)

Try to on/off hardware acceleration don't help solved my problem ;(((

If you need I can give to control my computer. 

And I tried to disabled ALL extensions in my chromium

---

### Post by kerry_s on 2015-01-05
thats not on, they should all be green.

---

### Post by FRAGnat on 2015-01-05
Oh, okay. Thanks for good screenshots. I try to change this param. But the problem is not solved.
[ATTACH=CONFIG]259021[/ATTACH]


P.S I'm sorry if my tone demanding, it is due to poor command of English

---

### Post by kerry_s on 2015-01-05
there's a setting in there for that raster threads, i set mine to 4. just scroll down aways.

okay i'm thinking it's probably the built in flash, go to chrome://plugins & disable Shockwave Flash 16.0 r0
i'm assuming you do have the system flash installed it's version 11

oops, my bag you need pepperflashplugin-nonfree for chromium

instructions:
[http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04)

---

### Post by FRAGnat on 2015-01-05
Sorry, but again it doesn't work. For your advice I disable [COLOR=#000000]Shockwave Flash 16.0 r0. But I had already installed pepperflash and [/COLOR]I did the following steps
1) > [COLOR=#888888]sudo update-pepperflashplugin-nonfree --install

2) [/COLOR]> [COLOR=#888888]sudo gedit /etc/chromium-browser/default[/COLOR][COLOR=#4F4F4F][FONT=Lato]Add the following line at the end on a new line:[/FONT][/COLOR]
. /usr/lib/pepflashplugin-installer/pepflashplayer.sh

---

### Post by kerry_s on 2015-01-05
maybe that version of chromium is just no good?
try this:
[http://www.webupd8.org/2014/02/how-to-install-chromium-beta-or-dev.html](http://www.webupd8.org/2014/02/how-to-install-chromium-beta-or-dev.html)

---

### Post by FRAGnat on 2015-01-05
OMG, It is helping. REALLY. I understood that these was the last attempt, but it is really work (I install beta version). Thank you very much, and give you requisite (I want to donate small thanks).

P.S English community very fast and good, when Russian community very sucks. I know, I need learn the English language, but it is hard ))))

P.S.S Please tell me, how do you know about the councils, which gave

P.S.S.S Why only I have some problem with "stable" version ? And how to find it.

---

### Post by kerry_s on 2015-01-05
lol, screw english i'd rather learn russian. :)

i don't know why just you, everyone does different things, use different add ons, have different hardware. you my friend are just lucky, you found the problems no one else found. lol

---

