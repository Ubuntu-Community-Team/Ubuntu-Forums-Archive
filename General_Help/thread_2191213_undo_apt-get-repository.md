---
title: "undo apt-get-repository?"
date: 2013-12-01
forum: General Help
---

### Post by bschilke.biz on 2013-12-01
I ran an apt-get-repository command and want to wait on installing the tool (it's the burg bootloader).  I think I can just leave it, but is there a way to reverse it? apt-get remove?

---

### Post by ibjsb4 on 2013-12-01
PPA Purge

Its in the software center

[ATTACH=CONFIG]248232[/ATTACH]

---

### Post by mc4man on 2013-12-01
you can use -r (remove)
 sudo add-apt-repository -r ppa:whatever you used to add

Note that in 12.04 I believe it doesn't remove completely so if may be better to open software sources > other and remove or disable ppa there

---

### Post by deadflowr on 2013-12-01
Unlike other ppa such as the x-edgers ppa, which update the x packages upon running an upgrade, don't you need to actually install the burg packages?
If so, then why even bother removing the ppa, if need be simply disable it in software sources > other software.

---

### Post by bschilke.biz on 2013-12-01
The only GUI app I can find is the Ubuntu Software Center, but I am running xubuntu so maybe that's why?

---

### Post by bschilke.biz on 2013-12-01
> **mc4man said:**
> you can use -r (remove)
 sudo add-apt-repository -r ppa:whatever you used to add

Note that in 12.04 I believe it doesn't remove completely so if may be better to open software sources > other and remove or disable ppa there

Ok, this ran without errors.  Assuming it got removed.  Thanks!

---

### Post by mc4man on 2013-12-01
> **bschilke.biz said:**
> Ok, this ran without errors.  Assuming it got removed.  Thanks!

Run sudo apt-get update to make sure it completes without error
If you see some nonsense about "ain" then you'll need to manually fix that 
(what ever release of Ubuntu that has the slightly borked add-apt... will leave ain behind (as in main but it only removes the m

---

