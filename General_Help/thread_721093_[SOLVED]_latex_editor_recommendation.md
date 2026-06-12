---
title: "[SOLVED] latex editor recommendation"
date: 2008-03-11
forum: General Help
---

### Post by amyst on 2008-03-11
I am looking for the linux near-equivalent of Miktex and TexnicCenter (these two are simply too great). I looked into the recommendations from other threads and downloaded texmaker from Synaptic - but it doesn't work and I can't make a sense out of its enduring compilation error. 

Can anyone recommend a good editor that will work right out of the box that is similar to TexnicCenter? No emacs or gedit. I used TexnicCenter for years and loved the interface. It is one of the two programs that keeps me booting to windows. 

Please help! :( I am so close to ditch xp.

---

### Post by perce on 2008-03-11
> **amyst8 said:**
> I am looking for the linux near-equivalent of Miktex and TexnicCenter (these two are simply too great). I looked into the recommendations from other threads and downloaded texmaker from Synaptic - but it doesn't work and I can't make a sense out of its enduring compilation error. 

Can anyone recommend a good editor that will work right out of the box that is similar to TexnicCenter? No emacs or gedit. I used TexnicCenter for years and loved the interface. It is one of the two programs that keeps me booting to windows. 

Please help! :( I am so close to ditch xp.

XEmacs (give it a try, it has nice extensions like x-symbols and whizzytex) or kyle (a KDE application, but it works on Gnome too).

---

### Post by amyst on 2008-03-11
Thanks - I was expecting someone to suggest Kile (I think you are refering to Kile) for sure. Does Kile work well in Gnome desktop? Does it need lots of KDE dependencies? The reason that I am asking is that at one time I have both Kubuntu and Ubuntu desktop, and the overlapping applications don't look good next to each other. 

Also, does Kile come along with all the tex packages or do I have to get them separately?

---

### Post by p_quarles on 2008-03-11
Thread moved to General Help.

---

### Post by joe.turion64x2 on 2008-03-11
> **amyst8 said:**
> Thanks - I was expecting someone to suggest Kile (I think you are refering to Kile) for sure. Does Kile work well in Gnome desktop? Does it need lots of KDE dependencies? The reason that I am asking is that at one time I have both Kubuntu and Ubuntu desktop, and the overlapping applications don't look good next to each other. 

Also, does Kile come along with all the tex packages or do I have to get them separately?
Kile is the best match for you I guess. It works flawlessly on Gnome, and will require tetex to be installed (the libraries). It has its KDE requirements (mainly some kdelibs) but if you already have Kubuntu installed that shouldn't be a problem, and since I guess disk space isn't the problem either you can safely install it.

Even if you don't use KDE you can safely install its dependencies, the only drawback is that it loads a little slower than a native Gnome app, but considering its superb features it is worth the wait.

I don't think you can get a better LATEX editor in any platform.

Thanks.
Joe.

---

### Post by Erunno on 2008-03-11
> **amyst8 said:**
> Thanks - I was expecting someone to suggest Kile (I think you are refering to Kile) for sure. Does Kile work well in Gnome desktop? Does it need lots of KDE dependencies? The reason that I am asking is that at one time I have both Kubuntu and Ubuntu desktop, and the overlapping applications don't look good next to each other. 

Also, does Kile come along with all the tex packages or do I have to get them separately?

Kile should work well under GNOME as do other KDE applications (and vice versa). Whether LaTeX gets installed pretty much depends if your distribution marked it as a dependency. On my distribution it is installed automatically for instance. At worst I think that Kile will pull kdebase as a dependecy besides the libraries but I guess you'll have see for yourself.

---

### Post by amyst on 2008-03-11
Thanks for all your (rapid!) replies. I'm going to give kile and tetex a try.

---

### Post by gaussian on 2008-03-11
Couple comments:

Nothing in Linux (as far as I know) will give you MikTeX's ultra-cool ability to automatically download missing tex-packages on the fly.

I know you said no Emacs, but in my humble opinion Auctex (which now includes Latex-Preview) is the best LaTeX environment. I personally learned Emacs to use Auctex, now I use it for pretty much everything.

---

### Post by perce on 2008-03-11
> **gaussian said:**
> Couple comments:

Nothing in Linux (as far as I know) will give you MikTeX's ultra-cool ability to automatically download missing tex-packages on the fly.

I know you said no Emacs, but in my humble opinion Auctex (which now includes Latex-Preview) is the best LaTeX environment. I personally learned Emacs to use Auctex, now I use it for pretty much everything.

Emacs and XEmacs (I personally prefer XEmacs because I find it easier to configure) also have an extension called whizzytex which compiles on the fly and shows the output in real time. It's very nice, although quite slow on old computers.

Emacs, XEmacs and Kile support inverse and forward search; you can find a detailed howto on how to set them up in the help of kdvi, the dvi viewer for KDE.

They don't download and install LaTeX packages, but If you install tetex-extra you'll have pretty much everything you need.

---

### Post by amyst on 2008-03-11
I looked at Auctex's screenshots, but I doubt it could be as efficient. For one TeXnicCenter generates a hierarchy of shortcuts to titles, figures, equations etc. for the "project" type latex files, which saves tons of time when I need to quickly find a figure.    

I found texmaker's interface more intuitive  than TeXnicCenter's (for one, symbols are grouped into tabs), but it lacks  the "template" feature. When I want to start with a self-written latex template, I have to cd to "Template" folder (I had been wondering why Ubuntu names a default folder in ~/ as "Template", now I know :) - correct me if I'm wrong!), open the tex file,  cd to another "work" folder, and save it. I don't need to do half as much clicks in TeXnicCenter because it knows that its Template folder is special. 

I'll give a Auctex a shot when I need to create something simple :KS

---

