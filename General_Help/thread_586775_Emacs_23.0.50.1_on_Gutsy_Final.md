---
title: "Emacs 23.0.50.1 on Gutsy Final"
date: 2007-10-22
forum: General Help
---

### Post by dmonkey on 2007-10-22
Hi,

I've visited this forum many times and have found invaluable help here, and this is my final resort.

I consider myself reasonably proficient in Linux, but this problem has stumped me. I recently install Gutsy 7.10. On my previous SUSE system, I successfully built the Emacs CVS with the options

./configure --with-gtk --with-xft

Indeed, I get a nice GTK environment when I open emacs. In SUSE, i was also able to select fonts via the ./.Xresources file:

Emacs*Font: Bitstream Vera Sans Mono:10

and this worked great. This is my current problem in Gutsy - I cannot get this font thing to work. I have tried:

Rebuilding emacs (Xft support shows up in config.log)
Using mkfontscale and mkfontdir to make the relevant files in the bitstream vera dir and then adding manually to x: xset +fp ...
Installing xfs and xsftt

None of the above has worked. Can anyone shed light on this issue? Indeed, I can load font like this:

Emacs*Font: -misc-bitstream vera sans-...

but all i get is an ugly aliased font in emacs.

Help!! This is driving me crazy!

---

### Post by gaussian on 2007-10-22
I have this working in Feisty (don't have access to that computer right now). Try instead of Emacs*font emacs*font. This could make a difference (it did in one of my computers). Can you change the font from command line, i.e. does 

emacs --font "Bitstream Vera Sans Mono-10"

work? 
I assume you are aware of the following link:
[http://www.emacswiki.org/cgi-bin/wiki/XftGnuEmacs](http://www.emacswiki.org/cgi-bin/wiki/XftGnuEmacs)

Alternatively you could try downloading a pre-built package, see:
[http://peadrop.com/blog/category/computers/emacs/](http://peadrop.com/blog/category/computers/emacs/)

I have no experience with them though

---

### Post by dmonkey on 2007-10-22
Thanks for the reply.

I should have told you the error I am getting! When I type emacs (or emacs --font ...) I get

No fonts match `Bitstream Vera Sans Mono:10'

This happens for any choice of truetype font. I *can* type:

emacs --font '-dejavu-dejavu sans mono-medium-r-*-*-*-*-*-*-*-*-*-*'

and I do get an emacs window, but the fonts are not antialiased. I have used the page you suggested before, and this is precisely the way that I downloaded and built emacs on my Gutsy.

Thanks for the help though.

(PS I also think I had this working in Feisty, but I have no idea why it should be different for Gutsy...)

---

### Post by gaussian on 2007-10-22
Ok, let's hope someone who actually knows thing or two will answer :) And I will put your experience to my rather long list of reasons for waiting before updating to Gutsy (my Feisty laptop works perfectly, why break it now?).

---

### Post by dmonkey on 2007-10-22
UPDATE **

I followed the instructions to download the package from the link you gave me, and it now works. This suggest I built the package incorrectly...

Never mind! Thanks again for the help!

---

### Post by dmonkey on 2007-10-23
Ok, another update.

Although the emacs snapshot works, I can't set the font using the xrdb resources - I have to set it in the command line, like this:

emacs-snapshot --font "..."

Anyone know why? Also, I reeaaaly want to know why my self-build didn't work. I can provide the config.log if anyone is interested...

---

### Post by dmonkey on 2007-10-23
For anyone interested, I solved the problem.

I needed the liboft font library.

Thanks again for the help.

---

### Post by rosslaird on 2007-10-23
I have the same problem, and installing libotf (and its various iterations) did not work for me. I still get the dreaded:

```
No fonts match `Monospace-13'

```

I upgraded to Gutsy today, so it's definitely gutsy-related.

Ross

Update:

As per this:

[http://peadrop.com/blog/category/computers/emacs/]("http://peadrop.com/blog/category/computers/emacs/")

I added the gutsy repos:

deb     [http://ppa.launchpad.net/avassalotti/ubuntu](http://ppa.launchpad.net/avassalotti/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/avassalotti/ubuntu](http://ppa.launchpad.net/avassalotti/ubuntu) gutsy main

And voila!
The fonts look big, but I think I can fix that, and they are antialiased -- and no error message.

R.

---

### Post by dmonkey on 2007-10-25
Well, I'm not too sure what I did to fix it. I just tried building again for fun.

Maybe try now removing the avassalotti snapshots and following again the instructions at [http://www.emacswiki.org/cgi-bin/wiki/XftGnuEmacs](http://www.emacswiki.org/cgi-bin/wiki/XftGnuEmacs). Thats all I did.

Wish I could be of more help!

---

### Post by Sudo-Alpha.get on 2008-02-13
How do you get Emacs on Gutsy?

---

