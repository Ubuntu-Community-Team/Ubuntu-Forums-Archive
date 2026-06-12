---
title: "From avi to DVD"
date: 2005-10-26
forum: General Help
---

### Post by sandrinux on 2005-10-26
Hy all
I use 5.10 Brezy, and I'm trying some kind of "basic video authoring".
I used before the 5.04 Hoary , and have followed this guide:

[http://forums.gentoo.org/viewtopic.php?t=117709](http://forums.gentoo.org/viewtopic.php?t=117709)

that I found very usefull.

Unfortunelly I have some problem now with transcode, as I told in another thread.

But the question here is:

can anibody suggest me an alternative to the trio transcode-mplex-dvdauthor to transform a "file.avi" in a DVD-compliant structure ?

I don't need subtitles, menus, two/three languages...
I simply want to watch a film with my family in the living room :-)
I don't need a "GUI-all-in-one" program, also because my very old PC (PIII800, 512Mb RAM, Matrox G400 16Mb) with a "command-line" one (with no X-session working, i mean) will probably encode some fps more.

May anibody help me.
Thanks.

P.S. sorry for my bad english :-\

---

### Post by N6546R on 2005-10-26
Maybe tovid?

Perry

---

### Post by Bil-E-daKid on 2005-10-26
I'd have to suggest Tovid. It rocks - I tried it in the weekend on the 'Star Trek: In the Pirkinning' movie that downloaded as an AVI.

Haven't watched the whole thing yet but Tovid certainly worked a treat making it into a DVD.

It's *extremely* small too - as it's just a bunch of scripts - but you can also install a very slim gtk GUI as well. 

It does some of the bits you don't necessarily need (menus, etc) but I think you'll find it does the trick.

There are some dependencies to it as well - just follow everything in this article and you'll get a working DVD in no time.

[http://www.linux.com/article.pl?sid=05/08/01/1734201]("http://www.linux.com/article.pl?sid=05/08/01/1734201")

---

### Post by sandrinux on 2005-10-27
Thanks
Seems that tovid is exactly that I was looking for.
I have tested it with a little file and it works!!

---

### Post by bionnaki on 2005-10-27
hmm..
so how do I install tovid?

sorry :rolleyes:

---

### Post by sandrinux on 2005-10-27
Was 1.30 AM, so may be I don't remember perfectly :-\ , but I did this way:

Download the tovid.version.deb in [http://tovid.sourceforge.net/](http://tovid.sourceforge.net/) 

give a 
**sudo dpkg -i tovid.version.deb **

you will have an error , something like:

**tovid depends from lib.version**

make a 

**sudo apt-get install lib.version**

then again
**sudo dpkg -i tovid.version.deb **

That's all

---

### Post by Bil-E-daKid on 2005-10-27
Yep - that's about it. If you want the gui, then download and dpkg -i the tovid-gui deb package as well.

The link in my last post lists some mandatory dependencies and some optional ones too. I just made sure I had all of them installed (via sudo apt-get install <package>) and it all worked fine.

:-)

---

### Post by jeffreyvergara.NET on 2005-10-27
you can find the .deb packages here [http://packages.kirya.net/]("http://packages.kirya.net/") or you can edit your sources.list

deb [http://packages.kirya.net](http://packages.kirya.net) unstable main contrib non-free
deb-src [http://packages.kirya.net](http://packages.kirya.net) unstable main contrib non-free

---

### Post by bionnaki on 2005-10-27
sweet thanks 
everyone

---

