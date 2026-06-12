---
title: "Firefox Won't Start"
date: 2006-12-19
forum: General Help
---

### Post by Exillo on 2006-12-19
Hi, 

On my Ubuntu Edgy, I booted up today and clicked on my Gmail Notifier icon to go to my inbox (it goes to my inbox through Firefox, not Swiftfox). It just showed the 'Starting Firefox' in the window bar and then disappeared and Firefox didn't start. I tried to open Swiftfox and the same thing happened, then both of them two times more and the same thing happened. 

The only thing I can think of is yesterday when I installed Automatix2 and then installed the Firefox Flash Player plugin although I was sure I had rebooted since then and everything was fine but maybe not...

Any help in getting Firefox/Swiftfox to work would be greatly appreciated. :???:

---

### Post by bodhi.zazen on 2006-12-19
Open a terminal

type firefox

post any error messages

---

### Post by digen on 2006-12-19
In case if you still face problems starting firefox, you can remove the firefox lock file & start fireox.

The lock file should be located at /home/username/.mozilla/firefox/

Under here there should be a folder with random characters.default like for example o6yxa08d.default in my case. You should find the file "lock". Removing it and starting firefox will work.

---

### Post by hikaricore on 2006-12-19
I wonder if my firefox / swiftfox might be suffering from a similar issue.  About every 7 out of 10 times it opens on the first try, but otherwise it just disappears without even bringing up the main windows.  I may have to check error output on my system when I get home to see if it may be an issue with the lock file.  :)  I'll point the sucker to /dev/null and be done with it ehehe.

---

