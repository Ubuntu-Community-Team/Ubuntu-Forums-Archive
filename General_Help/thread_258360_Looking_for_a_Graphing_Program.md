---
title: "Looking for a Graphing Program"
date: 2006-09-15
forum: General Help
---

### Post by UltraMathMan on 2006-09-15
I'm trying to find a free program that is similar to [Grapher (OS X)]("http://en.wikipedia.org/wiki/Grapher"). I've got wxMaxima with gnuplot running now but I'd like to be able to change the view of the graph, graph implicit bivariate functions, and have something more centered on 3D-Graphing that would ideally support multiple surfaces on the same graph. Any suggestions?

---

### Post by canadianwriterman on 2006-09-15
I don't know anything about graphing programs, but I found this that sounds, maybe, like what you're looking for...
[URL="http://www.cmap.polytechnique.fr/~jouve/xd3d/"]
http://www.cmap.polytechnique.fr/~jouve/xd3d/[/URL]

---

### Post by UltraMathMan on 2006-09-15
Thanks, it looks interesting, I'll check it out :)

---

### Post by UltraMathMan on 2006-09-15
OK, I'm having some trouble compiling I have build-essential and g77, but when I run ./configure && make I get ```
bash: ./configure: /bin/csh: bad interpreter: No such file or directory

``` any suggestions?

[B]EDIT: From the Install.txt file

"To compile and install xd3d and its related programs, you must have a
Fortran 77 and a C compiler. The X11 library libX11.a and the X.h
include file must be present on your computer"[/B]

---

### Post by UltraMathMan on 2006-09-16
hehehe I needed the csh shell, doh!

ok I ran ./configure && make clean && make , but got errors at the end ```
make[2]: *** No rule to make target `/home/steve/xd3d-8.2.3/lib/my_Xlib.a', needed by `/home/steve/xd3d-8.2.3/bin/xd3d'.  Stop.
make[2]: Leaving directory `/home/steve/xd3d-8.2.3/src/d3d'
make[1]: *** [xd3d] Error 2
make[1]: Leaving directory `/home/steve/xd3d-8.2.3'
make: *** [all] Error 2

```

I think I need my_Xlib.a ...
Any suggestions or alternate program suggestions?

**EDIT: misdirected ./configure to wrong xlib.a location that fixed but I still get a bunch of errors during compiling (more than what's shown above) but when I do a ctrl+shift+c and then a ctrl+v in gedit nothing pastes. I also tried to output to a text file but the errors didn't output.**

---

### Post by yopnono on 2006-09-16
Have you tried this.
[http://www.xaraxtreme.org/](http://www.xaraxtreme.org/)

---

### Post by Abild on 2006-09-16
Converting the rpm package with alien seems to work.
Do this:

install alien and fakeroot

convert the package by entering
fakeroot alien xd3d-8.2.3-1.i386.rpm
and install it
sudo dpkg -i xd3d_8.2.3-2_i386.deb

You run the program by entering xd3d from the console

Hope this helps :)

---

### Post by UltraMathMan on 2006-09-16
Thanks Abild, that got it installed :)

yopnono, thanks but I'm looking for a mathematical graphing program.

I trying to figure out how to work xd3d, in the meantime any other suggestions? 

Thanks again for everyone's help!

---

