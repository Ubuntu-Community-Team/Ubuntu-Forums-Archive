---
title: "gtkpod, easytag and mp3 tags"
date: 2005-04-13
forum: General Help
---

### Post by thinusp on 2005-04-13
Hi all

I've got a problem with gtkpod and/or easytag. I've spent several days updating my mp3 collection for my brand new iPod photo ;)

It looks like easytag does a good job of writing the tags, both id3v1 and id3v2, but when I import my tracks into gtkpod to transfer to the iPod, it only seems to see the id3v1 tags, consequently truncating any tag that's longer than 30 characters.

I've played with the charset setting (gtkpod says id3v2 tags are supported if you tell it the correct charset or save the tags in unicode), but nothing's working

Does anyone know what the problem might be?

I'm using easytag 1.99.3
               id3lib 3.8.3
               gtkpod 0.88.2

Thanx
Thinus

---

### Post by thinusp on 2005-04-13
'k, Made some progress ;) Funny how the answer pops up 10 minutes after you post to the forum.

gtkpod seems to prefer id3v1 tags. If there is no id3v1 tag available then it uses the id3v2 tag properly. But now I can't find a setting in gtkpod prefs to prefer id3v2 tags or to ignore id3v1 tags

anyone?
Thinus

---

### Post by graabein on 2005-04-13
I plan on using gtkpod with my iPod photo as well. Have you tried mailing the author on gtkpod's homepage?

---

### Post by thinusp on 2005-04-13
not yet, I feel I should first check out if anyone else had the same problem and/or if I'm just to stupid to see a solution ;)

But it looks like currently gtkpod is using id3v1 if it's available otherwise it uses the id3v2 tags. I would think that it should first look for id3v2 tags and then for v1 tags if the v2 tags are not available. otherwise it works perfectly.

On the topic of iPod Photos, I heard the only way to placce photos on the iPod is via iTunes and there is no linux alternative. Anyone know of an app that will do this?

Cheers
T

---

