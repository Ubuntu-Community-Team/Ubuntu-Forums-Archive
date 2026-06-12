---
title: "Change  highlight clolour"
date: 2014-03-07
forum: General Help
---

### Post by markus.p.baraa on 2014-03-07
[SIZE=2]Hi, I have used Linux for a while and I [/SIZE]wondered how I can change the highlight colour in my GTK theme.
I am using Cinnamon 2 and GTK+ 3.0. ](*,)

[ATTACH=CONFIG]250940[/ATTACH]

---

### Post by Tristan_Williams on 2014-03-07
I've never really dealt much with editing Gtk themes, but maybe this will help.

Gtk is basically CSS (used in web design), You probably already knew that but just in case.

If you can figure out which Gtk(CSS) rule controls the highlight color, you can change it to whatever you want.

Most themes have a bunch of global variables set to something, and then set specific elements in the DE to the variable.
So maybe you can figure out the variable and change its value.

I know probably not much help but worth a shot

---

