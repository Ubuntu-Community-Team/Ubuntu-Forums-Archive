---
title: "Firefox won't load my home pages"
date: 2007-05-03
forum: General Help
---

### Post by Nate7679 on 2007-05-03
When I try to load any pages that I had set as my home pages, the tab says "Loading..." and never loads the page. Sometimes it will say "Stopped" in the bottom bar for those tabs. The weird thing is that even after I restored the home page to the default, it will not load those specific pages that I had set as my home pages. 

I've tried

-Clearing all the browser data
-starting firefox in safe mode
-stopping my firewall (firestarter)

and nothing has worked. this is a really strange problem and I can't access any of my favorite sites. what else should I try?

Thanks

---

### Post by imdidactic on 2007-05-03
what pages are you trying to set as your home?  if they're personal pages, perhaps it's an issue with the host of the site?  without any specifics the best i can tell you is to remove and reinstall firefox.

Open a terminal.

sudo apt-get remove firefox
sudo apt-get install firefox

Maybe this will fix the problem for you.

---

### Post by Nate7679 on 2007-05-03
The only problem with that is then I have to re install all of my add ons and greasemonkey scripts which would be a pain. And I don't even know if that would fix the problem, so i'm not doing that yet.

---

### Post by ap9er on 2007-05-03
You won't lose your settings or addons, they should stay in .firefox in your home directory (which you could back up easily by copying the folder to a remote location).

I'm having the same problem in that certain sites won't load for me. But it's for all browsers, not certain if it is a DNS or Router or Ubuntu fault.

I've tried disabling ipv6.

edit: tried a different router, same result. Narrowed down my ISP's DNS or some weird Ubuntu configuration gone wrong. (Sites work using a proxy.)

---

### Post by Nate7679 on 2007-05-03
Thanks for your help. I reinstalled firefox and now its working fine.

---

