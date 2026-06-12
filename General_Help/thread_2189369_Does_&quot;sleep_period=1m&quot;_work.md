---
title: "Does &quot;sleep_period=1m&quot; work?"
date: 2013-11-22
forum: General Help
---

### Post by vasa1 on 2013-11-22
If I use values higher than **1m** in *sleep_period*, there's no problem but when *sleep_period=**1m***, nothing happens, no error even in a terminal, and the script doesn't work. Must one use *sleep_period=60s* instead? *man sleep* and *info sleep* don't clearly say that **1m** shouldn't be used and that **60s** should be used instead.

The "sleep" I have is part of GNU coreutils 8.20.

Does *sleep_period=1m* work for anyone else or is it that I've made a late discovery of something obvious?

---

### Post by steeldriver on 2013-11-22
I can only test it on coreutils 8.13 (Ubuntu 12.04.3) and 8.21 (LMDE)

```

$ time sleep 1m

real    1m0.003s
user    0m0.000s
sys    0m0.000s
$ 
$ sleep --version
sleep (GNU coreutils) 8.21
*<snip>*

```

I guess you could check the bug archives / release notes to see if anything slipped in between --> [https://www.gnu.org/software/coreutils/](https://www.gnu.org/software/coreutils/)

---

### Post by vasa1 on 2013-11-22
Okay, I guess it was something else that was wrong:
```
#!/usr/bin/env bash

sleep_period=1m

while true; do
      echo "Hello"
  sleep ${sleep_period}
done

``` works.

---

