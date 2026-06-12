---
title: "Help needed with scripts"
date: 2007-03-10
forum: General Help
---

### Post by skywatcher on 2007-03-10
Please can someone advise me on how to use a script to start more than one program. For example, I have a script that starts my 3G modem:

```
#!/bin/bash
# 3G connect

/etc/init.d/pcmciautils start
wvdial huawei_e620 && sleep 5 && internet 3gonly 384k
```

This works fine, but I would like to run gkrellm at the same time so that I can keep track of data usage. So I try this:

```
#!/bin/bash
# 3G connect

gkrellm
/etc/init.d/pcmciautils start
wvdial huawei_e620 && sleep 5 && internet 3gonly 384k
```

This starts gkrellm, but doesn't connect the modem. So I try this:

```
#!/bin/bash
# 3G connect

/etc/init.d/pcmciautils start
wvdial huawei_e620 && sleep 5 && internet 3gonly 384k
gkrellm
```

This has the opposite effect -- the modem connects, but gkrellm doesn't start.

How can I do this?

---

### Post by nereid on 2007-03-10
Use the second script which starts gkrellm before the modem and append an ampersand at the end of the line

```

...
gkrellm &
...

```

The ampersand will start the command in the background.

---

### Post by yabbadabbadont on 2007-03-10
You have to run one of them in the background or the script will stop until that program exits.  Add one ampersand "&" to the end of the line of the program to be started in the background.

Edit: Doh!  Too slow.  :D

---

### Post by skywatcher on 2007-03-10
Thanks guys! You taught me something...

---

