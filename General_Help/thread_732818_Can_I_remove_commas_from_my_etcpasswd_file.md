---
title: "Can I remove commas from my /etc/passwd file?"
date: 2008-03-23
forum: General Help
---

### Post by Adnarim on 2008-03-23
Hi,
since I upgraded to hardy I have a silly problem: [https://bugs.launchpad.net/ubuntu/+source/coreutils/+bug/205194](https://bugs.launchpad.net/ubuntu/+source/coreutils/+bug/205194) . logname doesn't show my loginname anymore.

Well I think it's related to my /etc/passwd-file. There my user has an entry like this here:
```
adna:x:1000:1000:adna,,,:/home/adna:/bin/bash
```

You see the three ,,, in this line? What do they mean? I can't remember if they existed before my upgrade but are they normal? Can I remove them?

greets

---

### Post by Hazed on 2008-03-23
Ignore this, misread your post :)

---

### Post by fsmithred on 2008-03-23
That's where your address and phone number go, if you add that information to your account. Better not mess with that file. Go to Admin -> Users & Groups to make changes.

---

### Post by Adnarim on 2008-03-23
I'm usin fluxbox so I don't have this menue. But If you say that they are normal it's unlikly that these commas are creating my problem.

greets

---

### Post by nick_h on 2008-03-23
Here is a [link](http://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/) to a description of the /etc/passwd file.

Field 5 is the comment field.  The commas are normal - no need to remove them.

---

### Post by knightcoder on 2008-03-23
Just try inserting/deleting commas for some other user (other than root) and see what difference it makes. Then go ahead removing it from the root user.

---

