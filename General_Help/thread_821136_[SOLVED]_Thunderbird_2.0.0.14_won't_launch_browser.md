---
title: "[SOLVED] Thunderbird 2.0.0.14 won't launch browser (hardy heron)"
date: 2008-06-06
forum: General Help
---

### Post by tomjennings on 2008-06-06
I can't get thunderbird 2.0.0.14 to launch a web browser when I click a URL in email. Nothing Happens. There seem to be some occurances of this problem in much earlier versions, but none in Hardy Heron I could find.

update-alternatives show that x-www-browser is set to /usr/bin/firefox-3.0, and that is the correct binary for firefox.

Thunderbird's Preferences --> Advanced --> Config editor had no occurrence of network.protocol-handler.app.html so I added it manually (to x-www-browser). Quit/restarted Thunderbird, still no work. 

I installed Thunderbird a week or so ago, no other problems. apt-get install, etc. I'm running ubuntustudio, 
tomj@zx:~$ uname -a

Linux zx 2.6.24-18-rt #1 SMP PREEMPT RT Wed May 28 23:38:58 UTC 2008 i686 GNU/Linux


I'm stumped. Any ideas?

---

### Post by NT4usB on 2008-06-07
Is System>Preferences>Preferred Applications (or, whatever the Hardy equivalent is) set to Firefox and Thunderbird?

---

### Post by tomjennings on 2008-06-07
> **NT4usB said:**
> Is System>Preferences>Preferred Applications (or, whatever the Hardy equivalent is) set to Firefox and Thunderbird?

AARGH! NO! It was set to "custom"! No string shown. Set to firefox and lo! it works. Sheesh! 

Thanks!!! Man, Gnome is getting too complicated!! Too much trivia!

---

### Post by NT4usB on 2008-06-07
be sure to mark the thread solved in thread tools.

---

### Post by tomjennings on 2008-06-07
> **NT4usB said:**
> be sure to mark the thread solved in thread tools.

Aha! Thanks again, will do!

---

