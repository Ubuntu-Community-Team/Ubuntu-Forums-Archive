---
title: "How can I hide files but readable with Samba shared?"
date: 2014-11-27
forum: General Help
---

### Post by whiteking on 2014-11-27
My issue is I want to alllow users to call application and that application have to use database files, like this picture

[IMG]http://i58.tinypic.com/x0y2wx.png[/IMG]


That mean DBApp.exe have to use DBFile.DBF in DatabaseFolder when it running. But I don't want users to access or copy this DBFile.DBF, so how can I set the DatabaseFolder to invisible from users but they also can read DBFile.DBF properly?


I try to use option 'Hide Files' and "Hide unreadable" but when set the folder option of windows to show hidden files, it can still see this hidden files.


Sorry for my bad english, and thank in advance for every replies.

---

### Post by mikewhatever on 2014-11-29
Check out [Samba options]("https://www.samba.org/samba/docs/using_samba/ch08.html") for that. I think "veto files" might work for you.

---

