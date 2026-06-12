---
title: "Port 25 in use - But where?"
date: 2008-02-06
forum: General Help
---

### Post by pfullarton on 2008-02-06
I have just installed DESKNOW - An Email and collaboration suite.  All went very well and is working fine other than email - port 25 (used for SMTP) is in use by another program - DESKNOW has its own SMTP  process builtin in.  I searched and searched but cannot find what is using it.  Can anyione guide me to finding and removing the process that is using PORT 25?

---

### Post by kpkeerthi on 2008-02-06
Run this command in a terminal:
```

netstat -antp

```

I'm not in front of linux right now but that should get you started. 

There is another handy tool  **lsof**. I think you may have to install it first in ubuntu.
```

sudo apt-get install lsof

```

Then to check which process is listening on 25, run from terminal
```

lsof -i :25

```

---

