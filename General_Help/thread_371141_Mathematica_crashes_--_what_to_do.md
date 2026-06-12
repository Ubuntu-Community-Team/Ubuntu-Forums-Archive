---
title: "Mathematica crashes -- what to do?"
date: 2007-02-26
forum: General Help
---

### Post by peterhaagerup on 2007-02-26
I am trying to use Mathematica 5.2 on my Ubuntu 6.10. I have several problems -- the first problem is the well known font-problem, the startup dialog saying "Unable to find font with Times, weight Plain, slant Plain, and size 12. Substituting Courier". I have heard that some has found a solution to this, but I haven't so far. I don't know why it is saying that, because the fonts look fine anyway.

The main problem is, whenever i am trying to save a document, opening the help browser, opening almost any other dialog, Mathematica crashes -- in other words, it is impossible to use it in this way. This is frustrating -- have anybody found a solution to this? I think it could be a problem that Mathematica doesn't like the current Ubuntu kernel or maybe something else, but it looks like a serious problem. I really need help on this :confused:

The third problem is that when using Beryl, any other color than white in both text and pictures is transparent - I think this might be solved, but it is not that important in constrast to the crashing problem.

I have been using Mathematica 5.2 on my old Gentoo Laptop -- the only problem at that time was the startup warning about the fonts.

If Mathematica is started from the terminal, it says this when crashing:
"Mathematica has received the signal: SIGSEGV and has exited.
If possible, please report this problem to [email]support@wolfram.com[/email]
describing in in as much detail as possible what you were doing
when the problem occurred.
Segmentation fault"

Please help me -- especially with the crashing problems -- I can't be the only one having problems with this :(

---

### Post by peterhaagerup on 2007-02-26
I finally found a solution. It turned out, that it was a general font problem for X-programs after Edgy-update, such as gv, xclock and of course Mathematica and Maple. It haven't thought about the problems I also had with Maple (math symbols turning into weird letters), gv that couldn't start and more. I finally found a fix from this thread:

[http://ubuntuforums.org/showthread.php?t=289227](http://ubuntuforums.org/showthread.php?t=289227)

What i did was to remove /usr/share/X11/fonts and created a symlink from /usr/share/fonts/X11 to /usr/share/X11/fonts:

# cd /usr/share/X11/
# sudo rm -dfr fonts
# sudo ln -s /usr/share/fonts/X11/ fonts

Now Mathematica is not crashing anymore (no font warning either), Maple fonts is what they used to be (i'm talking about the classic worksheet version), gv starts, no warnings about fonts when running xclock and so on.

I hope this will fix your problems too :)

---

### Post by kevinlyfellow on 2007-03-01
For beryl solution, go to post [http://ubuntuforums.org/showthread.php?p=2233095#post2233095](http://ubuntuforums.org/showthread.php?p=2233095#post2233095)

---

