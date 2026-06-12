---
title: "Right Alt key... I never noticed this before"
date: 2007-05-08
forum: General Help
---

### Post by aysiu on 2007-05-08
For over a year on my desktop computer, I'd always used the left Alt key. Recently, though, I tried the right Alt key and realized... it doesn't work.

The weird thing: on my laptop with Ubuntu, both Alt keys work.

That's odd. Am I the only one?

---

### Post by rygar on 2007-05-08
[http://www.pcworld.com/article/id,130923-page,1-c,linux/article.html](http://www.pcworld.com/article/id,130923-page,1-c,linux/article.html)

number 1!

---

### Post by earobinson on 2007-05-08
> 1. Fix your right Alt key.

U.S. users may notice before too long that the right-hand Alt key on their keyboard doesn't work in Ubuntu. This will drive you nuts if you frequently use that key. (I use mine constantly for the Alt-F2 Run command in Gnome.)[http://www.pcworld.com/article/id,130923-page,1-c,linux/article.html](http://www.pcworld.com/article/id,130923-page,1-c,linux/article.html)

Edit Dam your fast rygar.

---

### Post by bulldog on 2007-05-08
My right alt key isn't working either [desktop],only the left does.:)

EDIT;
Now it does too,TY

---

### Post by ticopelp on 2007-05-08
I heard about this fix, but I can't think of a single time I've ever used my right alt key, ever.

---

### Post by aysiu on 2007-05-08
Thanks for that! > To get the right Alt key to behave like the left Alt key, select System, Preferences, Keyboard. On the Layout Options tab, open the 'Third level choosers' branch, and reassign the third-level chooser to another key. (I prefer the right Windows key--my laptop doesn't even have one of these, so I am actually assigning a useless function to a nonexistent key!) I'll give it a shot.

To ticopelp: I'd been using Ubuntu on that computer for over a year and didn't notice until now. I, too, don't use the right Alt key.

Alt-F2 for me is left thumb on the left Alt key and left middle finger on F2.

---

### Post by earobinson on 2007-05-08
Let us know how it goes!

---

### Post by ricardisimo on 2008-05-17
Here's a related question...

I just installed Kubuntu Hardy on my comp at work (I'm Ubuntu Feisty here at home), and discovered the joys of altgr-intl (or some name like that) the keyboard layout of my dreams! It's basically "US-International with dead keys", only without the dead keys, if that makes any sense. There's only one problem, which is that the keyboard layout interface on Kubuntu is nowhere near as detailed as in Ubuntu (Feisty, at least), and there's no place I can find that allows you to decide your 3rd-level choosers. I'd like to select both, or rather either ALT key for this. Anyone know how to do this in Kubuntu? Thanks in advance.

---

### Post by ricardisimo on 2008-05-20
Anyone? Kubuntu doesn't give as many options as far as keyboard settings. But is there a work-around? For example, here's the pertinent lines from my xorg.conf:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"altgr-intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
```
What would "XkbOptions" read like with both ALTs as 3rd-level choosers? Thanks.

---

