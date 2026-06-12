---
title: "problem loading g++-4.0 and libstdc++6-4.0-dev"
date: 2007-07-26
forum: General Help
---

### Post by sumanta on 2007-07-26
Hi! 
I have gotta problem loading g++.
When I was trying to install g++-4.0, it required libstdc++6-4.0-dev.
Now when I tried to install libstdc++6-4.0-dev it required g++-4.0.
This is a some kind of deadlock situation.
 I also tried by dpkg --force, but it didn't work.

Please try some solutions.

All the best 
 Sumanta

---

### Post by LaRoza on 2007-07-26
This will install g++ and all headers.
```

sudo aptitude install build-essential

```

---

### Post by sumanta on 2007-07-27
Many many thanks!
It's working fine.

Sumanta

---

