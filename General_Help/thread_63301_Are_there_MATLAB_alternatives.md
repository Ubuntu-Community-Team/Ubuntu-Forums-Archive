---
title: "Are there MATLAB alternatives?"
date: 2005-09-07
forum: General Help
---

### Post by John.Michael.Kane on 2005-09-07
I'm looking for an alternative to matlab. if anyone has any idea of programs that come close to or mirror matlab please post. if this question has been ask already i'm sorry  reasking it.

Thanks


Edit: I think i have found what i was looking for in the [https://wiki.ubuntu.com//UbuntuScientists](https://wiki.ubuntu.com//UbuntuScientists)

---

### Post by bogoliubov on 2005-09-07
Yes there are.
One that is supposed to be good is Mathematica. It can do analytical and numerical stuff quite good. I have only tried it once, but it seems ok and I know some people who use it every day. However, it costs money. I don't know if there are student licenses or something similar.

Maple is good for analytical stuff. You can do some programming and convert your worksheets to latex code. This costs money too; but there are student licenses, should you be one...

Finally we have Scilab and Octave. These are free and you should be able to find them in Synaptic. I haven't tried them, but I've heard that Octave should be quite compatible with matlab-files....

Probably there are more, but these are the ones I've heard of...

Hope this helps!

---

### Post by John.Michael.Kane on 2005-09-07
Thanks

---

### Post by bored2k on 2005-09-07
I have Mathemathica 5. It costs about 700 hundred US dollars though.

```
apt-cache search matlab
python-numeric - Numerical (matrix-oriented) Mathematics for Python
python2.3-numeric - Numerical (matrix-oriented) Mathematics for Python
python2.4-numeric - Numerical (matrix-oriented) Mathematics for Python
ipython - enhanced interactive Python shell [dummy package]
ipython-common - enhanced interactive Python shell [common files]
libumfpack4 - set of routines for solving unsymmetric sparse linear systems
libumfpack4-dev - set of routines for solving unsymmetric sparse linear systems
libumfpack4-doc - set of routines for solving unsymmetric sparse linear systems
matwrap - wrapper generator for matrix languages
octave - GNU Octave language for numerical computations (2.1 branch)
octave2.1 - GNU Octave language for numerical computations (2.1 branch)
octave2.1-doc - PDF documentation on the GNU Octave language (2.1 branch)
octave2.1-emacsen - Emacs support for the GNU Octave language (2.1 branch)
octave2.1-headers - header files for the GNU Octave language (2.1 branch)
octave2.1-htmldoc - HTML documentation on the GNU Octave language (2.1 branch)
octave2.1-info - GNU Info documentation on the GNU Octave language (2.1 branch)
pdl - perl data language: Perl extensions for numerics
python-numeric-tutorial - Tutorial for the Numerical Python Library
python2.2-ipython - enhanced interactive Python shell [built for python 2.2]
python2.3-ipython - enhanced interactive Python shell [built for python 2.3]
python2.4-ipython - enhanced interactive Python shell [built for python 2.4]
r-base - GNU R statistical computing language and environment
r-base-core - GNU R core of statistical computing language and environment
src2tex - A converter from source program files to TeX format files
tela - interactive tensor language
texify - Beautify source code for use with LaTeX
scilab - Matrix-based scientific software package (a la Matlab and Xmath)
scilab-bin - Matrix-based scientific software package (a la Matlab and Xmath)
scilab-doc - Matrix-based scientific software package (a la Matlab and Xmath)

```

---

### Post by cnayak on 2005-09-07
[QUOTE=SD-Plissken]I'm looking for an alternative to matlab. if anyone has any idea of programs that come close to or mirror matlab please post. if this question has been ask already i'm sorry  reasking it.

Thanks


Edit: I think i have found what i was looking for in the [https://wiki.ubuntu.com//UbuntuScientists](https://wiki.ubuntu.com//UbuntuScientists)[/QUOTE]

 
 Scilab is the best among open source alternatives for Matlab. It has a GUI resembling Matlab. For Octave, you need to install gnuplot ( apt-get will do it).

---

### Post by John.Michael.Kane on 2005-09-07
bogoliubov bored2k cnayak thanks

---

### Post by myg on 2005-09-11
did it install correctly for you?  

i just apt-get'ed it and i get this error:


[HTML]<pre>/usr/bin/scilab: line 31: /usr/lib/pvm3//lib/pvmgetarch: No such file or directory</pre>[/HTML]


from a quick google search, it seems that others have this same problem.  any ideas?  

im running hoary.

---

### Post by kleeman on 2005-09-11
Try installing the pvm package. BTW this package only runs for me in kde not gnome wierd! There are bugreports on font issues....

---

