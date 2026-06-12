---
title: "[SOLVED] Firefox - xine wont load video"
date: 2008-02-21
forum: General Help
---

### Post by stooshbunutu on 2008-02-21
I was trying to watch a bbc video the other day and it said I needed a plugin in firefox to play it so I plicked the top one off the list which was *xine*. The videos will now buffer but I just get the blank background and no video playing.

How can I either get it working or remove it so I can try other options (it doesn't appear in my list of firefox plugins so I can't remove it like that)

Welcoming any help available:)

---

### Post by fyo on 2008-02-21
The (global) plugins should be located in /usr/lib/firefox/plugins or /usr/lib/mozilla/plugins.

Try "vlc" instead of xine. Getting no video would seem to suggest that you are missing the codec required to play back the content. "vlc" doesn't use separate codecs (their are built in) so it might do the trick.

(I also personally vastly prefer vlc over xine, but that's probably just me).

---

### Post by stooshbunutu on 2008-02-21
good idea I like vlc

how can i remove xine without royally screwing up firefox?

---

### Post by stooshbunutu on 2008-02-21
I have vlc plugin installed but it doesnt do anything, I also tried mplayer but only get sound not video.

Do you know If i have to specially configure any of them

---

### Post by stooshbunutu on 2008-02-21
I decided to scrap xine and go with whats done on [this thread]("http://ubuntuforums.org/showthread.php?t=661833")

It all works well now :)

---

