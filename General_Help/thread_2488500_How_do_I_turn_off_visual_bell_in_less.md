---
title: "How do I turn off visual bell in less"
date: 2023-07-07
forum: General Help
---

### Post by chopra on 2023-07-07
Hi guys,
I just upgraded from ubuntu 20 to 22, and I have my LESS envorinment variable set to LESS=-Lcq with the lowercase q for "quiet" in most, (but not all) situations.

I do not want to completely disable the audible bell, just when I reach the top or bottom of the screen. This had been working fine....until I upgraded.

Among some other unpleasant changes with the upgrade, less now causes the entire terminal screen to blink when I reach the top or bottom of the document, which is just as annoying as the bell.
This didn't happen before. According to the man page:

-q or --quiet or --silent
              Causes moderately "quiet" operation: the terminal  bell  is  not
              rung if an attempt is made to scroll past the end of the file or
              before the beginning of the file.  If the terminal has a "visual
              bell",  it  is  used  instead.  The bell will be rung on certain
              other errors, such as typing an invalid character.  The  default
              is to ring the terminal bell in all such cases.

       -Q or --QUIET or --SILENT
              Causes  totally  "quiet"  operation:  the terminal bell is never
              rung.  If the terminal has a "visual bell", it is  used  in  all
              cases where the terminal bell would have been rung.

I have tried altering the /etc/inputrc to comment out set bell-style visible and put set bell-style none instead, but this does not seem to work.

Thanks in advance,
Chopra

---

### Post by chopra on 2023-07-07
I found the solution.
A newer version of less has a --no-vbell option, so I changed the LESS variable to LESS='-Lqc --no-vbell'

I had to install it from this site
[http://greenwoodsoftware.com/less/download.html](http://greenwoodsoftware.com/less/download.html)

This placed less in my /usr/local/bin directory, so, for the man program to work I did, as root (sudo -i):
cd /etc/alternatives
ln -fs /usr/local/bin/less pager

Chopra

---

### Post by MAFoElffen on 2023-07-07
Thank you for posting that solution!

So... You can mark this as "Solved" now?

---

