---
title: "Opera and Thunderbird and Mailto links"
date: 2005-08-29
forum: General Help
---

### Post by installer on 2005-08-29
Have been trying to figure out how to open a compose window (in a running version of Thunderbird) when clicking on a Mailto link in Opera.

This  command  "/usr/lib/mozilla-thunderbird/mozilla-thunderbird-bin  mailto:%t"   works if Thunderbird is not running, but if it's running all I get is a choose user profile dialog, any ideas anyone?

---

### Post by installer on 2005-08-29
Even Firefox does the same, there must be others with the same issue.

Anyone ?

---

### Post by balloons on 2006-06-25
```
/usr/bin/mozilla-thunderbird -compose %w
```

---

### Post by dabeej on 2006-07-13
> **guitara said:**
> ```
/usr/bin/mozilla-thunderbird -compose %w
```

Thanks! It Works! Works for Dapper too folks (as it should).

---

