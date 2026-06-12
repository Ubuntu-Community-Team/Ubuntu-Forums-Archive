---
title: "pidgin window too small"
date: 2008-04-23
forum: General Help
---

### Post by bro on 2008-04-23
Hi,

I'm using pidgin in Hardy. I remember I could or at least had a bigger window to type in. Why can't I drag it to make it bigger and where/how can I change this?

---

### Post by Het Irv on 2008-04-23
If you Hit
Shift-Enter, the window will expand.  By default it only shows one line of text.  I can't see a way to change that default.

---

### Post by ryanhaigh on 2008-04-24
Pidgin developers decided that a single line for input is all thats needed and from what I have read it doesn't look like they will be changing their minds any time soon. It makes sense to some extent except that it makes the input area harder to focus with the mouse.

---

### Post by endlesssnowfall on 2008-04-24
There has actually been a fork of Pidgin called Funpidgin that adds back the ability to resize the text entry box, and adds some other optional features as well.  [http://funpidgin.sourceforge.net]("http://funpidgin.sourceforge.net")

---

### Post by notmatt on 2008-04-26
I would say lots of nasty things about the pidgin developers, but this is a public forum.  I spoke to a pidgin dev on IRC about it and he seemed to think it was great and why oh why would I want to change it.  Anyway, someone has written a plugin to fix pidgin:

[http://developer.pidgin.im/attachment/ticket/5296/manualsize-linux-i386.so](http://developer.pidgin.im/attachment/ticket/5296/manualsize-linux-i386.so)

If you download that plugin and copy it to your /var/lib/pidgin/ directory and then restart pidgin you should be able to enable the plugin that lets you resize the text input window.

---

### Post by rafaelcapanema on 2008-04-30
Wow! A few weeks ago I upgraded Pidgin to 2.4. The text box thing was really annoying. I thought it was a bug or something, and even stepped back to the previous version. Now that I have upgraded to Gutsy, I saw it again and came to Ubuntu Forums to find out what was going on. I'm in shock. Shame on you, Pidgin developers.

---

### Post by bro on 2008-04-30
thanx a lot! I'm going to try the plugin. Why any developer would want get this function 'out' of pidgin wonders me. If it does work, what harm is done by those who do change it to those who don't? It is by all means an unobtrusive feature...

> I tried: 
I downloaded the plugin from here: [http://developer.pidgin.im/ticket/5296]("http://developer.pidgin.im/ticket/5296"). Where there is both a version for 32 en 64bit. 
I installed it by moving the file to /usr/lib/pidgin/ (the above mentioned /var/lib/pidgin didn't exist in my filesystem, ubuntu hardy). Activated the plugin and yeah!

---

### Post by rafaelcapanema on 2008-04-30
Thanks a lot, notmatt! There's no /var/lib/pidgin here, though. I copied the script to /usr/lib/pidgin and it worked like a charm!

---

