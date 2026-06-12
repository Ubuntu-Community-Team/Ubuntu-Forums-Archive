---
title: "Google SPreadsheets slow as Mollasses for everyone!?!"
date: 2006-10-14
forum: General Help
---

### Post by mark2741 on 2006-10-14
I figured I'd check out google spreadsheets as it would be helpful to collaborate with a friend of mine on a particular spreadsheet.

So I uploaded my ods file (openOffice spreadsheet format). Google spreadsheets is *really* slow and it is using up almost all of my processor (based on the processor usage graph thingy widget on my desktop panel).

So....is it my computer? - P4 1.7ghz, 512mb ram
Browser? - firefox 1.5
Or the ods file format? - can't imagine this would be the problem as I'm sure it is converted once uploaded.

I tried to open it up in Opera to see the difference but alas, Opera isn't supported by google spreadsheets yet.

Anyone else using google spreadsheets?

I'm on dapper but will upgrade to edgy as soon as it's released.

---

### Post by gvgerman on 2006-10-14
For what it is worth, I've used it in the past and have not had these types of issues.

---

### Post by K.Mandla on 2006-10-14
> **mark2741 said:**
> Anyone else using google spreadsheets?
I use them, and I've noticed that they're likewise sluggish. It might depend on bandwidth too, so if you're on a slower connection, it might load slower. I use a couple of different machines to access one particular spreadsheet, and it's definitely slower (relatively) than others on slower machines with slower connections.

I haven't tried downloading, then editing, then re-uploading. It might streamline the process. :confused:

---

### Post by streeto on 2006-10-25
In firefox 1.0.X (ubuntu 5.10 "breezy"), google spreadsheets was usable. Some glitches here and there, but usable.

After upgrading to dapper firefox went to 1.5.X, and google spreadsheets became "slow as Mollasses".

I really don't know the cause of this. Maybe using firefox 2 in ubuntu "edgy" will fix it. I'll post my results here after upgrading.

---

### Post by joncheyne on 2006-10-26
JUst to confirm that Firefix 1.5.0.7 under Dapper is unusable for a 6 tab, 200 cell spreadsheet that works great under windows with the same version of firefox. 

Bandwidth is not the issue - on windows, works fine at 56k grps! Under Linux doesn't run with 2megs.

Watching the network useage, it downloads to the browsers at the same speed but then consumes 100% of CPU while it works out how to render the ajax layouts etc. THis can take about 30 seconds. Scrolling takes a similar toll. Tried Epiphany - same result, predictably.

I advocated the use of google spreadsheets so I could collaborate with windows users from my home and work ubuntu machines. Which I now have to run VMware on to do so - might as well just use excel!

I would laugh if it was funny. :-)

J

---

### Post by beerfan on 2006-10-26
My experience is similar to joncheyne's. Gspreadsheets is too slow to be usable in Firefox on Ubuntu but is fine on my slower windows computer using either Firefox or IE. I can add that I tried it a while back when it was still invite only and it was just as slow in Firefox on windows as it now is only on Ubuntu.

I've reported the problem to google via their feedback form so they know about it. Hopefully it will be resolved eventually.

---

### Post by joncheyne on 2006-10-26
further ... upgraded to Firefix 2.0 manually but just the same unfortunately.

On Google's FAQ, they do say that they do **not** suppport any browser running on linux at the moment. 

Ho hum. Not what I expected, for sure :-)

Anyone tried it unde KDE using konq?

---

### Post by sunitram on 2006-11-06
I have just tried the Firefox nightly build and it works very fast, no more sluggishness :-)

Get it here:
[http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/)

---

### Post by t_huankiat on 2006-11-06
I confirm that it's totally not useable in firefox 1.5 in Ubuntu.](*,) 
What seems to be the problem? Is this a purely Ubuntu version of FF or Linux in general?

---

### Post by doctorberen on 2006-12-20
Has anyone solved this mystery yet?

I'm experiencing the exact same problem.

My google spreadsheets is running very slowly on Firefox 2.0 running in Ubuntu 6.10.

If I go to my Windows computer and open the same spreadsheet using Firefox with exactly the same extensions, it is fast.

Help.

---

### Post by fourthirtysix on 2007-04-18
google spreadsheets is running very slow and sluggish on Ubuntu Feisty using Firefox 2.0.0.3

does anyone know why this is happening?

the same spreadsheet works much faster on the same computer when i dual boot into windows and use the same firefox 2.0.0.3

---

### Post by fourthirtysix on 2007-04-18
nevermind, i found what seems to be the problem at this link... excerpt below:

[https://bugzilla.mozilla.org/show_bug.cgi?id=328319]("https://bugzilla.mozilla.org/show_bug.cgi?id=328319")

> Brent Core   2007-02-11 09:20:17 PDT

I would like to add that I've experimented with this a lot and it appears to be
the combination of visiting a site that uses transparent PNGs stacked on top of
each other with CSS while not have 3D graphics card acceleration.  Many Linux
users do not have 3D graphics card acceleration due to the fact that
closed-source graphics drivers are not installed by default (and the
open-source graphics drivers capable of 3D acceleration are either alpha
quality or do not support all cards).  

The point is, this bug is not specific to only Linux users. However, Linux
users are much more likely to experience the problem due to the current
graphics drivers situation.

Basically the work of interpreting two or more stacked alpha channels is being
pushed onto the processor rather than the graphics card, essentially maxing the
proc out and bringing the entire system to a halt.  I've experienced a 100% CPU
usage just scrolling up and down on [http://www.linuxactionshow.com](http://www.linuxactionshow.com) .

Proposed solutions:

A) have an option within about:config to toggle off the display of transparent
PNGs (this is only a temporary fix for those who even know what "about:config"
is).  An extension could be developed as well, but again, this is a poor
solution.  Not everyone knows what an extension is, nor do they actually know
why web pages appear to be slow after installing Linux on their computer.

B) rethink the way Fx renders stacked transparent PNGs

C) detect when a user does not have 3D acceleration.  If it is determined that
no acceleration is present, then handle transparent PNGs differently


Obviously (C) looks like the best choice.  This is a VERY serious bug, and as
such should have top priority.  Fx cannot leave Linux users in the dust.  This
includes future One Laptop Per Child users, who will have no 3D acceleration
whatsoever.

test pages:
[http://www.digg.com/submit](http://www.digg.com/submit) (continue the submission process to the point where
you need to enter a description of the story.  CPU slowdown ensues)
[http://www.linuxactionshow.com](http://www.linuxactionshow.com)

Comment #10 Dr. David Alan Gilbert

---

### Post by benford on 2007-07-24
I can confirm that google spreadsheets are very sluggish when loading from Feisty on Firefox 2.0.0.5 (both 32 and 64 bit versions running from 64 bit Feisty). Has there been any progress in resolving this issue?

---

### Post by pofigster on 2007-07-24
Ok, I'm running Feisty with 2.0.0.5 Firefox and while Google spreadsheets is a little slower than on a windows box, it's not really that big of a deal. I do have nvidia drivers loaded, so I do have 3d acceleration (like the above article noted).  Try opening the restricted drivers manager (System >> Administration >> Restricted Drivers Manager) to install your video card drivers.  It is usable (I even loaded some 5 tab, 50 line spreadsheets and navigated them with no problem, made changes and saved the file)

---

### Post by benford on 2007-07-25
I think my problem might be related to 3d acceleration then. I'm running off an LTSP setup so I suppose 3d acceleration would be nigh impossible (even under Feisty).

---

