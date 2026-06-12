---
title: "Proxy password contains @"
date: 2007-04-18
forum: General Help
---

### Post by Renegade of Funk on 2007-04-18
Good morning all,

I have a small problem... At my office we use an proxy server. So when I want to use wget / apt or whatever (wich all uses the exported http_proxy variable) I can't connect becouse my password contains an '@' char. So when I use for example: export=http://nick:some@work@proxy.host:8080/
It sees "work@proxy.host" as the proxy addres and not "proxy.host" which should be used.

Is there anyway to escape this '@' (Don't know the English name for it :confused: ) wich is in the password?

Cheers,
Nick

---

### Post by heimo on 2007-04-18
Not sure what causes it, but the first one I'd try is backslash.
```
export http_proxy=http://nick:some\@work@proxy.host:8080/
```

---

### Post by Renegade of Funk on 2007-04-18
Already tried that. But no succes :(

Thanks anyway :)

---

### Post by heimo on 2007-04-18
This is a bit more desperate, but still worth trying - urlencode it with %40.

```
export http_proxy=http://nick:some%40work@proxy.host:8080/
```

---

### Post by Renegade of Funk on 2007-04-18
wh00t, thanks allot it works fine now :D

Cheers

---

### Post by heimo on 2007-04-18
> **Renegade of Funk said:**
> wh00t, thanks allot it works fine now :D


Excellent! For anyone else having problems with special characters in proxy password, solution seems to be to [urlencode]("http://en.wikipedia.org/wiki/Urlencode") them.

---

