---
title: "Inkskape or any script - resize SVGZ files on the command line"
date: 2015-01-03
forum: General Help
---

### Post by tamir2 on 2015-01-03
Need to change the package of 50-100 files in various sizes 48x48, 32x32, etc. But I have not found how to do it in Inkssape ((.  The Internet is only found information about converting svg in png. But I just need to change the size of icons in SVGZ format. How to do it?

---

### Post by beep3 on 2015-01-03
I don't think Inkscape can do that. However, you can use [librsvg2-bin]("http://graphicdesign.stackexchange.com/questions/6574/in-inkscape-resize-both-the-document-and-its-content-at-the-same-time/6670#6670").

To resize an individual svg file to 48 x 48px you could use something like:

```
rsvg-convert input.svg -w 38 -h 38 -f svg -o output.svg
```

Unfortunately, the width and height are in points, not pixels. A point is roughly 80% of a pixel, so 48px translates to 38.4 pixels. rsvg-convert only accepts integers, hence the width and height have been rounded down to 38. The result is an svg file that's 47.5 x 47.5 pixels.

Assuming you got a directory with svg files which you want to scale and save in a subdirectory named '48' you could use this command:

```
for f in *.svg; do rsvg-convert $f -w 38 -h 38 -f svg -o 48/$f; done
```

---

### Post by tamir2 on 2015-01-03
**beep3**, thank you very much, very rescued!
There is one more request, if not more difficult. Calculating dimensions is somewhat confusing.  Could tell what numbers to put in the terminal for 128x128, 32x32, 24x24, 22&#1093;22, 16x16: 
for f in *.svg; do rsvg-convert $f -w **38** -h **38** -f svg -o 48/$f; done ?

---

### Post by beep3 on 2015-01-03
Okay... try this:

First make some directories for the files you're going to scale:

```
mkdir 128 32 24 22 16
```

Next, calculate how many points the various target sizes have by multiplying the number of pixels by .8 *and* rounding the result to the nearest whole number:

[LIST]
[*]128px * .8 = 102.4pt => 102pt 
[*]32px * .8 = 25.6pt => 26pt 
[*]24px * .8 = 19.2pt => 19pt 
[*]22px * .8 = 17.6pt => 18pt 
[*]16px * .8 = 12.8pt => 13pt 
[/LIST]

Then, run the following commands to scale the images and save them in the appropriate directory:

```
for f in *.svg; do rsvg-convert $f -w **102** -h **102** -f svg -o **128**/$f; done
for f in *.svg; do rsvg-convert $f -w **26** -h **26** -f svg -o **32**/$f; done
for f in *.svg; do rsvg-convert $f -w **19** -h **19** -f svg -o **24**/$f; done
for f in *.svg; do rsvg-convert $f -w **18** -h **18** -f svg -o **22**/$f; done
for f in *.svg; do rsvg-convert $f -w **13** -h **13** -f svg -o **16**/$f; done
```

You'll find that the some images are 1px larger or smaller than you want them to be. I did a quick check and found that images scaled to 22px are in fact 23px and that images scaled to 32px are in fact 33px. I can't think of a way to get them to the exact size - it's a result of the rounding we did earlier. It's pretty close though ;).

---

### Post by tamir2 on 2015-01-03
May God bless you!
In my case, suitable and with such accuracy).

---

### Post by Holger_Gehrke on 2015-01-03
Just for curiosity's sake, could you explain why you're doing this ? SVG is vector-oriented, it's the job of the program displaying them to scale them, the numbers inside the file are unitless, abstract and could just as easily mean nanometres as light years. If you have to scale them either you or the program you're using is doing it wrong ...

---

