---
title: "LaTeX"
date: 2004-11-30
forum: General Help
---

### Post by ubuntu_demon on 2004-11-30
Hi,

I need to write a paper in LaTex. I have never worked with LaTeX before. What is the easiest way to work with it in ubuntu ? I want a graphical editor environment like  
teXnicCenter (on windows) preferably from the ubuntu main repositorie and I would like to create pdf files with it. Suggestions ?

Thnx

---

### Post by jdong on 2004-11-30
Lyx is in Universe... I think that's as close as you're gonna get.

---

### Post by WW on 2004-11-30
I haven't used TeXnicCenter, but after reading a bit about it, I think the closest thing to it in Linux might be **kile**.  I've only been using kile for a couple weeks, but it seems to work pretty well.  Since kile is a KDE program, I had to do some minor tweaking of the settings to get the buttons working the way I wanted.  (For example, in Settings->Configure Kile -> Tools, I use xdvi, ggv and xpdf for the "Dvi viewer", "PS viewer" and "PDF viewer", respectively.)  Also, if you run kile from the command line, it will print many warnings (since it is not running under KDE), but it still works fine.

kile is available in the universe component of the Ubuntu repositories.

I tried lyx once, but having used a plain old editor for so long, I found that the GUI just got in the way. Also, I think lyx uses a special file format (.lyx), so if you are collaborating with someone, you'll have to convince them to use lyx, too.  Another wysiwyg editor to check out is texmacs, if you want to go that way.

---

### Post by karih on 2004-11-30
[QUOTE=demon666_nl]Hi,

I need to write a paper in LaTex. I have never worked with LaTeX before. What is the easiest way to work with it in ubuntu ? I want a graphical editor environment like  
teXnicCenter (on windows) preferably from the ubuntu main repositorie and I would like to create pdf files with it. Suggestions ?

Thnx[/QUOTE]
 Hmm, never used any gui for LaTeX, just plain gedit.  
LaTeX can be a bit confusing but a good start tutorial is /usr/share/doc/texmf/latex/general/lshort.dvi (may be .gz, just decompress it; note that you must have the tetex package installed; alternate is to search google for it).

---

### Post by ubuntu_demon on 2004-12-02
I don't want to use a KDE program like kile. I want to use latex and not custom formats that lyx has (according to you guys).

I want at least syntax highlighting and easy graphical formula insertion.

Thnx guys

---

### Post by ubuntu_demon on 2004-12-02
Kile works okay. I couldn't find a gnome application of comparable quality.

---

### Post by 2fargon on 2004-12-02
Check out this package called "diploma". It has some example latex files with some neat usage, so you can be aware of how someone created a paper. That package was a life saver for me when I started using latex. I use kile too, and I highly recommend it as a gui.

I am not certain what you mean by saying "i don't want kile". Is it that your hate everything that has an association with KDE or something?

Along with Kile, I also use Kdevelop once in a while, and hey, it works for me.

---

### Post by ubuntu_demon on 2004-12-02
[QUOTE=2fargon]Check out this package called "diploma". It has some example latex files with some neat usage, so you can be aware of how someone created a paper. That package was a life saver for me when I started using latex. I use kile too, and I highly recommend it as a gui.[/QUOTE]

Thnx I'll check it out.

> 
I am not certain what you mean by saying "i don't want kile". Is it that your hate everything that has an association with KDE or something?

No i don't hate KDE. I just thought it would be nice if there were a gnome app like it. But this does not seem to be the case. That's why I decided to use kile.

---

### Post by 2fargon on 2004-12-02
[QUOTE=demon666_nl]
No i don't hate KDE. I just thought it would be nice if there were a gnome app like it. But this does not seem to be the case. That's why I decided to use kile.[/QUOTE]

Thank God, I think the world will be a better place with people judging software on it's merits, and stopped fighting about which WM is superior :)

I hope you enjoy Kile.

[http://www.cs.technion.ac.il/~yogi/latex.html](http://www.cs.technion.ac.il/~yogi/latex.html)
is a good page, with a few helpful example tex files to get scientists and engineers started, just in case you are getting started.

Cheers!

---

### Post by ubuntu_demon on 2004-12-03
[QUOTE=2fargon]Thank God, I think the world will be a better place with people judging software on it's merits, and stopped fighting about which WM is superior :)
[/QUOTE]

If I wouldn't need KDE libraries it could save me a couple of mb's. Gnome app's are supposed to be better graphically integrated.  Maybe there are some stability / performance issues. Those things were my only considerations.

> 

I hope you enjoy Kile.

[http://www.cs.technion.ac.il/~yogi/latex.html](http://www.cs.technion.ac.il/~yogi/latex.html)
is a good page, with a few helpful example tex files to get scientists and engineers started, just in case you are getting started.

Cheers!

Just getting started indeed :)

Thnx!

---

### Post by zabilcm on 2004-12-08
[QUOTE=demon666_nl]Hi,

I need to write a paper in LaTex. I have never worked with LaTeX before. What is the easiest way to work with it in ubuntu ? I want a graphical editor environment like  
teXnicCenter (on windows) preferably from the ubuntu main repositorie and I would like to create pdf files with it. Suggestions ?

Thnx[/QUOTE]
 You could also try "texmaker" which is available at [http://www.xm1math.net/texmaker/index.html](http://www.xm1math.net/texmaker/index.html)
this does not ask you for kde-libs to be installed.

---

### Post by ubuntu_demon on 2004-12-09
thnx I'll try it this weekend and let you know. I will write my next paper on Ubuntu. 

I'll write the current one under TechniXCenter in windows because I still can't acces my raid array in Ubuntu. I'm going to backup my data, do a reinstall and make Ubuntu my primary OS in the christmas break.

---

### Post by stelleg151 on 2007-11-22
> **ubuntu_demon said:**
> If I wouldn't need KDE libraries it could save me a couple of mb's. Gnome app's are supposed to be better graphically integrated.  Maybe there are some stability / performance issues. Those things were my only considerations.


Speaking of an extra couple of mb's the tetex packages are almost 600mb after unpacking... Wow?

> 
Just getting started indeed :)

Thnx!

---

