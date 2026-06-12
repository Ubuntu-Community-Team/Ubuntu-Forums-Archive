---
title: "Weird, outlined helvetica in Firefox..."
date: 2007-05-28
forum: General Help
---

### Post by volfro on 2007-05-28
Hi Ubuntuforums,

When I upgraded to Feistyx64 (and even, I think, before then), I started getting weird hollow fonts in Firefox, like this:

[IMG]http://img126.imageshack.us/img126/1395/screenshotiy2.png[/IMG]

It seems to only happen with Helvetica Neue Condensed, which many websites use nowadays. I thought it would go away when I got rid of Feisty 64 and switched to UbuntuStudio x32, and even formatted my Home directory so I got a completely fresh start. No dice. Any time there's Helvetica Neue condensed, it shows up as those weird, jagged outlines.

Anybody else had this problem? What can I do to fix it? It's not a huge deal, but it is quite aggravating.

---

### Post by volfro on 2007-05-29
Nobody's had this issue?

If it makes a difference, the problem doesn't occur in Epiphany. Or other browsers, for that matter.

---

### Post by fragos on 2007-05-29
When you don't have a font, firefox will pick one to use that it does have.  Open up nautilus and enter fonts:/// in the location bar.  You'll see all the fonts you have on the system and each will have displayed in each font the letters "Aa".  Look through there to see if an outlinr font.  If you do that's probably the one firefox is using.  Uninstall that font and your problem should be solved.

---

### Post by volfro on 2007-05-31
Crap. Out of three thousand fonts, Helvetica Neue Bold is in fact an outline font. Annoying.

By "uninstall" do you mean "delete"?

---

### Post by volfro on 2007-05-31
I moved it to another directory. Now I'm without Helvetica Neue Bold. That sucks.

Oh well, it solved the problem! Thanks very much.

---

### Post by fragos on 2007-05-31
OpenOffices lets you apply different font effects to any font.  Any font can be used as an outline font.  Other neat effects are shadow, embossed and engraved.  I use outline and shadow together.  Of course this is only for Open Office and not use in Firefox.

---

