---
title: "view last console commands by pressing &quot;up&quot; arrow"
date: 2016-02-22
forum: General Help
---

### Post by marchello_lippi2 on 2016-02-22
Hi all, 

I'd like to view last console commands by pressing "up" arrow. 
However, I can see **^[[A** instead. 
How do I solve it? 
Thanks ahead.

---

### Post by papibe on 2016-02-22
Hi marchello_lippi2.

What Ubuntu version are you running?
Are you using the default terminal application?
Did you change your shell?

Regards.

---

### Post by marchello_lippi2 on 2016-02-22
> **papibe said:**
> Hi marchello_lippi2.

What Ubuntu version are you running?

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:        14.04
Codename:       trusty

> 
Are you using the default terminal application?

It is headless server, I log into via ssh. 

> Did you change your shell?


Nope, how can I do it? 
Thanks ahead.

UPD: I tried 

**sudo chsh -s /bin/bash myuser**


UPD2: Performed re-login and everything works fine. Thanks!

---

### Post by Habitual on 2016-02-22
I sometimes see "**^[[A" **on interactive ssh sessions. I usually just press Ctrl+C twice before doing anything else and it's all good.

---

