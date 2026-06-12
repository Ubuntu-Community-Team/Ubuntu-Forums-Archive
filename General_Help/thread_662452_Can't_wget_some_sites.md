---
title: "Can't wget some sites"
date: 2008-01-09
forum: General Help
---

### Post by PurposeOfReason on 2008-01-09
Today, out of nowhere my conky mail and weather stopped working. I had recently disabled ipv6 as it stopped my internet from working all together (once again randomly). I turned it back on today (and oddly enough, the internet if fine), but the problem continues. The gmail portion reads
```
Resolving mail.google.com... 1.0.0.0
Connecting to mail.google.com|1.0.0.0|:443... failed: Connection timed out.
Retrying.

--21:08:02--  https://purposeofreason:*password*@mail.google.com/mail/feed/atom
  (try: 2) => `-'
Connecting to mail.google.com|1.0.0.0|:443... 
```

And if I try to just wget mail.google.com I get
```

--21:11:33--  https://mail.google.com/
           => `index.html'
Resolving mail.google.com... 1.0.0.0
Connecting to mail.google.com|1.0.0.0|:443... 


```

Any ideas?

---

### Post by dcstar on 2008-01-09
> **PurposeOfReason said:**
> Today, out of nowhere my conky mail and weather stopped working. I had recently disabled ipv6 as it stopped my internet from working all together (once again randomly). I turned it back on today (and oddly enough, the internet if fine), but the problem continues. The gmail portion reads
```
Resolving mail.google.com... 1.0.0.0
Connecting to mail.google.com|1.0.0.0|:443... failed: Connection timed out.
Retrying.

--21:08:02--  https://purposeofreason:*password*@mail.google.com/mail/feed/atom
  (try: 2) => `-'
Connecting to mail.google.com|1.0.0.0|:443... 
```

And if I try to just wget mail.google.com I get
```

--21:11:33--  https://mail.google.com/
           => `index.html'
Resolving mail.google.com... 1.0.0.0
Connecting to mail.google.com|1.0.0.0|:443... 


```

Any ideas?

mail.google.com ip address resolves to 74.125.19.18, not 1.0.0.0

You have crap in your hosts file or whatever does your DNS lookups.

---

