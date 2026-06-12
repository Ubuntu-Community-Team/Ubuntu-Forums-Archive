---
title: "Run command if computer is idle"
date: 2018-09-22
forum: General Help
---

### Post by raleigh3 on 2018-09-22
I would like to run a command if my computer is idle for 5 minutes.

I found this, but is not quite working.

It just does a one time check.

```
#!/bin/sh
idletime=$(xprintidle)
threshold=300000 # 5 min = 5 * 60 * 1000 ms
if [ "$idletime" -gt "$threshold" ]; then
  echo "idle for 5 minutes."
fi
```

---

### Post by Holger_Gehrke on 2018-09-23
You'd have to run xidletime repeatedly, basically polling. Not exactly good style ...
```

#!/bin/sh
t=300000
while [ $t -gt $(xidletime) ] ; do sleep 1; done
echo "idle for 5 minutes"

```

'xidle' seems like a better alternative, it hooks into the same mechanism that screensavers use. There seems to be a bit of a problem though. If you run this
```
xidle -timeout 5 -program "/usr/bin/xprintidle"
```
you'll see that xidle will not only call the program after 5 seconds of inactivity but also again at the end of an idle period that was long enough to generate a call to the program. So you'd have to use a script as the command which checks which of the two activation cases it's getting called on. Also the only way to end xidle is to kill it, which may or may not be a problem.

Holger

---

### Post by HermanAB on 2018-09-23
Also have a look at xprintidle described here:
[https://superuser.com/questions/638357/execute-a-command-if-linux-is-idle-for-5-minutes](https://superuser.com/questions/638357/execute-a-command-if-linux-is-idle-for-5-minutes)

---

