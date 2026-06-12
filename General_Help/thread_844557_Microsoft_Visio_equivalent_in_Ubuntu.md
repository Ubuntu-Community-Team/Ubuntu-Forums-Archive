---
title: "Microsoft Visio equivalent in Ubuntu?"
date: 2008-06-29
forum: General Help
---

### Post by imolafem on 2008-06-29
I'm running Kubuntu 8.04 and like it a lot.  I am considering going only to Linux for my home PC and I was wondering if there is an MS Visio equivalent that is capable of reading MS Visio 2007 and lower files?  I've read Excel files with Open Office and thought that was pretty cool, so this will be my last hurdle.  I would also like to be able to edit the .vsd files.

Thanks in advance....

---

### Post by forger on 2008-06-29
Answering with a link:
[http://www.osalt.com/visio](http://www.osalt.com/visio)

>  **ArgoUML** 0.24
Available for: windows mac linux unix java
ArgoUML is a great UML (Unified Modeling Language) tool. Written in Java and using Java Web Start makes it easy to work with (install) and use on any platform. It has full support for the UML 1.4... Read more
**Kivio** 1.6.1
Available for: windows mac linux unix java
Kivio is part of the KOffice open source office suite. For flowcharting, network diagrams and all other graphing need Kivio solves them with an easy to user interface. As part of the KOffice office... Read more
**StarUML** 5.0
Available for: windows mac linux unix java
StarUML is a great open source UML application. Supporting UML 2.0 and MDA (Model Driven Architecture) StarUML let's you work with all related diagrams. Code generation can be done for Java, C++ and... Read more
**Dia** 0.96
Available for: windows mac linux unix java
Dia is designed to be much like the commercial Windows program 'Visio'. It can be used to draw many different kinds of diagrams. It currently has special objects to help draw entity relationship... Read more
**OpenOffice Draw** 2.2
Available for: windows mac linux unix java
Open Office Draw, part of the Open Office package, wasn't designed to compete with high-end graphics packages but is an easy to use, effective drawing tool that makes it simple to create flowcharts,... Read more

---

### Post by Zimmer on 2008-06-29
Not sure you will find anything, given Visio is now owned by MS. However, for flowcharting and similar Visio applications Open Office Presentation has quite a bit to offer.
Long time since I used Visio (circa 1996/7) :) Office plans and flowcharts mostly.

---

### Post by imolafem on 2008-06-29
Thanks for the list of applications. Who has experience with one or some of these apps for infrastructure diagrams, server racks, DMZs, etc?  That is what I currently use Visio for...

---

### Post by forger on 2008-06-29
I've been playing around with kivio and dia last year, they're quite good, but I'm not sure for what you ask for, sorry :)

---

### Post by imolafem on 2008-06-29
Thanks for the suggestions on dia and kivio, they both look like what I want -- do you know if either of them can read/modify Microsoft Visio (.vsd) files?

---

### Post by ad_267 on 2008-06-29
> **imolafem said:**
> Thanks for the suggestions on dia and kivio, they both look like what I want -- do you know if either of them can read/modify Microsoft Visio (.vsd) files?

Don't know about kivio but I assume it would be similar. This from the dia faq [http://www.gnome.org/projects/dia/faq.html#VisioFiles](http://www.gnome.org/projects/dia/faq.html#VisioFiles)

> Compatibility

  36. Q: Can Dia open Visio .vsd files ?
      A: No, it can't. Visio file format is a completely proprietary and undocumented file format. So it is really difficult to write code to read it. The now-defunct Software Bazaar offered a bounty of several thousand dollars for reverse-engineering the Visio format. We really would like to be able to do so.

      An easier alternative would be to make a Visio plug-in that will allow conversion. Other programs have already done this for their proprietary formats. If somebody were to make such a script, we could set up a public server to do conversions.

      With Visio 2002, it has become possible to export Visio diagrams as XML. Microsoft, in their infinite generosity, has even published the Schema. With the new XSLT plug-in, it should be only a question of writing a proper XSLT document to be able to translate.

      Ian Redfern is working on decoding the Visio format. If you have any interest in converting Visio files, please give him your assistance. 

---

### Post by imolafem on 2008-06-29
Well that's a bummer....

I found this link called vsd dump from the faq link.

It looks like its something for gnome but I'm not sure what it does.

[http://freshmeat.net/projects/vsdump/](http://freshmeat.net/projects/vsdump/)

---

### Post by forger on 2008-06-30
You could also use Inkscape for more power over SVG images :) You could probably use somehow the XML output that Visio features to create an SVG image ?

---

### Post by imolafem on 2008-06-30
My end goal is to be able to share .vsd files with other Windows users.

---

### Post by bobblehat on 2008-06-30
A major drawback of Visio has always been it's proprietary closed format. Even when I used Windows I always found it caused problems by people I was sharing documents with not all having the same version or not having it at all. That was a major factor in me ditching Visio in the end - if the format had been more open I'd have been more likely to still be a user of it.

Just use something else such as Inkscape which uses svg natively and runs on both Linux and Windows.

---

### Post by forger on 2008-06-30
> **imolafem said:**
> My end goal is to be able to share .vsd files with other Windows users.

Dia supports opening VDX files, export in VDX format (in Visio menu File > Save as) and use Dia in linux.

You can export to .VDX using Dia menu File > Export :)

---

### Post by imolafem on 2008-06-30
> **forger said:**
> Dia supports opening VDX files, export in VDX format (in Visio menu File > Save as) and use Dia in linux.

You can export to .VDX using Dia menu File > Export :)

Perfect!  I'll give it a try.  Thanks so much!

---

### Post by emily.wilson on 2009-12-30
Hey man its difficult to use any other alternative for visio...
As if you are habitual like me to visio a [Project management software]("http://www.visiotoolbox.com") it would be difficult for you to shift to other tool. Me too use visio 2007 and now as 2010 is available in market i am soon waiting to experiment my hands on it.

---

### Post by junapp on 2009-12-30
not exactly meeting your requirements, but I think they have some online sharing features. Not 100% sure but seeing as how google is going to the Chrome OS I figure something like:
[http://www.gliffy.com/](http://www.gliffy.com/)
will become more and more polished over time and likely snapped up by Google at some point.

[http://www.gliffy.com/examples/network-diagrams/](http://www.gliffy.com/examples/network-diagrams/)

---

### Post by przemnet on 2012-10-24
Hi,

you may find **yEd Graph Editor** usefull.
[http://www.yworks.com/en/products_yed_about.html](http://www.yworks.com/en/products_yed_about.html)
[http://en.wikipedia.org/wiki/YEd](http://en.wikipedia.org/wiki/YEd)

**Dia** - diagram creation program also looks good
[https://live.gnome.org/Dia](https://live.gnome.org/Dia)

This site may also help: [http://alternativeto.net/software/microsoft-visio/?platform=linux](http://alternativeto.net/software/microsoft-visio/?platform=linux) 

Looking forward,
Przemek.

---

