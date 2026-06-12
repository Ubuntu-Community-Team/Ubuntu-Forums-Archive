---
title: "[SOLVED] unable to save"
date: 2008-03-09
forum: General Help
---

### Post by xXJT-JaredXx on 2008-03-09
i tried to upgrade from gutsy to hardy and had many problems so i reformatted back to gutsy and now i cant save anything like there are permission problems, i can only save things like documents etc. if i open them as a root user. so if anyone has any ideas that'd b great thx

---

### Post by banewman on 2008-03-09
As a check - browse to the /home folder in nautilus then right click your users folder and select properties then the permissions tab. 
If you don't own it then you can change that by typing in a terminal - 
sudo chown -Rv you:you /home/you
substitute your user name for  you
:)

---

### Post by xXJT-JaredXx on 2008-03-09
thx yeah i checked n it said i'm the owner

---

### Post by banewman on 2008-03-09
Next open from the menu -
system - admin - users and groups 
and see what access to the system you're user has.
:)

---

### Post by xXJT-JaredXx on 2008-03-09
ok its set to default, change to @admin?

---

### Post by banewman on 2008-03-09
Yes - you should have one user that can admin the system so you don't login as root - that is why the sudo command was invented. :)

---

### Post by xXJT-JaredXx on 2008-03-09
ok thx i'll give it a go

---

### Post by xXJT-JaredXx on 2008-03-09
thank you so much, i'm still pretty new to ubuntu, it all seems to be working again, thx for your help

---

### Post by banewman on 2008-03-09
Glad you got it sorted and hope you enjoy it.
:)

---

