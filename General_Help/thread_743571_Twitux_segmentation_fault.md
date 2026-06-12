---
title: "Twitux segmentation fault"
date: 2008-04-02
forum: General Help
---

### Post by InspirationDate on 2008-04-02
I installed [Twitux 0.60 from getdeb]("http://www.getdeb.net/release.php?id=1896").  It starts fine but when I try to connect or go into the account menu, the program crashes and I get "Segmentation fault (core dumped)" in the terminal.

Can anyone suggest something I could do to help me debug this problem?  I figure everything will be fixed when I upgrade to Hardy and install 0.61 but I'd rather not wait if I don't have to.

---

### Post by subratabera on 2008-04-10
Try this-->

Delete the following folder

 ~/.gconf/apps/twitux 

and then run twitux, goto settings-->Account. Enter your account details. 

Login.

Hope this helps.

---

### Post by InspirationDate on 2008-04-10
Ah man!

I was sure that was the first thing I tried... but I did it again and it worked!
Thanks ever so much!

---

