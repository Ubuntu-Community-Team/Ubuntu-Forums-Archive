---
title: "Gambas?"
date: 2008-01-24
forum: General Help
---

### Post by k0rfain on 2008-01-24
sorry, i didnt know where else to put this... But is there anything like gambas but for Gnome/gtk?

[http://gambas.sourceforge.net/](http://gambas.sourceforge.net/)

---

### Post by AnonCat on 2008-01-24
The Gambas homesite FAQ mentions HBASIC and Monobasic.  I have no idea if they're anything like Gambas, but they might be worth a try.  There's also a non-free Visual Basic style program available for Linux, but I can't remember what the name of it is.  I'll try to find it and get back to you (it might have a free home use edition or something.)

Here's a site with a list of BASIC compilers available for Linux:

[http://basic.mindteq.com/LinuxList.asp](http://basic.mindteq.com/LinuxList.asp)

---

### Post by hammer v2 on 2008-02-06
Yup. it's called REALbasic.

It's proprietry software, but the standard linux version is free.

It's a BRILLIANT piece of software by the way...definately worth a go! I had a few bugs with the R5 version and had to move back to R4 which has yet to give me any hassles.

Anyway, It's free. It's also well documented and really well supported with 3rd party plugins and things.

There's a from novice to pro book you can buy which is really good at showing you the ropes (depending on your level of experience I guess...)

---

### Post by hammer v2 on 2008-02-06
Forget what i said...realbasic is too buggy. I gave up on it last night and moved to GAMBAS. It's nice to see a gpl app whip a proprietry app's ***! :) Gambas recently hit version 2 (Stable) and it is much nicer to work in. It now does GTK apps! yay! I think this is the way forward for you. :) 

V2 isn't in the ubuntu repos yet.

add this line to your sourced.list and go nutz! :)

1) Add the following line to your /etc/apt/sources.list file:
For Gutsy systems:

deb [http://azores.linex.org/gambas-other/](http://azores.linex.org/gambas-other/) gutsy main

For Feisty systems:

deb [http://azores.linex.org/gambas-other/](http://azores.linex.org/gambas-other/) feisty main


For Edgy or Guadalinex V4 and V4.1 systems:

deb [http://azores.linex.org/gambas-other/](http://azores.linex.org/gambas-other/) edgy main



2) Update your packages sources:

apt-get update


3) Install gambas:

apt-get install gambas2

---

