---
title: "How can I make a right-click script to convert avi to mpg ?"
date: 2007-08-29
forum: General Help
---

### Post by tefflox on 2007-08-29
Basically, this works:
[INDENT][FONT=Courier New][B][COLOR=Navy]ffmpeg -i movie.avi -aspect 16:9 -target ntsc-dvd movie.mpg

dvdauthor -o dvd -t movie.mpg
dvdauthor -o dvd -T

mkisofs -dvd-video -o movie.iso /home/jess/movies/dvd/[/COLOR][/B][/FONT]

[/INDENT]I want to make a right-click script, so I can right click on the avi file and it does all the work in the background.

---

### Post by jusmurph on 2007-08-29
I think you need to put the script under /home/User?/.gnome2/nautilus scripts.

Not in frount of a Ubuntu machine but doa google for nautilus scriips and you should find where it needs to go.

---

