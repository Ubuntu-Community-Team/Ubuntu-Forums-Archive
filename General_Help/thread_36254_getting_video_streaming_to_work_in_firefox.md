---
title: "getting video streaming to work in firefox"
date: 2005-05-22
forum: General Help
---

### Post by minimidgy on 2005-05-22
I can't figure out how to watch movies that are embedded in webpages.  The only way that I can figure out how to watch these videos is by viewing the page info and then downloading the video. How can I integrate video codecs into Firefox.

Oh and one more thing, Why doesn't apple make a quicktime for linux? It would really help me alot.

---

### Post by f.prisson on 2005-05-22
Have a look at [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) there is a description about installing the mplayer and mplayer plugin for firefox. With this plugin you can also play quicktime movies.

---

### Post by minimidgy on 2005-05-23
[QUOTE=f.prisson]Have a look at [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) there is a description about installing the mplayer and mplayer plugin for firefox. With this plugin you can also play quicktime movies.[/QUOTE]
it always freezes at around 25 percent.

---

### Post by f.prisson on 2005-05-24
I had to edit ```
/etc/mplayerplug-in.conf
``` so that is uses ESD.

---

### Post by mtron on 2005-05-24
i prefer the mediaplayer connectivity add-on for mozilla firefox. it displays a button that launches the needed player automatically when you click on it.

see: [http://www.ubuntuforums.org/showthread.php?t=33107](http://www.ubuntuforums.org/showthread.php?t=33107)

---

### Post by royg1234 on 2005-06-01
I agree w/ using the media player connectivity extension.  (even better than embed, because you can resize video!)

---

### Post by nix4me on 2005-06-01
I use totem-xine with the mozplugger firefox plugin.  Works great.

nix

---

### Post by nyy3321 on 2007-02-14
everytime i try to play a streaming video embedded in firefox, i hear audio for a second and then mplayer reconnects me. I tried this with many streams so i know its not an issue with a particular website i'm recieving the stream from.

I'm using firefox 2.0 with the mplayer plugin with the user agent switcher add-on. i deleted totem and xine and vlc plugins for firefox to prevent any interference.

the video is not flash based, i believe it is a wmf or wmv file.

---

