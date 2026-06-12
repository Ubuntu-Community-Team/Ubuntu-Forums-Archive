---
title: "galeon and firefox crash on certain pages"
date: 2007-06-19
forum: General Help
---

### Post by phazei on 2007-06-19
I'm not sure how long the problem has persisted, but I just noticed it.
I'm a webdeveloper  and I noticed on the backend of one of my clients sites firefox 2.0.0.4 kept closing with no notice on particular pages.
To try to get to the pages I installed Galeon 2.0.2 and had the same problem.
The Epiphany Gnome browser, what I'm using now, works fine.

It's not just those pages though.  I found out while writing this post that if I hit either space bar or enter in this editing box using both Galeon or Firefox, they crash; but just typing letters works just fine.  But if i use the RTE text editor here: [http://freetextbox.com/demos/](http://freetextbox.com/demos/)  they have no problems.

Also if I do a google search for "rpm" they close as they're loading the pages.

I'm really clueless as to what could cause this.  youtube.com works just fine so I guess it's not a flash problem.
More probably causes them to crash, but that's what I've found so far.
Any help would be appreciated.

Thanks,
   Adam

---

### Post by Crafty Kisses on 2007-06-19
> **phazei said:**
> I'm not sure how long the problem has persisted, but I just noticed it.
I'm a webdeveloper  and I noticed on the backend of one of my clients sites firefox 2.0.0.4 kept closing with no notice on particular pages.
To try to get to the pages I installed Galeon 2.0.2 and had the same problem.
The Epiphany Gnome browser, what I'm using now, works fine.

It's not just those pages though.  I found out while writing this post that if I hit either space bar or enter in this editing box using both Galeon or Firefox, they crash; but just typing letters works just fine.  But if i use the RTE text editor here: [http://freetextbox.com/demos/](http://freetextbox.com/demos/)  they have no problems.

Also if I do a google search for "rpm" they close as they're loading the pages.

I'm really clueless as to what could cause this.  youtube.com works just fine so I guess it's not a flash problem.
More probably causes them to crash, but that's what I've found so far.
Any help would be appreciated.

Thanks,
   Adam

You might want to check the processes you have running at the time of the crash, and see hw much the CPU% usage is.

---

### Post by phazei on 2007-06-21
It occures on a fresh boot without anything extraordinary running.
CPU usage isn't abnormal, it spikes to like 50% for a moment when firefox/galeon closes.
If I do a search for 'tire' it also closes.  I'm not sure what google shows differently when I do a search for 'rpm' or 'tire' but it appears to be consistent.

I'm using libcurl4 since I needed it to run curlftpfs since libcurl3 (7.15.5) has issues with curlftpfs.  That's the only major change I've done to the system since installing it.  Don't think firefox uses that library though, at least not from what i could find.

Is there any way for me to have firefox run in some debug mode that can find exactally what call causes it to close?

---

### Post by erikas_boy on 2008-01-06
I get the same problem with FireFox 2.0.0.11 on Gutsy, but so far only on one online game i play.  Yahoo mail and Gmail cause no problems.  I can use SeaMonkey with no troubles at all.  Fwiw it only started after I moved up from Feisty this past weekend.

---

### Post by jpoRS on 2008-03-21
I have the same problem in Firefox and OpenOffice, and it is just since I started to upgrade to Gutsy.

Any fixes yet?

jim

---

### Post by Propwash on 2008-03-22
Hi
I have the same problem with Firefox and Gutsy. The Firefox crashes are specific - in other words they occur on the same web page and I can reproduce them.  I have had the error console on and I've noticed that there is a fair amount of warnings while Firefox loads the web pages that cause the crash.  I think it has something to do with Firefox itself or a library shared with the other apps mentioned earlier in this post.  I've turned off Java and Javascript and still no joy - same thing happens on the web pages that bombed before.  My system is vanilla Ubuntu and its up to date with all patches.  Anyone have ideas on this?  What is different about Epiphany yet the same with Galeon and Firefox?  This behaviour is not evident on my Vista or Windows XP machines nor have I seen it with my Debian linux machine.  
Regards
Gutsy (7.10)/Firefox 2.0.0.12/Gnome 2.20.1/Toshiba Satellite 186M, Celeron

---

