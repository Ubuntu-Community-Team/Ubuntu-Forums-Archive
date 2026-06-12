---
title: "Thunderbird won't open links"
date: 2007-06-11
forum: General Help
---

### Post by srunni on 2007-06-11
Hi,

Does anyone know how to make Thunderbird open links to Firefox? I don't see anywhere in the Thunderbird preferences that I can set this option, and right now links just won't open at all. I'm running Kubuntu Feisty, if that helps.

Thanks in advance for the help!!!

---

### Post by Belyel on 2007-06-11
Does it open the link if firefox is already open?  On my systems with tbird and ffox, links in email will only open if a browser window is already open.  Not sure how to change this behavior.

---

### Post by srunni on 2007-06-11
No, for me Thunderbird doesn't open links at all. Are you running GNOME or KDE?

---

### Post by arrrghhh on 2007-10-22
so i am now experiencing this same issue.  i upgraded to gusty from feisty, and it was working... i had another issue so i just wiped my hdd and did a clean install, now this problem occurs.  any help is greatly appreciated, as this MADDENING issue has never happened before.

note: when i was running feisty, links would open in firefox no matter if it was open or not.  also note, i have FF set to the default internet browser for ubuntu...


figured it out... not sure why, but after adding the line "network.protocol-handler.app.http" to my thunderbird advanced prefs, it works... [here](http://ubuntuforums.org/showthread.php?t=502651) is that thread to salvation!

---

### Post by srunni on 2007-10-23
Well I switched to KMail a while back, so it's all good :D

---

### Post by HareBall on 2007-11-04
Did anyone ever sort this out? I am having the same deal. I can open links in from T'bird to Firefox only if Firefox is already opened. If it isn't open nothing happens.
I really don't want to switch email programs.
Also, I have just re-installed Feisty after having loads of problems with Gutsy. It was working in Feisty before I did all this. It was also working in Gutsy.

---

### Post by Maestro23 on 2007-11-04
> **HareBall said:**
> Did anyone ever sort this out? I am having the same deal. I can open links in from T'bird to Firefox only if Firefox is already opened. If it isn't open nothing happens.
I really don't want to switch email programs.
Also, I have just re-installed Feisty after having loads of problems with Gutsy. It was working in Feisty before I did all this. It was also working in Gutsy.

Works for me.  Goto System>>Prefs>>Preferred Apps

Make Thunderbird the default mail reader.

---

### Post by HareBall on 2007-11-04
That didn't work either. Still don't open anything unless I already have Firefox open.

---

### Post by srunni on 2007-11-04
Maybe this thread will help: [http://ubuntuforums.org/showthread.php?t=158290](http://ubuntuforums.org/showthread.php?t=158290) - look at the 3rd post.

---

### Post by newgalois on 2007-11-11
I'm using Kubuntu Gusty and this works for me. Only note that for Firefox 2.0, the file is prefs.js instead of user.js

---

