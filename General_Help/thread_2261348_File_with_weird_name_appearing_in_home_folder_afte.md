---
title: "File with weird name appearing in home folder after every login"
date: 2015-01-18
forum: General Help
---

### Post by sigdrifa2 on 2015-01-18
Hi everybody,

for the first time in a long time I have a problem that Google can't solve :?.

Every time I log in, a weird file appears in my home folder. I delete it, and it won't come back during the session, but next time I log in, it's back. It's categorized as a text file, it's empty, and the name looks like it contains characters for which no font is installed, like this:

[ATTACH=CONFIG]259329[/ATTACH]

On the command line, it looks like this:
```
-rw-rw-r--   1 tanja tanja     0 Jan 18 12:41 ?p?@@x?@8
```
I'm running Ubuntu Studio 14.04, but the problem is not exclusive to XFCE; I also have KDE installed, and it still comes back, only in dolphin the name looks slightly different.

Is there a way to find out, which program created a file? Has anyone else ever run into a problem like this? This is so bizarre I don't even know how to phrase a search on Google.

Any help would be appreciated.

---

### Post by TheFu on 2015-01-18
Is it always the exact same filename?
What happens if you have root take ownership and change the permissions to 444 (readonly)?

---

### Post by sigdrifa2 on 2015-01-18
Thanks for the quick reply. I just solved it. As usual, I only got the right idea after I posted. Happens to me all the time, first I ask, then suddenly my brain decides to shift to a faster gear after all :rolleyes:

Posting the solution in case someone else runs into this problem (however unlikely.)

It was AeroFS, which for some reason I never got to work on this system, and I had totally forgotten about it. I found this out by first logging in not to a desktop but only on the command line. The file wasn't created then, so I went back to XFCE and moved everything from the ~/.config/autostart folder to a backup location and put it back file by file until I found the culprit.

---

