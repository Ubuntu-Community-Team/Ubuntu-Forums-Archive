---
title: "Firefox search plugins not showing up in the correct folder"
date: 2005-09-04
forum: General Help
---

### Post by Daniel Rehm on 2005-09-04
I never got around to removing all the Firefox search engine plugins I didn't want until just yesterday. I  like my search area to be nice and tidy: Just google, dictionary.com, imdb, stuff like that. So I removed eBay, Amazon, stuff like that.

I looked up where they were stored on Linux, navigated to the appropriate directory (in my case, /usr/lib/mozilla-firefox/searchplugins) and cleared out all the superfluous junk. Wheeeeee.

Fine so far.

What happened next sort of surprised me, though.

Feeling experimental, I added a few search engines, just for kicks. I mean, I can always just remove them, right?

Wrong.

I'm not sure what's going on... because the new plugins aren't showing up in the folder that they're supposed to be in... and, insult to injury, Gnome's search utility isn't finding them! So now I can't delete them!

Is this maybe because of the non-standard version of Firefox that ships with Hoary? Where the hell is it putting these things? I'd like to get rid of these plugins but I can't find them to do it! They're 100% functional, by the way, so I *know* they're out there somewhere.

---

### Post by Daniel Rehm on 2005-09-04
Could somebody maybe install a search plugin and just see if it arrives in the appropriate folder? That way I'd at least know if I was crazy, or not.  =-/

---

### Post by Ishamael on 2005-10-24
A bit late, but here it is:

~/.mozilla/firefox/*.default/search

(where * is some random chars)

---

