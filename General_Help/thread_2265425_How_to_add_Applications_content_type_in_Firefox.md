---
title: "How to add Applications content type in Firefox"
date: 2015-02-15
forum: General Help
---

### Post by monkeybrain20122 on 2015-02-15
Hi, I come across some potcast links of the type itpc (itune I suppose). When clicking these links in Firefox it displays an error saying Firefox doesn't know what to do. I realise I can add an entry to Edit > Preferences > Applications if I install Clementine. After that if I click the link a dialogue box would pop up asking what to do. Now I have removed clementine and I can open these links with vlc. I am sure there is a better way to achieve this without having to install and remove clementine first. what is the recommended way to do this?

Thanks.

---

### Post by dragonfly41 on 2015-02-15
To inspect content type of your links you could install

Live HTTP Headers add-on in Firefox.

[https://addons.mozilla.org/en-US/firefox/addon/live-http-headers/](https://addons.mozilla.org/en-US/firefox/addon/live-http-headers/)

and here is one video clip explaining its use for sniffing 

[https://www.youtube.com/watch?v=zscdslE1yb0](https://www.youtube.com/watch?v=zscdslE1yb0)

---

### Post by mc4man on 2015-02-15
Maybe because clementine registers x-scheme-handler/itpc
(haven't seen any of these links so can't say if you can simply add

---

### Post by monkeybrain20122 on 2015-02-15
> **mc4man said:**
> Maybe because clementine registers x-scheme-handler/itpc
(haven't seen any of these links so can't say if you can simply add

Is there a way to add that by hand?

My Firefox preferences now look like screenshot (see the added itpc entry) after installing and removing clementine.

---

### Post by mc4man on 2015-02-15
> **monkeybrain20122 said:**
> Is there a way to add that by hand?

My Firefox preferences now look like screenshot (see the added itpc entry) after installing and removing clementine.
I don't think simply making an entry in ~/.local/share/applications/mimeapps.list would matter, maybe next time you build vlc add it to vlc.desktop.in (- in source > share) so it's part of the install

Or it could be something else clem does during install to add the mime?, glancing at the clem source I  see  the .desktop has it  & there is "clementine-itpc.protocol"
(both in source > dist), the protocol file may be just for kde, see [http://packages.ubuntu.com/trusty/amd64/clementine/filelist](http://packages.ubuntu.com/trusty/amd64/clementine/filelist)
You could also either extract the clem .deb or open in archive manager > debian > read thru some of the install files..

In general though no way to fool around here as I can't find a suitable link..

---

### Post by monkeybrain20122 on 2015-02-15
Another thing. After removing clementine I made a new FF profile just to test and the itpc entry is gone. So somehow it is registered in FF's profile.  A friend posted the link on Facebook a while ago I just tried it out of curiosity. I will try to dig it up again.

---

### Post by mc4man on 2015-02-15
Maybe just try adding to mimeapps.list, could need a log out or restart
So trust me I don't know nothing here - so after adding to Added section- 
x-scheme-handler/itpc=vlc.desktop;

Decided to make a Desktop link file & see what would happen, as in - 
test.desktop contents of - 
```
[Desktop Entry]
Encoding=UTF-8
Name=Link i don't know
Type=Link
URL=itpc://feeds.feedburner.com/Voice-OverJourney
Icon=text-html
```
clicking on it opened the url directly  in vlc

So then just used itpc://feeds.feedburner.com/Voice-OverJourney in FF's adrress bar & got the screen

---

