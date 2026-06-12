---
title: "Postscript files problems"
date: 2007-06-07
forum: General Help
---

### Post by jtgalway on 2007-06-07
Hi all,

   I had a scan around the forums to see if there was something similar to my problem and couldn't find a relevant post, so sorry if this has been dealt with before.

   I installed Ubuntu Feisty a couple of months ago and everything seems to be working great - best distro I've ever used! I only had two problems: I couldn't get a 1280X800 resolution and I am having problems with ps and eps files. The first problem was solved by installing 915resolution as I have a dell laptop (Inspiron 630m) with an Intel 915 integrated video card.

   I can't seem to solve the postscript problem and it's a big one for me because I am a grad student and need to be able to produce ps and pdf documents using latex. The problem occurs when I use either 'convert' or some program like 'ps2pdf' on files I've made on my computer. For instance, I have tried to use gnuplot to make some plots for myself and when I use a postscript output and try to view the file, my computer locks up, my HD goes crazy and I can see with 'ps aux' that the memory is being chewed up. Even the mouse starts jumping around the screen. The same occurs if I try to convert that ps file to a pdf or some other format. Even when I convert it to a jpeg, say, and leave it running for the 10-12 mins it takes to complete, the image is cropped funnily and half of it is missing.

   This is not an old computer. I bought it last year and I think it is running 1GB ram and a ~2GHz Centrino. I tried installing all of the fonts I could find, a total LaTex installation and the same with ghostscript. I tried dpkg reconfigure ghostscript as well and it didn't help.

   Weirdly, if I produce ps or eps files on another computer (SL4.0, RH9, etc) and transfer them to my computer, I can do whatever I want with them. I can view them and convert them etc to my heart's content.

   When the computer starts to really freeze up, I can only get things back to normal by waiting it out or by killing the following process, which is obviously eating up memory. It's always the same gs process that causes the problem:

```
xxxx     11689  3.2 87.2 1075200 896052 ?      D    18:53   0:06 /usr/bin/gs -sDEVICE=x11alpha -dNOPLATFONTS -dGraphicsAlphaBits=4 -dTextAlphaBits=4 -dDOINTE
```

   Any advice on what to try next would be appreciated! Thanks.

   John

---

### Post by WW on 2007-06-07
Could you give an exact sequence of commands that leads to a problem?

From what you wrote, it sounds like if you do this:
```

$ gnuplot
gnuplot> plot sin(x)
gnuplot> set terminal postscript eps
gnuplot> set output "sine.eps"
gnuplot> replot
gnuplot> quit
$ ggv sine.eps

```
then you'll have a problem viewing the file with ggv.
Is that correct?

EDIT: By the way, there are an assortment of bug reports related to ghostscript over in [https://bugs.launchpad.net/](https://bugs.launchpad.net/), including [this one]("https://bugs.launchpad.net/ubuntu/+source/kdegraphics/+bug/110765").  (The report says the bug is in "kdegraphics", but it is not clear that it is specifically a KDE/Kubuntu bug.)

---

### Post by jtgalway on 2007-06-08
Yup! That's the kind of thing I'm talking about. 

Another example would be if I did something like this:

```
$ convert image.bmp image.ps
$ gv image.ps &
```

Even the convert command would take forever to complete.

Anything along those lines really. As I said, I only get this error from ps/eps files I create on this laptop. I have no problem dealing with files created on another computer and then manipulated on this one, so you could be right about the KDE/Kubuntu bug (although I am using Ubuntu).

Thanks for the info.

---

### Post by Welschemann on 2007-06-12
Hello,
I had the same issues: Generating ps files with GNUplot. And when trying to open or even just when a preview is generated, the computer almost freezes due to memory consumption (90% of 1GB).

But I found out about the problem and a (temporary) solution in this forum. Have a look at [http://ubuntuforums.org/showthread.php?t=318986#9](http://ubuntuforums.org/showthread.php?t=318986#9)

Installing gs-gpl
```
sudo aptitude install gs-gpl
```

and then switching to it
```
sudo update-alternatives --config gs
```

---

