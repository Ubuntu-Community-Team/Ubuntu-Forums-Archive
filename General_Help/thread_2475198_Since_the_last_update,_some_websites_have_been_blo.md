---
title: "Since the last update, some websites have been blocked"
date: 2022-05-19
forum: General Help
---

### Post by SeijiSensei on 2022-05-19
Sounds like your DNS is misconfigured.  What happens when you run
```
$ host ubuntuforums.com
```

You should see 
```

ubuntuforums.com has address 185.125.188.17
ubuntuforums.com has address 185.125.188.16
ubuntuforums.com mail is handled by 10 mx.ubuntu.com.

```

Testing reverse DNS should work, too.
```
$ host 185.125.188.17
17.188.125.185.in-addr.arpa domain name pointer ubuntuforums.org.

```

---

