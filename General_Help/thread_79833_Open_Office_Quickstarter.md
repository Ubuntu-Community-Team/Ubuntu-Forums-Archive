---
title: "Open Office Quickstarter?"
date: 2005-10-20
forum: General Help
---

### Post by ymmotrojam on 2005-10-20
Is there any way that I can get Open Office to start up part of the way when I login like it does in Windows? Is the quickstart ability available for Ubuntu? Thanks.;)

---

### Post by rwabel on 2005-10-21
[quote=ymmotrojam]Is there any way that I can get Open Office to start up part of the way when I login like it does in Windows? Is the quickstart ability available for Ubuntu? Thanks.;)[/quote]

you mean openoffice2? openoffice has the quickstart. And I'm still waiting for the final release of openoffice2 in breezy

---

### Post by MakubeX on 2005-10-21
IMHO, OpenOffice in Breezy is very amazing. The startup was like a breeze for it only took me not more than 10 seconds to put the thing on-screen as compared to OpenOffice on other distros.. maybe like Fedora Core 4.

---

### Post by fishfork on 2005-10-29
Open Office still takes ages to load on my old hardware, and I'm having trouble getting the quickstarter to work with OpenOffice 2 in Breezy. I've installed package ooqstart-gnome, but, no matter what I put in 'full path to the application', I cannot get it to actually load OpenOffice. Has anyone got this to work in breezy?

---

### Post by ercork on 2006-03-08
Not sure if anybody's interested in this any more but someone on the openoffice forum made a quickstart script which works perfectly (for me anyway):

[http://www.oooforum.org/forum/viewtopic.phtml?t=30269&highlight=quickstart+linux](http://www.oooforum.org/forum/viewtopic.phtml?t=30269&highlight=quickstart+linux)

The ooqstart-gnome in the repositories doesn't seem to work with openoffice2 so try this instead. On my old PIII Thinkpad (900MHz), writer documents now load in about 7-8 seconds as opposed to 20-25 without. Plus, when you close down your docs, it stays running in the background so the next time you open something up, it's equally fast. It takes up extra RAM of course, but I think the speed increases are worth it.

---

### Post by ronmarley1 on 2006-03-08
See the capture below.  I have this option available in OOo 2.0.  Open a OOo app. and it's under Tools-->Options-->Memory.

---

### Post by ercork on 2006-03-09
Strange, I don't have that option available at all. For me, "Number of Objects" is the last option in that dialog box. I'm using openoffice version 1.9.129 in Breezy - is yours a more up to date version?

---

### Post by treris on 2006-03-09
probably it is, 
OOo version 2.0.1 has been available for some time through the repositories, 

I don't know if you're using for instance the command line or Synaptic, but adding 

deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./ 

to your etc/apt/sources.list and then refreshing your packages should help you upgrade from version 1.9.129 to 2.0.1

and that does include a quickstarter

---

### Post by ronmarley1 on 2006-03-09
[QUOTE=ercork]Strange, I don't have that option available at all. For me, "Number of Objects" is the last option in that dialog box. I'm using openoffice version 1.9.129 in Breezy - is yours a more up to date version?[/QUOTE]

I'm running 2.0.  By the way, 2.02 was just released today.

---

### Post by ercork on 2006-03-09
Didn't know there was a different repository with newer versions - must update so. Thanks.

---

### Post by ronmarley1 on 2006-03-09
[QUOTE=ercork]Didn't know there was a different repository with newer versions - must update so. Thanks.[/QUOTE]

2.02 is not in the repos yet.  Probably will have to wait until Dapper for that.

---

### Post by rwabel on 2006-03-09
I'm on dapper and I've 2.02 :-)
and true there is that nice option. I've to check that out

---

