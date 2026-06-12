---
title: "[SOLVED] Importing and Exporting between MS-Project &amp;amp; Planner"
date: 2007-01-30
forum: General Help
---

### Post by The Foz on 2007-01-30
I am working very hard to be able to retire my Windoze. 
Unfortunately, in my job, MS-Project is a *de facto* standard for project planning.
I know that I can do pretty much the same things in planner. What I don't know is whether it is possible, and how, to import plans from MS-Project into planner, and vice versa. MS-Project can export to, and import from, XML, CVS, and a few other text based file formats.
Does anyone have any experience with this?

---

### Post by marianom on 2007-01-30
Hi Foz, I'm after the same thing.
Check [this]("http://www.simpleprojectmanagement.com/forum/index.php?action=vthread&forum=3&topic=163") out and let me know if it works for you. I asked the guys who work with me to send the msproject file in xml and I'm still waiting.

---

### Post by Turtle.net on 2007-01-30
This one : [http://ganttproject.biz/](http://ganttproject.biz/) is working (able to import msproject files).
Never used it at work in real condition but that should be ok.

---

### Post by marianom on 2007-01-30
Thanks Turtle.net. I imported my .mpp file and it worked ok. I cannot find how to save the file as .mpp but anyway it's cool.
I posted this same questions months ago (I will update that thread now) and finally an answer!!!!
Thanks again

---

### Post by The Foz on 2007-01-31
Cool!
I also just imported a .MPP file. 
Thanks a million, Turtle. Just what I needed.

---

### Post by Turtle.net on 2007-01-31
> **marianom said:**
> I cannot find how to save the file as .mpp but anyway it's cool.
I think you have to export it as a file viewable by MSproject but not as a mpp.

---

### Post by waltea on 2007-09-04
I have just found a great tool for this which is by Projity and called [OpenProj]("http://openproj.org/").

It imports and exports MS Project files really easy. They are exported in Microsoft XML format.

And getting it on my machine was very easy from the Debian package. Enjoy!

I know it might be too late for some but I hope it is of some use.

---

### Post by The Foz on 2007-09-05
I have also just started using OpenProj.

So far I have found it really good. I am using it on both Linux & Windows, at home anf at the office.

---

### Post by linux4begin on 2007-11-26
Dear All,

yes, OpenProj  is working on Ubuntu-7.10 without any prob.
If you go through the Synaptic Package Manager then it will be good, as it will ask you to install the required dependencies also, so we dont need to do any more.

First i had tried with .deb package but it gets fail, then i had tried with SPM [Synaptic Package Manager] and it works fine after it.

I recommende it to use for .mpp 

Pl. reply if anyone find any more thing on this.

---

### Post by Soarer on 2007-11-26
I don't seem to have it in Synaptic. Could you say which repository contains it?

Thanks.

---

### Post by forestpixie on 2007-11-26
couldn't find it in the repos either, but I'd installed from the sourceforge download
[http://sourceforge.net/projects/openproj/](http://sourceforge.net/projects/openproj/)

change to directory containing download, probably cd Desktop

then ```
sudo alien openproj-0.9.6-1.noarch.rpm
``` 

you'll have a deb file then to install from - I haven't had a problem with the deb install.

---

### Post by Soarer on 2007-11-26
Thanks forestpixie :)

---

### Post by The Foz on 2008-07-15
You can find OpenProj on sourceforge:
[http://sourceforge.net/projects/openproj/]("http://sourceforge.net/projects/openproj/")

It is available for Windows as well as Linux.

I have tested it out by managing a complete project from start to finish using it.

---

