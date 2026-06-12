---
title: "Uninstall OpenOffice Fonts"
date: 2007-05-26
forum: General Help
---

### Post by nsivin on 2007-05-26
I want to get rid of most of the TTF fonts that load
automatically when I fire up Writer, since more than half seem to be for
languages that I don't read. I have used spadmin to add TTF fonts, but it only deletes fonts previously added. 

I also tried deleting the actual TTF files from the font directory. That got their names off the font menu in OOW, but there is still a blank line for each one, which means it is just as cumbersome to pick the font one wants. There must be some way to do this, but the OOO 2.0 Writer Guide does not give a clue about it. 

There was a previous post entitled " Can I delete Openoffice Fonts?." Several replies were from people who wanted an answer, but no one suggested one!

---

### Post by merlinus on 2007-05-26
The best way to do this is to use Synaptic, and enter "ttf" in the search box.  This will iallow you to select and uninstall all of the other language fonts without having to do it manually.

Of course, I learned this the hard way, after doing what you did, and creating a mess.  I got out of it by using Thunar as root, and copying and deleting lots of fonts!

Good luck!

-merlin

---

### Post by fragos on 2007-05-26
Synaptic is always best for these things because it knows all the steps involved.  It even rebuilds grub when you use synaptic to delete older kernel versions.  The part you probably didn't do was run "sudo fc-cache -fv".

---

### Post by merlinus on 2007-05-26
> **fragos said:**
>  The part you probably didn't do was run "sudo fc-cache -fv".

What does this do?

Thanks!

-merlin

---

### Post by H.E. Pennypacker on 2007-06-03
> **merlinus said:**
> The best way to do this is to use Synaptic, and enter "ttf" in the search box.  This will iallow you to select and uninstall all of the other language fonts without having to do it manually.

Of course, I learned this the hard way, after doing what you did, and creating a mess.  I got out of it by using Thunar as root, and copying and deleting lots of fonts!

Good luck!

-merlin

Thanks.  This, I am sure, has saved much of my time.

---

### Post by oomingmak on 2007-07-08
> **merlinus said:**
> The best way to do this is to use Synaptic, and enter "ttf" in the search box.  This will iallow you to select and uninstall all of the other language fonts without having to do it manually.

Of course, I learned this the hard way, after doing what you did, and creating a mess.  I got out of it by using Thunar as root, and copying and deleting lots of fonts!
Thank you! This is a godsend for me. All those foreign fonts were driving me crazy.

I never could understand why they got installed in the first place if you've selected English as the only language during the installation. You'd think that the installer could  install appropriate font sets based on the language chosen for the set-up routine and also as specified for the installation.

Anyhow, I too tried manual font removal in the past and found that all the entries (in programs like OpenOffice) were still there bugging me. For some reason it just never occurred to me to use Synaptic (simply because fonts are not 'programs') but now that you have pointed it out to me, it seems so obvious. They are packages just like anything else.

It was so easy to do and it's a joy to finally have font lists that aren't 8 times the height of your screen.

:)

---

