---
title: "Program that parses html?"
date: 2008-03-28
forum: General Help
---

### Post by Helgiks on 2008-03-28
I am creating a small script for conky so that it displays what teachers in my school are sick and not coming in.

I'm using curl and grep for this, but I need a program that parses the html for me before sending it to conky, so 

<p>28. mars 08</p><p>Einar &Oacute;skarsson EFN/N&Aacute;T</p><p>Gu&eth;r&uacute;n Ragnarsd&oacute;ttir DAN</p>

looks like:

28. mars 08
Einar Óskarsson EFN/NÁT
Guðrún Ragnarsdóttir DAN

How would i go about doing that? The html code isn't really the problem but the  &Oacute;=Ó, &eth;=ð ... any suggestions for a program that can do that for me?

---

### Post by Helgiks on 2008-03-28
Well, ok, I just did it the hard way, abusing sed...

---

