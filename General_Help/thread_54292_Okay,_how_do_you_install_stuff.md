---
title: "Okay, how do you install stuff?"
date: 2005-08-04
forum: General Help
---

### Post by snoochems on 2005-08-04
Hi all
I've just booted into ubuntu.  I'm a total n00b for all things non-windows.

I am determined to change this.

So, i see the firefox icon, i click on it, and am amazed that it loads up.  Wow, i thought, i'm flying.

I then do what i always do when i get firefox...i go and install 'adblock'.  I am then greeted with a screen telling me that my firefox is outdated, and that i should download and install firefox 1.06.

So i download it, and i manage to open it up.  I then double click on the file called 'firefox-installer-bin', and it starts installing.  But just as i relax, i get a message 'fatal error [-618]: Couldn't open xpistub library'

So, what now.

---

### Post by drummer on 2005-08-04
First of all, go to [http://www.ubuntuguide.org#extrarepositories](http://www.ubuntuguide.org#extrarepositories) and follow what it says there, just copy/paste/enter each line in the black boxes into a terminal window (Applications > System Tools > Terminal). You can then go into Synaptic (System > Administration > Synaptic Package Manager), search for firefox and select the update option when you right-click the firefox entry, then click apply.

Also have a look at the rest of the Ubuntu Guide for instructions to get multimedia codecs, java and heaps more working, it's really easy to set Ubuntu up if you follow the guide. Almost everything you will need you can get from synaptic and apt-get (synaptic is just a graphical front-end to apt-get).

EDIT - there is also a bug in the firefox shipped with Ubuntu where the version number isn't actually the version it is, not sure if this is fixed in the version you will get from synaptic. If firefox still complains about the version not being right when installing extensions, go to "about:config" in firefox, type in "extensions.lastAppVersion" (without quotes) next to 'Filter' and change the 'Value' to 1.0

---

### Post by Lord Illidan on 2005-08-04
Hi..
If you are a n00b, you have come to the right place..I was a n00b too..and I still am, in some ways..

Make sure that after you have enabled the respositories, you take a look at synaptic, so that you can see what packages are available for installation.

---

### Post by nanospire on 2005-08-04
The first couple of months are the hardest.  I am eternally grateful fot this site:

[http://ubuntuguide.org](http://ubuntuguide.org) 

This is a step-by-step guide on how to install the most important applications.

---

### Post by snoochems on 2005-08-08
Thanks guys,  

But what exactly are the repositories?  I've 'turned them on', but i still dont understand what exactly they are.

---

### Post by chazm on 2005-08-08
[QUOTE=snoochems]Thanks guys,  

But what exactly are the repositories?  I've 'turned them on', but i still dont understand what exactly they are.[/QUOTE]


They're like mirrors that hold all sorts of software and/or upgrades. After uncommenting the lines in sources.list, open a terminal and type: sudo apt-get update, and then sudo apt-get upgrade. You'll see all the packages that need updating, if any.

Glad to see another person adventuring into Linux, it's really great when you get used of it :)

---

### Post by DirtDawg on 2005-08-08
[QUOTE=snoochems]Thanks guys,  

But what exactly are the repositories?  I've 'turned them on', but i still dont understand what exactly they are.[/QUOTE]

Think of the repositories as a big, online software store with hundreds of products in stock and they're all free of charge. 
Pretty cool, eh?

---

### Post by snoochems on 2005-08-09
Cool as thanks ppl

---

