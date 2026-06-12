---
title: "Help me make a script to stop a user from openning two instances of skype"
date: 2007-04-07
forum: General Help
---

### Post by seshomaru samma on 2007-04-07
i installed dapper on my mom's computer and everything is fine
except there is a considerable gap between the time she clicks on the skype icon and the time it actually loads. she then clicks on it again and again and the next thing you know 5 instances of skype open with error messages.
is there a way to make sure that any extra skype session is killed instantly?

---

### Post by yabbadabbadont on 2007-04-07
```
#!/bin/bash
if [[ -e /tmp/skype.running ]]
then
    exit 0
fi

touch /tmp/skype.running

exec skype

rm /tmp/skype.running
```

---

### Post by seshomaru samma on 2007-04-07
thanx

---

