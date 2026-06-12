---
title: "Banshee Cover Art"
date: 2006-12-22
forum: General Help
---

### Post by jhuff on 2006-12-22
Does anyone know how to change the cover art that Banshee selects?  I have an album that the wrong cover is selected.

---

### Post by wilko10 on 2006-12-23
I get a similar problem sometimes. I wish I knew where it got it from.

Sometimes an obscure track, also on a popular compilation album displays the compilation Art eg "Dark side of the 80's"

I dont know why it wont use embedded art if it has it as a first. The bashee site is no use here. either.

Lets hope someone can tell us which site it comes from.

J

---

### Post by aidanr on 2006-12-23
you can put cover.jpg or folder.jpg in the albums directory and then banshee should use that instead of what it finds on the net

---

### Post by wilko10 on 2006-12-23
Thanks for the info about dropping the artwork into the folders.
However this has got me curious, I ran the firestarter firewall and monitored the urls banshee went to these are

72.29.166.157 which is [http://musicbrainz.org/](http://musicbrainz.org/) this seems to get mp3 tags
84.53.134.16 which says is invalid-is the site down or does it maybe not respond to a web browser.
87.117.229.100 which is [http://www.last.fm/dashboard/](http://www.last.fm/dashboard/)  is this because I have LastFm enabled for audioscrobbler.

However I am still not sure which of this,if any, is picking up cover art for missing album art.

The banshee website isn't any help 

Can anyone decipher this further?

Nicki

---

### Post by wilko10 on 2006-12-29
Right,
it is definatley musicbrainz.org that provides the data and gets it wrong.

You can add their program to your system, called picard, that allows you to correctly tag your songs/albums but more importantly, help them fix errors.

also there is test code in banshee .113 / .114 that reads cover art out of the song ala Itunes.

Once banshes tag editor allows adding cover art, it will be enabled as the default, followed by the folder.jpg as second choice, then musicbrainz as the final choice.

Looks like we need to give it 6 months ?

Jeff

---

