---
title: "How to mount cifs with special chars in username?"
date: 2007-04-14
forum: General Help
---

### Post by yang on 2007-04-14
No mention of how to do this in the man page.

I tried:

```

mount ... -o 'user=John\\ Smith,ip=...'
mount ... -o 'user=John\ Smith,ip=...'
mount ... -o 'user=John Smith,ip=...'
mount ... -o 'user="John Smith",ip=...'

```

Nothing seems to be working. I am able to use a user with no spaces in his name though.

---

