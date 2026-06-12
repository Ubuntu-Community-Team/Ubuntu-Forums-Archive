---
title: "(Lubuntu) Youtube is no more working."
date: 2015-09-08
forum: General Help
---

### Post by josjarephoslav on 2015-09-08
After installing Midori, I can not watch anything in Youtube anymore.
Both, on Mozilla and on Midori. This is what happens when I open a link;

[[IMG]http://s5.postimg.org/tk41pck5f/2015_09_09_001832_1024x576_scrot.jpg[/IMG]]("http://postimg.org/image/tk41pck5f/")

I searched this forum, couldn't get any certain solution. Of course,
 I am new. So I need some guidance. I get this and it looks like a solution;


[SIZE=3][I]                         "[SIZE=2]For Youtube or Vimeo, you need WebKitGTK+ 1.1.20 or newer."
[/SIZE][/I][/SIZE]**[FONT=arial]                                         -Midori's Official FAQs Page[/FONT]**[SIZE=3][I][SIZE=2]
[/SIZE][/I][/SIZE]

Okay, I tried hard to find this WebKitGTK thing so I could install it to my
system. I think it is some kind of a plug-in. At the end, I get zero result
for getting the mentioned version of the plug-in for the latest Lubuntu.

For your comfort, I am sharing these infos about my hardware and
software setup with you, by hoping that it will be a door for the 
solution. I think I am missing something somewhere in these infos.

HARDWARE

[[IMG]http://s5.postimg.org/bvcaxq8eb/2015_09_09_001212_1024x576_scrot.jpg[/IMG]]("http://postimg.org/image/bvcaxq8eb/")

SOFTWARE

[[IMG]http://s5.postimg.org/b8de87bib/2015_09_09_001244_1024x576_scrot.jpg[/IMG]]("http://postimg.org/image/b8de87bib/")

Thank you for your time!

---

### Post by kerry_s on 2015-09-08
for midori use html5:
[https://www.youtube.com/html5](https://www.youtube.com/html5)

---

### Post by ventrical on 2015-09-08
One could use ubuntu-restricted-extras from the software center ... uhmmm.. did you try removing midori?

---

### Post by monkeybrain20122 on 2015-09-08
I think you need the package gstreamer1.0-libav to play html5 streams with h264 on Firefox (Vimeo and Youtube, e.g) . Installing Ubuntu-restricted-extras should install it (if not just install it separately)
Not sure about Midori.

---

### Post by josjarephoslav on 2015-09-08
While I was waiting for answers, I kept searching. 
Found a link that sounds similar to my problem.
I tried the same solution method for my problem. 
[COLOR=#ff8c00]It worked![/COLOR] I know, it looks like I needed to do 
HTML5 thing or install the packages you guys 
mentioned but entering these codes step by step 
in terminal fixed it.&#8203;

```
[SIZE=2][FONT=arial narrow]sudo apt-get install flashplugin-installer[/FONT][/SIZE]
```
[SIZE=2][FONT=arial narrow]```
sudo ln -s /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/mozilla/plugins/libflashplayer.so
```
```
sudo apt-get install nspluginwrapper
```
```
nspluginwrapper -v -a -n -i
```
[/FONT][/SIZE]After entering all codes, restart the Midori.

Source:
[http://itsfoss.com/fix-missing-flash-player-error-midori-quick-tip/](http://itsfoss.com/fix-missing-flash-player-error-midori-quick-tip/)
[SIZE=1]

Small Question:

Still, it is out of the topic but 
is flash needs better hardware
 to perform smootly? Or, is HTML5 
a better technology to run on low-end 
hardware? I am still having issues with 
playing videos on Youtube at 240p.[/SIZE]

---

