---
title: "Open Office"
date: 2005-07-28
forum: General Help
---

### Post by luv2cmwork on 2005-07-28
My first question is, does Ubuntu come with Open Office right out of the box?

Here's my problem.  Let me preface it, by saying I'm a newbie.

I didn't even look if Open Office was already installed and installed it, using apt-get.

Now, under Applications>Office, I have:

Evolution
OpenOffice.org 2 Base (doesn't work)
OpenOffice.org 2 Calc (doesn't work)
OpenOffice.org 2 Draw (doesn't work)
OpenOffice.org 2 Impress (doesn't work)
OpenOffice.org 2 Math (doesn't work)
OpenOffice.org 2 Printer Administration (doesn't work)
OpenOffice.org 2 Writer (doesn't work)
OpenOffice.org Drawing 
OpenOffice.org From Template
OpenOffice.org Presentation
OpenOffice.org Spreadsheet
OpenOffice.org Word Processor

So, did I install duplicate copies and screw something up?  I think I did, because they seem to be two different versions.  Or is that all the Open Office package and if so, why don't many of them work.  

Many of the programs dont' work (as indicated above).  I get the message:

******
Cannot Launch entry
Details:  Failed to execute child process "/opt/openoffice.org1.9.113/program/soffice (No shuch file or directory) 
******

Unless there is a better answer, my intent was to completely remove all Open Office through Synaptic and reinstall, using apt-get.  I looked in Synaptic and saw MANY referenced to Open Office...but hesitated to delete all of them, for fear I'd screw something up.

Any suggestions?

Thank you so much, in advance.

---

### Post by tom-ubuntu on 2005-07-28
These are the stable versions (1.1.x):
OpenOffice.org Drawing
OpenOffice.org From Template
OpenOffice.org Presentation
OpenOffice.org Spreadsheet
OpenOffice.org Word Processor

You installed the beta version of OpenOffice.org 2. I would recommend that you remove them and use the stable version.

---

### Post by luv2cmwork on 2005-07-28
Love to.  What's the best way to do that?  Either command line or synaptic...I need to know what to remove.

If it's more than you care to write, I'll try to figure something out.

Thanks!

---

### Post by GTvulse on 2005-07-28
Open Synaptic. Follow the menu: System/Administration/Synaptic Package Manager. Click on the Search button on the toolbar, type "Openoffice.org 2" without the quotes. Select all the entries with a green square and open the contextual menu by clicking the right mouse button. Select "Remove Completely" and click on the "Apply" button on the toolbar. Click yes on the confirmation dialog and poof, that old beta will be gone.

---

### Post by luv2cmwork on 2005-07-28
Easy advice...perfect.

Only problem is, I have no green squares.  Only open (white) squares.  Do I do something with them?

---

### Post by luv2cmwork on 2005-07-28
[QUOTE=luv2cmwork]Easy advice...perfect.

Only problem is, I have no green squares.  Only open (white) squares.  Do I do something with them?[/QUOTE]

Sorry...that didn't sound right...sounded kinda of smart.  Didn't mean it that way.

It does seem easy (which I would like), but it's not working.

No green squares, so I'm not sure what to do.  Probably 8 or so open (white) squares.  Should I try removing them somehow?

---

### Post by GTvulse on 2005-07-30
Did you install following the how-to thread on Installing the development versions? If so, you'd find the entries under "rpms created by alien" or something like it, off the top of my head.

Frankly, all those scripts and convoluted recipes only complicate something that is as-easy-as-pie (and only takes the time you need to download and process the files). Search for my small journal in this same forum (I still don't know a direct link to it :-)) for a right-to-the-point way of installing OOo 2 from the official distro.

---

