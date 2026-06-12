---
title: "Cyrillic letters instead of German umlauts in some documents, web pages etc."
date: 2016-04-18
forum: General Help
---

### Post by Lennex on 2016-04-18
Hello everybody,

let me start by saying that I have already asked my question on [ubuntuusers.de]("https://forum.ubuntuusers.de/topic/umlaute-werden-als-kyrillische-zeichen-dargest/"), unfortunately, to no avail (I will link from there to here as well). Also, I have already done a lot of web searching, but also without any usable results.

My problem is as follows: I am using Ubuntu 14.04.4 LTS with XFCE. For a few month now, I have a very strange problem. In some documents (PDFs), as well as on certain websites, fonts are not rendered corrrectly. In particular, whenever a German "umlaut" occurs in these documents (that is something like an "ä", basically an a, o, or u with extra dots on top), this character is not rendered correctly. Instead, I am presented with some cyrillic letter. An example is attached to the post, the correct rendering should be "Bundespräsidentenwahl", with an "ä" instead of the cyrillic "d".

Oddly enough, the problem really is one of rendering only (or printing as well in the case of PDF), the character is the standard Unicode symbol, and when copied to say the command line or a text editor, it displays as it should as "ä". Also, my system is set to English language settings, all language specific environment variables are set to "en_US.UTF-8". Also, the problem seems to be deeply rooted within the system, as it also occurs say over SSH, a newly created user account, and with any web browser.

I really hope that somebody could help me with this rather annoying issue!

Cheers,
Lennex

---

### Post by Lennex on 2016-04-20
Hello again,

I have finally solved the problem! Turns out that some time ago I had installed a somehow "damaged" Helvetica font, and that messed up the rendering of certain symbols. As a solution, I have simply removed the offending .ttf file from /usr/local/share/fonts/ttf and then regenerated the font cache using
```
sudo fc-cache -f -v
```
Now, everything is fine again :-).

Cheers,
Lennex

---

