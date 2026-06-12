---
title: "Firefox cant display sites well in Ubuntu 7.04"
date: 2007-04-22
forum: General Help
---

### Post by anhhung on 2007-04-22
Hi, I've just installed Ubuntu and got some problems with my firefox.

Sites seem to get shrink become abnormally smaller compared to the normal displays in XP. 

I tried making the size bigger but things got screwed up. Only a minor number of sites got the right display. It really hurts my eyes.

Is there anyway to fix this problem? I'm trying to migrate to Ubuntu from this version!

---

### Post by Martje_001 on 2007-04-22
I think it is your resolution. Set it to 1024x768.

---

### Post by dwbell on 2007-04-22
No it's not the resolution. I can't tell you exactly what the fix is because I'm using Kubutu but look for a setting to force fonts to use 96 dpi. That fixed things on my machine.

---

### Post by anhhung on 2007-04-22
Thanks for the quick response. It looks quite better now but some sites seem to got shrink. I mean, the size got smaller and there were quite some space not in used. Does this mean poor design on the web's side?

---

### Post by strabes on 2007-04-22
What sites are smaller? What is smaller? Just the fonts or are pictures smaller too?

---

### Post by Geekboy on 2007-04-22
I'm having some issues with [CNN]("http://www.cnn.com").  It's with the latest news section.  Very blocky and large.

---

### Post by strabes on 2007-04-23
Can you post a screen shot? With the window active, just hit alt+print screen.

---

### Post by Geekboy on 2007-04-24
Well, I fixed my problem with fonts not displaying properly.  I remember having this same problem with other versions of Ubuntu.  I would even try tinkering with Firefox's font settings , but that would not help.

It turns out I needed Microsoft True Type Core Fonts (msttcorefonts package) installed.  Installing the fonts is very easy with Ubuntu.  You can do it from Synaptec Package Manager.  This is how I did it:  (I'll put it step by step)

[LIST]
[*]Click on System > Administration > Synaptec Package Manager
[*]Type in your password
[*]Search for msttcorefonts
[*]Select the package and click on Apply
[*]The package will now install[/LIST]After it's done, restart Firefox and the fonts should look fine.  :KS

---

### Post by strabes on 2007-04-24
He he he, or you could just type "sudo apt-get install msttcorefonts" and hit enter :)

That was the next thing I was going to suggest. msttcorefonts is almost required for general ubuntu usage.

---

### Post by jmagsho on 2007-04-24
> **anhhung said:**
> Thanks for the quick response. It looks quite better now but some sites seem to got shrink. I mean, the size got smaller and there were quite some space not in used. Does this mean poor design on the web's side?

The comment about poor web design is a good one.   One thing to consider is that in the past few years, many web developers wrote to the M$ standards for Internet Explorer which are much, much looser than those of the W3C which is what Firefox is built against.   As such, things like using M$ fonts and other Windoze specific hooks are often used at the expense of the rest of us who surf with non-M$ operating systems and/or browsers.

---

### Post by Geekboy on 2007-04-24
> **strabes said:**
> He he he, or you could just type "sudo apt-get install msttcorefonts" and hit enter :)

That was the next thing I was going to suggest. msttcorefonts is almost required for general ubuntu usage.
I hear you, but I can never remember the package name. ;)

---

