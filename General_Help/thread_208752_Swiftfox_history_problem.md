---
title: "Swiftfox history problem"
date: 2006-07-04
forum: General Help
---

### Post by DREMA on 2006-07-04
I have a problem with my swiftfox/firefox, the history doesnt work, every time I close my browser all the adresses just dissapear, I double checked the settings and is suposed to store the adresses, any idea about this?
Thanks!

---

### Post by aysiu on 2006-07-04
Try this: ```
sudo chown -R drema:drema ~/.mozilla
``` and then restart Swiftfox.

---

### Post by DREMA on 2006-07-04
Nope, I still have the same problem, I can't figure where is the problem, because the autofill and my stored user/pass works perfect.

---

### Post by bollix47 on 2006-07-04
I know you said you checked your settings but take a look at:

tools - options - privacy - settings

Make sure the Clear Private Data settings don't include history.

Also, remember history pages (tools - options - privacy - history) should be more that zero.

---

### Post by DREMA on 2006-07-04
Nop, everything seems to be fine, I have unchecked the history browsing on the clear private data, besides, Its supose to ask when to clear my data. I have more than zero on the history. 

Its pretty wear, but surely its just a stupid thing, jeje

---

### Post by bollix47 on 2006-07-04
Have a look at [this]("http://forums.mozillazine.org/viewtopic.php?t=435137&highlight=history").  
If that doesn't help try searching for history problems in the firefox forum. That's how I found the above.

---

### Post by DREMA on 2006-07-08
jaja this is very weird, I was looking for a solution on the firefox forums, and suddenly the history works, I close my swiftfox by an error an then open it again to keep searching and the history bar just works :shock: I didn't do anything

---

