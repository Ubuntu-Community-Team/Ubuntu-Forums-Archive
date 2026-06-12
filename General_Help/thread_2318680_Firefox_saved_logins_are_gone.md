---
title: "Firefox saved logins are gone"
date: 2016-03-28
forum: General Help
---

### Post by PaulBx on 2016-03-28
In a recent upgrade, apparently, my saved logins have disappeared. Or maybe it happened when I lost power a couple of weeks ago. I just don't have them any more. I re-entered a couple to make sure it still works, and it does.

I found nothing about this in a search here or generally.

Looking in the .mozilla directory, nothing jumps out at me. I have a /home/paul/.mozilla/seamonkey/mjgcmg3t.default that I copied over to /home/paul/.mozilla/firefox/mjgcmg3t.default when I transitioned from seamonkey to firefox half a year ago, and seamonkey still has the saved logins (except for the recent ones of course). Perhaps I could copy them over again if I knew what file to copy, but again that leaves out the recent ones.

Anybody have some suggestions?

---

### Post by coldraven on 2016-03-28
From Mozilla help:
[https://support.mozilla.org/en-US/kb/recovering-important-data-from-an-old-profile](https://support.mozilla.org/en-US/kb/recovering-important-data-from-an-old-profile)


> [h=2]Passwords[/h] Your passwords are stored in two different files, both of which are required: 
 
[LIST]
[*] key3.db - This file stores your  key database for your passwords. To transfer saved passwords, you must  copy this file along with the following file.
[*] signons.sqlitelogins.json - Saved passwords.
[/LIST]


---

### Post by PaulBx on 2016-03-28
Apparently signons.sqlitelogins.json is the old way. Now saved in logins.json.

I see a file logins.json with my 3 recent passwords saved, and another file logins.json.corrupt with the old ones. It is 172k. I tried copying the .corrupt one back to logins.json but firefox just renamed it to  logins.json.corrupt again and I saw no passwords. Strangely I can't open this file with geany but I can use "less" to read it and I see old passwords in it (I don't use a master password). I might get most of them from the old seamonkey profile but that one is 160k so I'd be missing the recent ones. I can't find anything to recover the logins from the corrupt file unfortunately. Oh well!

---

### Post by PaulBx on 2016-03-28
OK, I looked at the structure of my new logins.json with the 3 logins (adding a CR for each login, just to see it better). This showed me what the file was supposed to look like. Then I made a copy of my old seamonkey logins.json. Then I did "less" on my logins.json.corrupt, and went to the end of that file where the new entries were. I cut out those entries, and pasted them in the appropriate place at the end of my seamonkey copy. At the beginning of the file is a "nextId" field that I updated because I now had those extra entries - one higher than the number of the last entry. Then I copied that seamonkey copy back to my firefox profile, started up firefox, and now I have my logins back, including the new ones!

It looked like a long shot but I thought it was worth a try. Apparently the corruption was somewhere in the earlier entries. 

I guess I had better revisit my backup strategy. Not too helpful to have a dd copy of my whole (encrypted) disk...

---

