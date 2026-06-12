---
title: "Different views for different terminal users"
date: 2013-03-21
forum: General Help
---

### Post by 00chilli00 on 2013-03-21
Hi all,

The issue i'm having is kind of hard to explain but i'll do my best.
I have two different accounts and for one everything is normal when I'm connected via terminal ( ssh, however same results if I am just logging in locally) 
With one, things such as tab-auto complete works, I get different colours and I also get my username before the $. I can't recall commands by pressing up either 
I have attached a screenshot as an example.

---

### Post by sudodus on 2013-03-21
Maybe the .bashrc files are different. You can check it with diff

```
diff /home/user1/.bashrc /home/user2/.bashrc
``` 
where user1 and user2 should be replaced with the real user names.

---

