---
title: "ssh broken pipe"
date: 2017-06-24
forum: General Help
---

### Post by marchello_lippi2 on 2017-06-24
Hi all, 

I experience error on one of my ssh servers: ```
packet_write_wait: Connection to xxx.yyy.zzz.hhh port 22: Broken pipe
``` Other ssh server is like more stable. Well, maybe it is because the geographic distance to the first one is longer. 
So, is there any way to prevent mentioned error? 
Is it possible at all? 
Thanks ahead.

---

### Post by TheFu on 2017-06-24
Connection hiccups.  tmux or screen are the normal solutions. Admins use tmux/screen all-the-time, always, for every connection.  

Lots of youtube how-tos for both.

---

