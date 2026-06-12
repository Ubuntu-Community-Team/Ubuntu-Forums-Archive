---
title: "MP3 in Rythmbox (Music Player)"
date: 2005-06-15
forum: General Help
---

### Post by pooplar on 2005-06-15
I've brought over all my mp3's and places them in a folder in the home dir, however when trying to import them to Music Player I get the error:
'There is no plugin to handle a MP3 file.'
So, how do I remedy this?

---

### Post by Knome_fan on 2005-06-15
Mp3 support isn't included out of the box for legal reasons.

However, this is easy to solve.
Just enable the universe repository (Take a look at the great ubuntuguide about how to do it:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories))
and then install gstreamer0.8-mad

And that should be it.
Have fun. :-D

---

### Post by pooplar on 2005-06-15
works like a charm, thanks.

---

