---
title: "Xmms"
date: 2005-06-06
forum: General Help
---

### Post by mila80 on 2005-06-06
Hi all,
   I have a problem using xmms.
The problem is: when I get start one of this programs is all ok, but when I push start to listen mp3 the background program's interface color became black and all is blocked. I can use other programs, but I can't shout down xmms.

Someone can halp me?
MArco

---

### Post by az on 2005-06-06
1.  try opening a terminal and launching xxms from there.  POst the error messages it makes, if any.

2-  Try beep-media-player.  It is xmms, but better.

---

### Post by lt_kije on 2005-06-06
Have you followed the instructions on this page ([http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)) regarding MP3 playback? Due to copyright and IP restrictions, Ubuntu cannot ship an MP3-capable player by default. XMMS can play MP3s, but needs some helper files to do so.

lt_kije

---

### Post by mila80 on 2005-06-06
[QUOTE=azz]1.  try opening a terminal and launching xxms from there.  POst the error messages it makes, if any.

2-  Try beep-media-player.  It is xmms, but better.[/QUOTE]
 well, no error messages.
the aplication is blocked.

---

### Post by mike998 on 2005-06-06
I might add that you may have xmms using the wrong output plugin.
Open XMMS and right click > preferences > Output plugin.
Try some of the other output plugins.

If xmms freezes totally, in a terminal, try :

ps -ef | grep xmms

Then

Kill <the number in the left hand column>


As a side note, I usually keep the force quit applet handy just in case of misbehaving windows.

---

### Post by bored2k on 2005-06-06
[QUOTE=mila80]well, no error messages.
the aplication is blocked.[/QUOTE]
 Probably something to do with the sound server. 
A) Go to preferences (xmms) and select esound, then retry.
B) In your panel: system > preferences > sounds > disable sound system. Then go to xmms and change your sound to arts or alsa or oss.

---

### Post by az on 2005-06-06
xmms does not require any plugins to play mp3.

---

### Post by mila80 on 2005-06-07
[QUOTE=azz]xmms does not require any plugins to play mp3.[/QUOTE]

Hi, 
  I tryed with Beep media Player, but I have the same problem.

The application is frozen...

How can I do??? 
Marco

---

### Post by christooss on 2005-06-07
I think its freezing because output plugin is set to oss. So set it to esound esd. It works perfectly to me.

---

### Post by ihot on 2005-06-07
thank you so much for all information, i can play XMMS now, coz i set to esound in preference (audio i/o plugin). Thank U!   ;-)

---

### Post by mila80 on 2005-06-07
[QUOTE=christooss]I think its freezing because output plugin is set to oss. So set it to esound esd. It works perfectly to me.[/QUOTE]


All right now!
Thank you!

---

### Post by bored2k on 2005-06-07
I suggest you install beep-media-player. Its much better.

---

### Post by minimidgy on 2005-06-08
I just installed beep and it does the same thing as xmms, it freezes when I hit play

---

### Post by christooss on 2005-06-08
[QUOTE=minimidgy]I just installed beep and it does the same thing as xmms, it freezes when I hit play[/QUOTE]
 DId you changed output plugin from oss to esound?

---

