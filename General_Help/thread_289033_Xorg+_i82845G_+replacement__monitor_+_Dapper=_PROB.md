---
title: "Xorg+ i82845G +replacement  monitor + Dapper= PROBLEMS!"
date: 2006-10-30
forum: General Help
---

### Post by s_26_c on 2006-10-30
Well here I am facing a bizzare problem which has made me to post here the first time!!! I had my Dapper installation up and running just fine for the last 4 months or so. The problem started when I broke my monitor a few weeks ago. My machine vendor did provide me with a free replacement monitor, but I suspect now that they dumped an old stuff on me!:(  When i tried to test the new monitor, the Ubuntu logo appeared and everythng began loading, but then.....nothing!!! I mean nothing but a pitch black screen!!!!
In the following weeks , I'v done everythng possible to get my new (old!) monitor to work wth Linux, but to little avail. I'v tried to reconfigure Xorg using 'dpkg-reconfigure xserver-xorg',
by putting appropriate driver (I chose the generic i810 driver for my Intel 82845G integrated card as I had done before, and had worked wth my previous monitor),and gave the correct Horz and Vert frequency ranges for my new monitor( 30-54 & 50-160 resp., as per the label at the back of the monitor)...but dat dint help!! I issued 'startx' but got no display!!  I pressed ctrl+alt+bcksp to hault X, and found dat there were no errors(EE) or warnings (WW) there!!
  I even tried to install sum other distros like Gentoo, Vector Linux, etc., and tried sum LiveCDs as well(including Ubuntu/Kubuntu Live CD). But none of them  worked...they all gave back the same black screen problem. ](*,) 
 Then , I gave a try with Debian!!! To my surprize, it worked like a charm!!! and Debian uses xfree86!!!
So i was thinking, has xorg got sumthng to do wth my problem???
I am far from being a geek,I'm just a layman who happens to be a linux afficionado....so plz give sum easy solution to my problem (if possible ,dat is!!!)

---

### Post by ahaslam on 2006-10-30
> **s_26_c said:**
> I'v tried to reconfigure Xorg using 'dpkg-reconfigure xserver-xorg'
Did you **sudo** that?

Tony.

---

### Post by s_26_c on 2006-10-31
of course!!! 'sudo dpkg-reconfigure xserver-xorg'
If i chose the generic VGA driver, I do get a X, but with terrible display!!!

and also i'm sure i entered all the relevant informations correctly!! You see, all the same options worked fine with Debian, but NOT with Ubuntu dapper!!! This leads me to believe that the problem  is infact with xorg. 
Is there any way I can revert to xfree86 instead of xorg as my xserver??? I know that Xfree86 is no more Free-as-in freedom, but still.....

---

