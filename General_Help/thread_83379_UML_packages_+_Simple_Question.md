---
title: "UML packages + Simple Question"
date: 2005-10-28
forum: General Help
---

### Post by k_smolka on 2005-10-28
Ok guys

Bit of a newbie with ubuntu.

Have been looking for a graphical UML package similar to visio. Have come across a package called dia. 

Have had a look at the readme and have checked on the web site and i think i have all required packages required

when i run ./configue i get the following error message:
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

Does this mean i am missing a c++ complier. 

Can some one suggest how to get around this.

If anyone has any better packages they know of i would be more that greatful.
many thanks

would list the config.lof file but its massive

---

### Post by LorenzoD on 2005-10-28
Dia is in the repositories so a simple apt-get install dia should do. If you want a gnomeified version, use apt-get install dia-gnome instead.

Dia is a diagram drawing application. It can draw UML diagrams as well, but it's support for UML is limited compared to a "real" UML application. If you have kde, you may want to look at umbrello. On the Gnome side, MonoUML looks promising, but needs some work yet. There is also ArgoUML, which is written in Java.

---

### Post by MarcDM on 2005-10-28
how about installing dia from the repositories? 

I'm not sure which one it's in, but I have universe and multiverse enabled. 
I use the one from there, and it works well. 

You can also try grabbing dia2code from the repositores as well. It converts dia uml diagrams into C++/C/Python and a couple others.

Marc DM

PS. When I say repositories I mean check Synaptic

---

### Post by blawson327 on 2005-10-28
i have been using Umbrello for some school work this semester it seems pretty good for what we have been doing. We did end up using dia for one section that Umbrello didnt handle. Umbrello is in the repositories and i have it running under gnome.

---

### Post by joncheyne on 2006-04-28
Hi

Other than those in the repositories, there are a couple of tools worth looking at.

[Poseidon]("http://www.gentleware.com") is the souped up version of ArgoUML and is available for free for personal use. Not free software though but the most functionality you can get for free as in beer. On Dapper I find it less stable than on Breezy and it is a massive java app so can be a bit sluggish

[ArgoUML]("http://argouml.tigris.org/") is similar but behind on some diagram types (no Swim Lanes last time I looked whereas Poseidon has a great implementation of these). Open source though and may be in one of the less supported repos.

My fav though is [UMLet]("http://www.umlet.com/") which is a very lightweight tool but amazingly useful none the less. It acts more like a sketch pad for uml drawings rather than a full project repository. Onve you get the hang of the double click to copy interface it is really fast.

Hope this helps

Jon

---

