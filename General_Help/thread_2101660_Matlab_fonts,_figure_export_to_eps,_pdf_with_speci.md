---
title: "Matlab fonts, figure export to eps, pdf with special characters, umlaut broken, fixed"
date: 2013-01-05
forum: General Help
---

### Post by cocojambo on 2013-01-05
Hi!

I was really tired finding the solutions which fix all the problems I had with Matlab on my Linux machine (Matlab version 2011b, but I guess it applies to other releases as well). As this forum is well indexed by Google, I reactivated my forum account :-) and have tried to put a meaningful title, so that others can find this information as well.

These were my problems:
- German umlauts (ä, ö, ü) and all non ISO character were not correctly displayed in Matlab figures
- Exporting of figures to different formats, especially eps and pdf broke the fonts, although I managed at some time to display the fonts in the figure correctly

Here is how I cured all symptoms (thanks for all the contributors, sorry for not naming them by name).

Matlab ONLY uses iso fonts for exporting to eps/pdf, but any modern Linux distribution uses UTF font encoding (seems like Matlab is kind of legacy software to me). To fix the display, start matlab with an ISO locale, for a german one you could use
```
$ LANG=de_DE@euro; matlab
```
to force matlab to temporarily use the ISO locale.

For this to work, you have to enable the corresponding ISO locale by editing the file
```
$ sudo nano /var/lib/locales/supported.d/local
```
and adding de_DE@euro ISO-8859-15, this can also be done by executing
```
$ sudo locale-gen de_DE@euro
```

For matlab to correctly render fonts the figure axes (keyword axis), the packages xfonts-100dpi and xfonts-75dpi have to be installed:
```
$ sudo apt-get install xfonts-100dpi xfonts-75dpi
```

I have also added the matlab fonts to the system:
```

$ sudo ln -s $MATLABDIR/sys/fonts/ttf/cm/ /usr/share/fonts/
$ sudo fc-cache -f -v

```
You have to log out and log in again, so that Matlab finds the fonts.

All put together, that does the trick. By the way, I use "export_fig" from Matlab file exchange to export my figures to pdf. For the figures to look nice, actually you have to set up the paper in centimeters (or inches). But this is another story. Read more at:
[http://www.parl.clemson.edu/~ahoover/Matlab-figures.txt]("http://www.parl.clemson.edu/~ahoover/Matlab-figures.txt")

I hope this help you. Happy Matlabing!

Bye,

coco

---

