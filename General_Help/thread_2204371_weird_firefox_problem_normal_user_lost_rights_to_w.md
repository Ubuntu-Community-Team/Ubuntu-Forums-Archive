---
title: "weird firefox problem: normal user lost rights to write?"
date: 2014-02-08
forum: General Help
---

### Post by raspatan on 2014-02-08
Hello all!

I have a weird problem with firefox in my xubuntu 13.10.

I was normally using firefox with my user account (so no as root. I am the only user in this laptop). Previous sessions (tabs, history, bookmarks) were always saved. But suddenly, one day, when I turned on firefox, it had lost the tabs (homepage was standard ubuntu+google one), all noscript configuration, although my bookmarks and history were still there. The restore previous session was not selectable. When I reconfigured the perefernces so as to keep previous session tabs, tell sites I dont want to be tracked and other things about cookies, those were not saved. Whenever I openned firefox again, there it was the ubuntu homepage and my changes in preferences were undone. This problem seemed to me very much like a lack of writing privileges of my user. Well, to check that, I went to .mozilla/firefox/26svlojy.default/ (with thunar) and yes, several files like pref.js, sessionstore.bak, sessionstore.js, and others were locked. To be sincere, I did not enter to that folder before so I cannot tell whether they were writable before but I imagine so. To check even further, I sudo'ed firefox and yes, after selecting previous session once, my tabs were there. If I reopen firefox with sudo my tabs are there again. Still, I lost the nonscript config (apparently there was a new release) and my pinned tabs. 

So, my questions: did I suffer a change in privileges? How did that happened? How to restore it? chmod? 

Thank you all!!

---

### Post by Impavidus on 2014-02-08
Those files in .mozilla/firefox/xxxx.default/ should all be writable for the normal user. People rarely lose write permissions accidentally, but accidentally changing ownership does happen, usually from careless usage of sudo. A quick way that may fix it is```
sudo chown -R your-user-name:your-user-name ~/.mozilla
```Else, remove your profile and create a new one, you you'd have to reconfigure firefox.

---

### Post by raspatan on 2014-02-08
Thank you impavidus! That fixed the problem since now my normal user session can write the files. I still don't understand how it changed though. As you said, it might be due to careless usage of sudo, although I don't remember changing ownership at all!   Anyway, problem solved but mistery pending...  Thnks!

---

### Post by ajgreeny on 2014-02-08
You mentioned using "sudo firefox" to start FF as root (which is definitely not advisable, of course) but which also suggests that you may have been using **sudo** to start GUI applications; something that can in theory cause the sort of problem you have seen[B].

ALWAYS[/B] use gksudo, or kdesu if running kde, to start their appropriate GUI applications, never use sudo for this.  More info on this in the link **Root-Sudo** in my signature below.

---

### Post by raspatan on 2014-02-08
Thank you ajgreeny! In fact, I have been running several GUI applications from the terminal when they have no shortcut by default (I know I could create one...). I didn't know about gksudo! Great article that one you mentioned. Im will definitively start using that now!   Best.

---

