---
title: "My fonts changed after running KDE?!?!"
date: 2007-07-11
forum: General Help
---

### Post by herbster on 2007-07-11
I have attached a SS of Firefox, but it's similar with Terminal. Nothing has changed in terms of the actual fonts or anything, but it's just the look of them has changed, they are a bit different and I am perplexed except that for the first time I logged into a KDE session yesterday for a few mins and tinkered around with it to try it out, then logged out and back into my regular gnome and my fonts had kinda changed.

I am sorry I don't have a SS of what it looked like before, but the fonts are only in Terminal, Firefox and a few other things, everything else (menus, etc.) are fine. I have Firefox set to use Verdana but if you look at the SS it's not, same with the font for Terminal, it is just looking different than what it is set to.

Puzzled :confused:

---

### Post by Espreon on 2007-07-11
Hmmmm, try Uninstalling KDE and Purging it.

Oh BTW: Nice theme, it is the one I use!

---

### Post by herbster on 2007-07-11
> **Espreon said:**
> Hmmmm, try Uninstalling KDE and Purging it.

Oh BTW: Nice theme, it is the one I use!

What's the command again? I want to be sure I'm right before I do it and mess anything up. I know it's dpkg --purge something or another.

And yeah I love the FF theme, it is perfect with my desktop/theme :)

---

### Post by Espreon on 2007-07-11
I believe the GUI way to do it was to open Synaptic and select all the KDE stuff to be completely removed.

---

### Post by herbster on 2007-07-11
Okay I removed kubuntu-desktop but it's still the same. It's like the fonts are a tiny bit "fuzzier" if you will, but I have again, changed no settings.

I'm on the verge of reinstalling Feisty here, someone please help! :(

---

### Post by nvteighen on 2007-07-25
Hi, I've exactly the same problem. I'm working it around and if I find something, I'll tell you.

---

### Post by herbster on 2007-07-25
nvteighen,

I searched for quite some time and could not find a solution that worked. I wound up reinstalling Ubuntu.

---

### Post by nvteighen on 2007-07-25
Yes, I'm going to do it right now. It seems to be a problem with GNOME's gtk engine corrupted by KDE's qt. Reinstall is the only way I can think to get rid of that corruption. And have noticed fonts were just one problem: for example, I couldn't properly create a desktop for a new user (it was a proposed solution I found somewhere) and Compiz didn't work anymore.

In one word: KDE hijacks GNOME.

Wish me luck.

---

### Post by nvteighen on 2007-07-25
Solved reinstalling.

---

