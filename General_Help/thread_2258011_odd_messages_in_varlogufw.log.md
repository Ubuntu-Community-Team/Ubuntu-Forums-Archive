---
title: "odd messages in /var/log/ufw.log"
date: 2014-12-24
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-12-24
Running Trusty with plain Openbox as DE (like a stripped down Lubuntu), 64 bit.

I had /var/log/ open in thunar and noticed ufw.log was growing as I watched. Checking it with an editor shows messages like this (some substrings substitued as indicated because I'm not clear what part of this output is potentially sensitive) this repeated over and over:
```

Dec 23 15:22:10 m kernel: [5_digits_different_each_repetition.6_digits_different_each_repetition] [UFW BLOCK] IN=eth0 OUT= MAC=alphanumeric_string_with_a_colon_as_every_third_character SRC=numerals_and_decimals_looks_like_an_ip_address DST=224.0.0.1 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=5_digit_string PROTO=2

```
The interval between time stamps at the beginning of the repeated sequence
alternates between 26 and 34 seconds resulting in entries alternating between
10 and 36 seconds after the minute.


My ufw status:

```
me@m:~$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip
me@m:~$

```

This stops when I physically disconnect from the internet but resumes when I reconnect. So what does this mean? Is it a security concern? Hey, I don't won't North Koreans threatening me (joking). If nothing else this log is wasting more and more space but it doesn't seem to be growing too terrribly fast.

Thanks for any thoughts you can share.

And a Super Solsticial Season to all Sapients!

---

