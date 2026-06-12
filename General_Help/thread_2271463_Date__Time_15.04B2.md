---
title: "Date / Time 15.04B2"
date: 2015-03-30
forum: General Help
---

### Post by mbott on 2015-03-30
After a fresh install of 15.04B2, I find that I cannot convince Ubuntu Unity that I do not reside in New York nor can I add additional cities to Clock.  Not a biggie, just annoying.

-- 
Mike

---

### Post by ventrical on 2015-03-30
Same here.

---

### Post by MikeMecanic on 2015-04-03
Me I'm able to change the city (from New-York to any other one) but I'm not able to add another one.  The data base seems not to be there: it's not searching for the new city.

---

### Post by mbott on 2015-04-04
I can add multiple blank locations, but there are no times associated/reported for them. My city remains New York. Thanking the powers to be that that is not the case.  :)

-- 
Mike

---

### Post by mc4man on 2015-04-04
bug here, unconfirmed (though may be elsewhere/
[https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1440157](https://bugs.launchpad.net/ubuntu/+source/indicator-datetime/+bug/1440157)

(on a live session was able to only once add a new location, tried just randomly hitting a few keys & it seems it was actually  a place - sadada

---

### Post by mbott on 2015-04-04
> **mc4man said:**
> 
(on a live session was able to only once add a new location, tried just randomly hitting a few keys & it seems it was actually  a place - sadada

That doesn't help either because I'm not in sadada.  :)

-- 
Mike

---

### Post by MikeMecanic on 2015-04-06
It's working now probably with the patch we just receive from Software Updater 6:00 eastern time.  You should mark it solve if it work for you. @[[COLOR=#000000]mbott[/COLOR]]("http://ubuntuforums.org/member.php?u=498932")

---

### Post by mbott on 2015-04-06
That's a negative, ghost rider.

Neither the Software Updater nor Synaptic updated any files at 18:30edt.  Edited to add: Do you have pre-released updates selected?

-- 
Mike

---

### Post by MikeMecanic on 2015-04-06
Yes I do and i just receive another one.  It seems to be intermittent.  Sorry for the false alarm.

---

### Post by mbott on 2015-04-06
No problem at all. When I worked in IT to live and eat, I made it a point of not adding anything "pre-released" to the systems I controlled. It has carried over into retirement. :)

-- 
Mike

---

### Post by mbott on 2015-04-24
I've been away for about a week and rather than update the beta-2, I did a fresh install. During the install, I was able to enter my location, however after reboot, I was back in New York City and was unable to change my location or add any additional clock locations.

Mike

[ATTACH=CONFIG]261507[/ATTACH]

---

### Post by mbott on 2015-05-06
Might a fix be on the horizon?

> ** Changed in: unity-control-center (Ubuntu)
     Assignee: (unassigned) => Lars Uebernickel (larsu)

-- 
Mike

---

### Post by cariboo on 2015-05-06
Moved to General Help, as we are now in the Wily testing cycle.

---

### Post by mbott on 2015-05-08
Getting closer:

> 

This bug was fixed in the package libtimezonemap - 0.4.4

---------------
libtimezonemap (0.4.4) wily; urgency=medium

  [ David Shea ]
  * Update the SVG, generated new map images, and cleaned up a couple other
    image-related issues.
  * Constrain the location when clicking in the same spot.

  [ Lars Uebernickel ]
  * Port to libsoup directly for geoname requests, fix some memory leaks and
    do not reuse GCancellables. (LP: #1440157)

 -- Iain Lane <iain.lane@canonical.com> Fri, 08 May 2015 00:18:37 +0100
Changed in libtimezonemap (Ubuntu):
status: 	In Progress &#8594; Fix Released 

---

### Post by thomasv3 on 2015-05-14
Hi all,
I am facing this [bug]("https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1440157") also about [COLOR=#333333][FONT=monospace]libtimezonemap. Can you tell me how can i get [/FONT][/COLOR][FONT=monospace][COLOR=#333333]libtimezonemap (0.4.4) from apt-get update please ?[/COLOR][/FONT]
[FONT=monospace][COLOR=#333333](Or where i can follow news/updates to check when it should be available in main repository. No emergency but as i work in a worldwide company i am used to this feature a lot ;)[/COLOR][/FONT]
[FONT=monospace][COLOR=#333333]Thanks for help.[/COLOR][/FONT]

---

### Post by mbott on 2015-05-18
Excellent question!

-- 
Mike

---

### Post by mbott on 2015-05-21
> **thomasv3 said:**
> Hi all,
Can you tell me how can i get libtimezonemap (0.4.4) from apt-get update please ?

Working on it. <=That should read I hope to have some assistance on the issue shortly.

-- 
Mike

---

### Post by mbott on 2015-05-31
Ian Hawdon said via Launchpad:
> For those who can't wait for this to be back ported into Vivid, you can grab libtimezone 0.4.4 for Wily and install it. I'm yet to see any ill
effects from doing this. If you're more paranoid, recompiling is also an option. 

For someone like me who is not quite sure the best way to do this, what is a safest way to proceed?

-- 
Mike

---

### Post by mbott on 2015-06-04
Sadi Yumu&#351;ak (sa-yu) wrote:

> Got it!

Download this (1) [https://launchpad.net/ubuntu/+archive/primary/+files/libtimezonemap-data_0.4.4_all.deb](https://launchpad.net/ubuntu/+archive/primary/+files/libtimezonemap-data_0.4.4_all.deb)
and this (2-a) [https://launchpad.net/ubuntu/+archive/primary/+files/libtimezonemap1_0.4.4_amd64.deb](https://launchpad.net/ubuntu/+archive/primary/+files/libtimezonemap1_0.4.4_amd64.deb)
or this (2-b) [https://launchpad.net/ubuntu/+archive/primary/+files/libtimezonemap1_0.4.4_i386.deb](https://launchpad.net/ubuntu/+archive/primary/+files/libtimezonemap1_0.4.4_i386.deb)
or choose other from here: [https://launchpad.net/ubuntu/+source/libtimezonemap](https://launchpad.net/ubuntu/+source/libtimezonemap)

And install these two packages with a command like this:
sudo dpkg -i "libtimezonemap1_0.4.4_amd64.deb" "libtimezonemap-data_0.4.4_all.deb"

See [https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1440157]("https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1440157")

Thanks!

-- 
Mike

---

### Post by mbott on 2015-06-04
This cleared the only issue I encountered with 15.04.  :)

-- 
Mike

---

### Post by thomasv3 on 2015-06-04
Thanks a lot mbott , this works perfectly. Nice job.

---

### Post by mbott on 2015-06-04
> **thomasv3 said:**
> Thanks a lot mbott , this works perfectly. Nice job.

Not me. Sadi Yumu&#351;ak posted the fix in the bug report.  I was just the parrot.  

-- 
Mike

---

