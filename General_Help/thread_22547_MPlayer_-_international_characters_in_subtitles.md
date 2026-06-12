---
title: "MPlayer - international characters in subtitles"
date: 2005-03-28
forum: General Help
---

### Post by mich_r on 2005-03-28
Hi all,

I have successfully installed and configured MPlayer media player, following the "RestrictedFormats" wiki topic. My problem is that the international characters ( outside a-z, A-Z ) from subtitles are displayed as "?" or "_", with any encoding I specify in options (I need Central European characters, so I've tried ISO-8859-2, Windows-1250, UTF-8, Unicode, converting the subtitles file to the certain format first of course). 
So I suppose the fonts used by mplayer just doesn't contain needed chacracters. The question is how to change the font, here is what I've tried:

1. started gmplayer
2. click "options" button
3. go to "Font" tab
4. there is a "font" textbox and "browse" button here, I don't know what to enter in the textbox and the "browse" button takes me to the "select file" standard dialog box where I have no idea what should be selected

I think I should notice that I am a linux newbie, this is my first linux workstation I am trying to configure.

Can anybody help me?

Regards
Michal

---

### Post by krtko on 2005-06-20
Hi. I have this in my .mplayer/config:

vo=sdl:x11
fs=yes
#font=/usr/share/mplayer/font-arial-cp1250/font-arial-28-cp1250/font.desc

fontconfig=yes
font="Arial Black"
subfont-encoding=windows-1250
subfont-text-scale =4

---

### Post by FreDeas on 2006-06-29
Hi, I have exactly the same problem.

Neither mplayer or kafeine or any other program displays the correct characters, I've tried what you proposed and the program crashed. In aprevious installation of ubuntu I was able to watch the subtitles correctly, now I can't.

Anybody could help?

---

### Post by yuv on 2006-07-18
Preferences > Subtitles & OSD
Encoding: Slavic/Central European (ISO-8859-2)
Check “Unicode subtitle”

Preferences > Font
than chose Arial
Encoding: Unicode

And wish all the best for clau and visit [http://clau.sparetimegroup.net/index.php/page/2/](http://clau.sparetimegroup.net/index.php/page/2/)
you will enjoy it..I did :)

---

