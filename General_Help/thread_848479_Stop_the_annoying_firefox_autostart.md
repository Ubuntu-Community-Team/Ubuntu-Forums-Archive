---
title: "Stop the annoying firefox autostart"
date: 2008-07-03
forum: General Help
---

### Post by Redsandro on 2008-07-03
I run a lot of Ubuntu's, but I'm new to (modern) **Xubuntu**. Somehow, **firefox** starts every time I log in with that *"restore session?"* dialog. I don't want firefox to start at all.

I have checked **Apps > Settings > Config Manager > Autostarted Apps** but it's not there. I checked **~/.config/autostart**, not there either. Any other place autostarts are hidden?

---

### Post by domoronic on 2009-01-31
I have had the same problem. I am not running "restore session" and have tried everything. I am completely lost on how to remove firefox from starting. I have tried in sessions under autostarted apps. 

I am running xubuntu 8.10.

---

### Post by tom66 on 2009-01-31
When shutting down, make sure you uncheck the 'Save session for future logins' checkbox.

---

### Post by domoronic on 2009-01-31
I have made sure not to check "Save session for future logins" and removed all autostarted apps but it still loads every time.

---

### Post by cd-r80 on 2009-02-03
Me too. I have mobloquer, orage, starting & cannot find where to stop them?

---

### Post by domoronic on 2009-02-05
I have tried everything this is getting really annoying. I know it's probably something really simple but i just can figure out how to remove it. Firefox and Yakuake start automatically. i have checked my HOME/.config/autostart folder and there i nothing that even mentions them in there. Is there another script or file that loads up on startup. I even greped for files with firefox in them but i'm a little out of my depth there.

I created a new user and it didn't start up then. I am thoroughly confused now.

---

### Post by domoronic on 2009-02-06
I have worked out thanks to mr google how to get rid of this.

If you exit everything and then restart, ticking the box marking "save session for future logins" then it'll load up all shiny and new. Next time you restart make sure you untick the box again. I'd still like to know how to do it manually but there you go. Hope this helps.

---

### Post by cd-r80 on 2009-02-11
Did not work for me. Still autostarting.

Oh! I removed it also from the panel & they stopped jumping on my face. Allthought I wanted them to stay in the panel.

---

### Post by peakshysteria on 2009-02-11
Check out: [[COLOR="Red"]Session Restore[/COLOR]]("http://kb.mozillazine.org/Session_Restore")

Or install [*][Tab Mix Plus](http://tmp.garyr.net) 0.3.7.3

---

