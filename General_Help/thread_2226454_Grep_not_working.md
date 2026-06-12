---
title: "Grep not working"
date: 2014-05-27
forum: General Help
---

### Post by ubu88 on 2014-05-27
Hi,

I'm trying to grep a service name but it's not working.

```
 service --status-all | grep -i 'privoxy'


```

---

### Post by steeldriver on 2014-05-27
In what way exactly is it not working? Do you not get the result that you were expecting, or do you get additional output that you were not expecting? (HINT: service --status-all usually produces a lot of output on stderr)

---

### Post by ubu88 on 2014-05-27
Yes, it just puts out all the service name without filtering out the grep command.

---

### Post by steeldriver on 2014-05-27
You can redirect stderr to /dev/null if you don't want to see it

```

service --status-all 2>/dev/null | grep -i 'privoxy'

```

or combine stderr with stdout if you want to grep in both (for example, to list privoxy even if its status is unknown)

```

service --status-all 2>&1 | grep -i 'privoxy'

```

---

### Post by ubu88 on 2014-05-27
That works, thanks a lot!

---

