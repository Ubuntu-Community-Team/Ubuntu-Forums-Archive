---
title: "Change ownership to root.root"
date: 2008-02-18
forum: General Help
---

### Post by Sergeantfour on 2008-02-18
I've tried to change my "docs" folder from <user> to <root> ownership using

sudo chown root.root /tmp/docs/

and different variations of the same with absolutely no luck.  Keeps telling me that the Operation's not permitted.  It's for Java too, which I could come in handy later...

Keeping in mind that I'm an utter Newb, would someone be kind enough to hook a brother up?

---

### Post by JangMunho on 2008-02-18
it seems should be:
sudo chown -R root:root /tmp/docs/

notice that it's " : " rather than " . " ...

---

### Post by Sergeantfour on 2008-02-18
Thanks a lot!

---

### Post by pointone on 2008-02-18
Just FYI, the /tmp folder is usually cleared on each restart. If "docs" stands for documents, you may want to move them somewhere else if you plan on keeping them. :P

Otherwise, please ignore my ramblings.

---

