---
title: "Xubuntu 7.04 + Ubuntuzilla = large spaces between lines in Firefox"
date: 2007-10-16
forum: General Help
---

### Post by retrovertigo on 2007-10-16
I just installed Xubuntu 7.04 a couple days ago, and because I wanted to get quicker updates for Firefox and Thunderbird I installed Ubuntuzilla.  After using Ubuntuzilla to install Firefox 2.0.0.7, large spaces started appearing between lines.  I have uploaded an example [here](http://i27.photobucket.com/albums/c158/palehose/crappy_fonts.png).

Has anyone seen something like this before?  Any ideas on how I can get rid of those god-awful spaces?  My X11 configuration did not change at all, it's not referencing different font directories, so I don't know why the fonts would change so drastically between the Firefox 2.0.0.6 from the Ubuntu repository and the 2.0.0.7 that was installed by Ubuntuzilla.

It seems to happen with some fonts, and not with others, too... Like these forums are fine, no large spaces between lines of text.  I'll check the stylesheets to compare and see if something jumps out at me.

---

### Post by retrovertigo on 2007-10-16
OK, after looking into the stylesheets, I noticed this was happening a lot with stylesheets that referenced Verdana and Arial, two fonts not present on my system.  I copied over the MS TrueType fonts from my Windows partition (I knew that would come in handy one day!) and re-ran mkfontdir and fc-cache.

Voila!

---

