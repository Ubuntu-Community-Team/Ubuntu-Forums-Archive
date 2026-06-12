---
title: "looking for a music player"
date: 2005-10-04
forum: General Help
---

### Post by IdoMcFly on 2005-10-04
I've tried xmms, bmp, rythmbox and mpd and all of them have their strength but now I'm looking for my ultimate music player.

I need:
[LIST]
[*]many format support (mod, s3m, ogg, mp3, flac, musepack...)
[*]global key control (don't need to focus on the player to play/stop/pause/next...)
[*]playlist with a quick search like xmms
[*]quick queuing like xmms (select an item then hit 'q', it will play this track next then continue like nothing happened)
[*]ability to affect the file within the playlist (tag, delete the file from disk...)
[*]GTK2 integration
[*]crossfade when pausing/stoping
[/LIST]

xmms does it all but the GTK2 part and it is quite buggy for me
mpd does it all but the quick queuing and affecting the file from the playlist
rythmbox don't have global key

so I'm looking for another player to try :)

thanks!

---

### Post by claus on 2005-10-04
[QUOTE=IdoMcFly]I've tried xmms, bmp, rythmbox and mpd and all of them have their strength but now I'm looking for my ultimate music player.
I need:
[LIST]
[*]many format support (mod, s3m, ogg, mp3, flac, musepack...)
[*]global key control (don't need to focus on the player to play/stop/pause/next...)
[*]playlist with a quick search like xmms
[*]quick queuing like xmms (select an item then hit 'q', it will play this track next then continue like nothing happened)
[*]ability to affect the file within the playlist (tag, delete the file from disk...)
[*]GTK2 integration
[*]crossfade when pausing/stoping
[/LIST]
xmms does it all but the GTK2 part and it is quite buggy for me
mpd does it all but the quick queuing and affecting the file from the playlist
rythmbox don't have global key
so I'm looking for another player to try :)
thanks![/QUOTE]
What about 'VLC for GTK+'? Did you try this one already? It's included in the repositories. It even plays WindowsMedia files.
> 'mod'
Should this read '.mov' (Macromedia Quicktime)? This is
unfortunately not included. I'm still looking to get .mov's
running on Ubuntu myself! There*is* some package available,
but it didn't really work on my PC (yet).
Claus

---

### Post by Zotova on 2005-10-04
Have you tried BMP (Beep Media Player) - it is very similar to xmms but I personally find it to be a lot more stable and reliable than when I tried xmms - it also comes with some nice ubuntu skins if you are looking for a integrated look and feel.

I don't know however if it supports all the formats you need but it is worth a try.

---

### Post by kayas80 on 2005-10-04
You should try Amarok. I'm really fussy with media players, i've tried them all, and for me it's leaps and bounds ahead of the others.

---

### Post by MGajh on 2005-10-04
... or perhaps try Banshee

---

### Post by nkrust on 2005-10-04
[QUOTE=kayas80]You should try Amarok. I'm really fussy with media players, i've tried them all, and for me it's leaps and bounds ahead of the others.[/QUOTE]

is there any place where i may find it as a single package rather than a multitude of packages. does it run on gnome, coz the site reads amarok.kde

---

### Post by kayas80 on 2005-10-04
[QUOTE=nkrust]is there any place where i may find it as a single package rather than a multitude of packages. does it run on gnome, coz the site reads amarok.kde[/QUOTE]

Yes it runs on gnome with no problems.

---

### Post by Pettman on 2005-10-04
[QUOTE=claus]What about 'VLC for GTK+'? Did you try this one already? It's included in the repositories. It even plays WindowsMedia files.
> 'mod'
Should this read '.mov' (Macromedia Quicktime)? This is
unfortunately not included. I'm still looking to get .mov's
running on Ubuntu myself! There*is* some package available,
but it didn't really work on my PC (yet).
Claus[/QUOTE]
Have you tried MPlayer?

---

### Post by IdoMcFly on 2005-10-04
thanks all for the answer :) I like mpd very much, I'm just looking for a way to found the file on my disk when I need to delete one.

---

### Post by kayas80 on 2005-10-04
[QUOTE=IdoMcFly]thanks all for the answer :) I like mpd very much, I'm just looking for a way to found the file on my disk when I need to delete one.[/QUOTE]

I'm afraid I once once again have to  suggest Amarok!!

---

### Post by IdoMcFly on 2005-10-05
found out a way to get the file path :)
gmpc 0.12 provide the information relative to the root directory we provided.
we can also get the information with the mpc client
```
mpc --format %file%
```

---

### Post by nkrust on 2005-10-05
[QUOTE=MGajh]... or perhaps try Banshee[/QUOTE]
can i get Banshee as one single deb package, if yes where

---

### Post by doclivingston on 2005-10-05
[QUOTE=nkrust]can i get Banshee as one single deb package, if yes where[/QUOTE]

Banshee is in universe in breezy. You're not going to be able to install it on Hoary, due to the required dependencies - in particular HAL >= 0.5.2.

---

### Post by nkrust on 2005-10-05
[QUOTE=doclivingston]Banshee is in universe in breezy. You're not going to be able to install it on Hoary, due to the required dependencies - in particular HAL >= 0.5.2.[/QUOTE]


can u suggest a music and movie player that i might be able to download as a single debian package, if yes where.

---

