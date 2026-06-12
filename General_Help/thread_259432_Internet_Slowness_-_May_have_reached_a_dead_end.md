---
title: "Internet Slowness - May have reached a dead end"
date: 2006-09-17
forum: General Help
---

### Post by itrevorevans on 2006-09-17
Hi folks, please hear me out. I understand that this topic may have been exaustively addressed before, but none of the solutions seem to work for me.

I have been using ubuntu for a little over two years now, and never have I dealt with an internet that slow before. It's not slow per se, but it takes more than 10 minutes to resolve an address, and that's not feasible for me, and so I've been using windows for all my browsing work (who would have thought?).

I have disabled IPv6 globally, and explicitly entered my DNS entries, and nothing seems to work, and I'm growing hopeless with time.

For what's it worth, I'm connected to a Linksys router via a 2200BG wireless card, and I would greatly appreciate additional pointers on this matter.

Cheers,
Trev

---

### Post by ajgreeny on 2006-09-17
Is it slow as this when you use the ubuntu live CD?  If it is then it could be your hardware. Can't imagine why it should be so slow, however)  if not then perhaps it is something to do with your browser or network connection.
Try completely uninstalling your browser (purging it totally), having first backed up your bookmarks but not your config files as they may be the source of your problem. Then reinstall the browser and see if it solves the problem.  If you are using firefox it could be one or more of the extensions you have installed, so add then again one at a time and see which, if any, cause the prioblem.

If it's your network connection, then I'm afraid someone better able to help you is needed.  Good luck!

---

### Post by coffeecat on 2006-09-17
A couple of thoughts. You say you have been using Ubuntu for over two years. Has the internet been slow in Ubuntu all that time? If not, what changed when the internet became slow?

I'm using a Linksys router and my laptop has a 2200BG chipset and I have no problems with the internet with this combination. Having said that there are several Linksys routers and I wonder if this might still be an IPv6 problem despite your having tried to disable IPv6 system-wide. The reason I say this is that on [this thread](http://www.ubuntuforums.org/showthread.php?t=87798&) there is a howto at the beginning, but later into the thread some people report that this doesn't work in Dapper and there are suggestions for what is needed in Dapper. Perhaps whatever you did didn't actually disable IPv6. Might be worth looking into. Also - have you tried disabling IPv6 in Firefox? It's a quick and easy way to check if this is the problem. Briefly, in case you don't know this, type 'about:config' into the FF address bar. (No quotes). Then 'ipv6' into the filter. Now change the value 'false' to 'true' in the one line that appears. (Right- or double-click.) Now close and re-open firefox.

---

### Post by itrevorevans on 2006-09-17
Thanks for your replies, ajgreeny and coffeecat.

> **ajgreeny]Is it slow as this when you use the ubuntu live CD? If it is then it could be your hardware. Can't imagine why it should be so slow, however) if not then perhaps it is something to do with your browser or network connection.[/quote]

You know, that's actually a good idea. I don't have the latest Live CD though (never got around to burning one), but I have a Hoary one which should do the trick, ie. eliminate the possibility of a hardware conflict.

> Try completely uninstalling your browser (purging it totally), having first backed up your bookmarks but not your config files as they may be the source of your problem. Then reinstall the browser and see if it solves the problem. If you are using firefox it could be one or more of the extensions you have installed, so add then again one at a time and see which, if any, cause the prioblem.
I actually did uninstall Firefox 1.5 and reinstalled it afterwards said:**
> A couple of thoughts. You say you have been using Ubuntu for over two years. Has the internet been slow in Ubuntu all that time? If not, what changed when the internet became slow?

Hmm... the speed dropped a few weeks after upgrading Breezy. The internet has never been slow before, ever. In fact, I fell in love with Warty because it was very smooth when it comes to wireless connectivity.

> I'm using a Linksys router and my laptop has a 2200BG chipset and I have no problems with the internet with this combination. Having said that there are several Linksys routers and I wonder if this might still be an IPv6 problem despite your having tried to disable IPv6 system-wide. The reason I say this is that on this thread there is a howto at the beginning, but later into the thread some people report that this doesn't work in Dapper and there are suggestions for what is needed in Dapper. Perhaps whatever you did didn't actually disable IPv6. Might be worth looking into. Also - have you tried disabling IPv6 in Firefox? It's a quick and easy way to check if this is the problem. Briefly, in case you don't know this, type 'about:config' into the FF address bar. (No quotes). Then 'ipv6' into the filter. Now change the value 'false' to 'true' in the one line that appears. (Right- or double-click.) Now close and re-open firefox.

I actually did read that thread, to the point that `ip a` stopped listing anything corresponding to IPv6. And firefox has ipv6 disabled, too. Unfortunately, everyone seemed to have their slowness issues gone by one of these two solutions, and there's no mention of any other possibility at fixing this. It could perhaps be Firefox, but then Opera operates at the same level.

Would appreciate additional pointers. Meanwhile, I shall try my Hoary Live CD.

Much thanks,
Trevor

---

### Post by kuja on 2006-09-17
I've been having problems with the dns resolution taking for what seemed like ages myself too. Fortunately, I've found something that seems like a worthwhile solution. I added my router (192.168.1.1) as the primary dns server in my network settings. Worked like a charm for me.

---

### Post by itrevorevans on 2006-09-18
Thanks for the advice, kuja, but unfortunately that didn't yield any difference.


ajgreeny, Hoary Live CD works just as great as Windows. That doesn't mean I should revert back to Hoary now does it?

---

### Post by bikeboy on 2006-09-18
Not sure if it's possible for you right now but I would look at downloading the edgy knot 3 and running that live before you look at reverting. Then you can see whether the next version of Ubuntu is going to resolve your problem.

---

### Post by ajgreeny on 2006-09-18
When you uninstalled firefox did you do a complete uninstall including the configuration files.  I can't remember the terminal command to do it with apt-get but in synaptic it is something like "Mark for complete removal" when you click on the installed package in the list.  This will remove everything related to firefox so make sure you have a copy of your bookmarks etc, but not other config files which might be the problem.

Another thought - have you tried downloading epiphany or something else and seeing whether that is also slow.  If it is OK then it must be just firefox.  Similarly, when you use apt or synaptic what speed is your download there?  If that is OK, then it again must be firefox at fault.

---

### Post by kuja on 2006-09-18
> **ajgreeny said:**
> When you uninstalled firefox did you do a complete uninstall including the configuration files.  I can't remember the terminal command to do it with apt-get but in synaptic it is something like "Mark for complete removal" when you click on the installed package in the list.  This will remove everything related to firefox so make sure you have a copy of your bookmarks etc, but not other config files which might be the problem.

Another thought - have you tried downloading epiphany or something else and seeing whether that is also slow.  If it is OK then it must be just firefox.  Similarly, when you use apt or synaptic what speed is your download there?  If that is OK, then it again must be firefox at fault.

With apt-get, it would be "sudo apt-get remove --purge firefox"

---

### Post by ajgreeny on 2006-09-19
Thanks kuja, I had looked it up after posting, but not got around to replying again.

---

