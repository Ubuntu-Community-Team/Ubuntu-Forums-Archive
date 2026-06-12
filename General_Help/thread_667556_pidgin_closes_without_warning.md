---
title: "pidgin closes without warning"
date: 2008-01-14
forum: General Help
---

### Post by .Michael on 2008-01-14
Pidgin will be happy as can be doing what it does best.

All of a sudden, it closes out as if I did it manually. This happens all the time. Its frustrating when you're in a chatroom or in an im convo, and pidgin suddenly closes out.

I got the latest version of Ubuntu.
I didn't change anything about pidgin since install of Ubuntu.

But I do have quite a bit of logs(from Chats and Im's). Could that cause it?

---

### Post by .Michael on 2008-01-14
bump!

I ran it in a terminal and its last words were:
> (19:45:04) cap: Max Message Difference timeout occured
(19:45:04) cap: SELECT * FROM cap_msg_count WHERE buddy='yada' AND account='immichaelkthx' AND protocol='prpl-aim' AND minute_val=1182;
(19:45:04) cap: SELECT * FROM cap_status_count WHERE buddy='yada' AND account='immichaelkthx' AND protocol='prpl-aim' AND status='available';
(19:45:28) cap: Max Message Difference timeout occured
Segmentation fault (core dumped)


---

### Post by Wolvenhaven on 2008-06-20
I got the same problem, I don't even know where it came from because it started after a reboot(nothing was installed or updated).  I get the segmentation fault when I type pidgin in terminal and from the GUI it just runs and crashes.  I can only get it to work correctly by running it as root but that's a security issue.

---

### Post by saurish on 2008-07-07
I have the same problem! It started today. Everything was fine earlier. Don't know what caused it.

---

