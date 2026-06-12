---
title: "ubuntuforums crashes firefox - gutsy"
date: 2007-10-22
forum: General Help
---

### Post by bionnaki on 2007-10-22
this has been happening to my firefox. the ubuntu forums main page will freeze/crash firefox. any ideas? I dont have any extensions installed and have not made any tweaks.

does this happen to anyone else?

---

### Post by DagMan on 2007-10-22
I've never had it crash but when I first hit the site it often takes quite a while to load freezing firefox for a short while and with the processor hitting 100% the whole time until it snaps back to normal.  It's always been like that on ever computer and at least the last 3 versions of Ubuntu that I've noticed.  It's kind of funny that the support forum for the distro isn't friendly with it.  I think it's a think with Firefox and not Ubuntu though as it happened on gentoo in Firefox here as well.

---

### Post by bionnaki on 2007-10-22
yes, it is very odd.

---

### Post by bionnaki on 2007-10-22
I think it might be the javascript menu. I turned off javascript and it loads just fine - in fact, its way quicker. I'm going to look into the noscript extension and only block javascript from this forum until its corrected.

---

### Post by billstei on 2007-11-02
What I am getting with Firefox 2.0.0.8 in Gutsy is that any forum will crash if I do a Reply Post and type one letter followed by a space.  The space character crashes it (I did this posting in Opera)  I also tried turning off Javascript in Firefox, but it didn't change the issue.

Bill

---

### Post by oilchangeguy on 2007-11-02
> **billstei said:**
> What I am getting with Firefox 2.0.0.8 in Gutsy is that any forum will crash if I do a Reply Post and type one letter followed by a space.  The space character crashes it (I did this posting in Opera)  I also tried turning off Javascript in Firefox, but it didn't change the issue.

Bill

nice computer in your sig. what is it? a trs80, or commadore 64?

---

### Post by stimpack on 2007-11-02
I can cause it to crash on will, fire up ubuntuforums, new tab and load gmail in the new tab while ubuntuforums is still loading, it dies.

---

### Post by billstei on 2007-11-04
This issue is related to the spellchecker in Firefox, which runs whenever typing text into a forum (like this one).  To fix it I deleted /usr/lib/firefox/components/libmyspell.so and then updated to the latest security update firefox_2.0.0.8+2nobinonly-0ubuntu1_i386.deb using Synaptic.  It's entirely possible that you do not need to delete libmyspell.so but I did just to make sure it got reinstalled.

Bill

---

### Post by Coombabah on 2008-01-01
> **bionnaki said:**
> this has been happening to my firefox. the ubuntu forums main page will freeze/crash firefox. any ideas? I dont have any extensions installed and have not made any tweaks.

does this happen to anyone else?

Firefox has been going to near 100% CPU for a minute or so at random times whilst loading pages on Ubuntuforums.org . This has happened on a number of computers all running Gutsy. 
I have the web developer 1.14 add-on and normally have Java disabled.

I don't know if it could be related to this issue but the firefox error console reports an error,  "$ is not defined" in some javascript just after some javascript fixes for Ie6 rendering bugs on these pages.
$('q').addEvent('focus', function() {
			$('q').select();
		});

---

