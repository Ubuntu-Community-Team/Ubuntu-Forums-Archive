---
title: "Need a Dock!"
date: 2006-08-08
forum: General Help
---

### Post by calvinthomas on 2006-08-08
Can anyone tell me a dock for Ubuntu, I have installed xgl and love it but I really want a dock similar to the OSX dock! Can anyone help out, i've heard of kiba but I can't install it!

Calv

---

### Post by thermans on 2006-08-08
Kiba is awesome.  What problems are you having with it?

---

### Post by calvinthomas on 2006-08-08
I can't install it, when I use this guide here:

[http://www.compiz.net/topic-2004-howto-compile-and-install-kiba](http://www.compiz.net/topic-2004-howto-compile-and-install-kiba)

and copy and paste the first line in a terminal I get (with a sudo command):

cvs [checkout aborted]: could not get working directory: Permission denied

Without a sudo command I get:

cvs checkout: warning: failed to open /home/calvin/.cvspass for reading: Permission denied
cvs [checkout aborted]: could not get working directory: Permission denied

Calv

---

### Post by calvinthomas on 2006-08-08
Ok, i've managed to get it installed by downloading the rpm and using alien to convert it to the deb and then just installing, it seems to have installed fine but I have no idea how to start the dock, can anyone tell me how to do this? Also how can I make it start at start-up?

Calv

---

### Post by atrus123 on 2006-08-08
go to the directory where the kiba-dock is and type:

./dock

(or whatever the command with your version is).

To run it at startup, add it to your sessions (under Preferences).

For example, mine reads:

/home/atrus/tmp/akamarucvs/kiba-dock/dock

I'm using cvs, so yours might be a bit different.

---

### Post by calvinthomas on 2006-08-08
hmm perhaps it didn't install fine, when trying what you said I get:

./dock: symbol lookup error: ./dock: undefined symbol: g_type_register_static_simple

Is that an installation problem or do I need to run something first?

Calv

---

### Post by calvinthomas on 2006-08-08
I'm doing well, well kind of, i've got it installed and running.... and populated using the populate script, but how do I add other applications to it?

Calv

---

### Post by phido on 2006-08-08
edit the populate.sh and run it again

---

### Post by jstueve on 2006-08-08
Or.... drag a program icon to the dock (the edges work best), you can open up nautilus to /use/share/applications or drag program items from the gnome panel.

---

### Post by jimmygoon on 2006-08-08
If you can compile it, gnome-dock.org looks EXTRAORDINARILY promising...

---

