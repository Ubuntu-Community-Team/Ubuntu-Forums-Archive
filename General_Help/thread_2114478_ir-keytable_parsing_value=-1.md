---
title: "ir-keytable parsing value=-1"
date: 2013-02-10
forum: General Help
---

### Post by smee204 on 2013-02-10
I have setup a file in /lib/udev/rc_keymaps/ to map some remote buttons to keys. Most of them work apart from a few. 
One example is I am mapping a key to KEY_PERIOD like this 

```
0x800ff415 KEY_REWIND
0x800ff414 KEY_FASTFORWARD
0x800ff41b KEY_PERIOD #skip next
0x800ff41a KEY_COMMA #skip previous
0x800ff416 KEY_PLAY
0x800ff418 KEY_PLAYPAUSE
0x800ff419 KEY_STOP
0x800ff417 KEY_RECORD
...

```

However when I import it to ir_keytable it is not mapped correctly. When parsed it goes wrong.
 ```
sudo ir-keytable -v -c -w /lib/udev/rc_keymaps/imon_mce
Parsing /lib/udev/rc_keymaps/imon_mce keycode file
parsing 0x800ff415=KEY_REWIND:  value=168
parsing 0x800ff414=KEY_FASTFORWARD:     value=208
parsing 0x800ff41b=KEY_PERIOD:  value=-1
...

```

If I map the 0x800ff41b key as something else like KEY_STOP it is fine and parses as KEY_STOP.

Any idea why I am getting value=-1

Is there a list of valid keys somewhere?

I am using the new Ubuntu 13.04 kernel 3.8.0-5-generic so it could be a bug?

Thanks

---

### Post by sully101 on 2013-03-07
I am experiencing the same on 12.04 have you had any luck finding a solution?

---

### Post by sully101 on 2013-03-07
To answer my own question KP_DOT from input.h in the kernel source

---

