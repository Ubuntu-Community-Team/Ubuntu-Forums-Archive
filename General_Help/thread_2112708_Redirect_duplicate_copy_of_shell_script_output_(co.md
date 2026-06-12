---
title: "Redirect duplicate copy of shell script output (console) to a logfile"
date: 2013-02-05
forum: General Help
---

### Post by jingo_man on 2013-02-05
i'm using someone else's package, which doesn't contain much error handling and zero logging.

how can i simply add in, without any other impact to the normal script operation, every command that gets outputted to console also is put into a specified logfile?

additionally, i call the bash script inside a "screen" session, i.e.

```
screen -S session_name -d -m /path/to/shell/script.sh
```

i have seen some people make reference to "exec ..." straight after the hash!bang, but this affects the output within the screen session above.

i tried using:

```
#!/bin/sh
exec >> /path/to/logfile.log 2>&1
...
```

also a concern of the file sizes getting crazy, as the script is on an endless loop. any simple mechanism to help with this? log rotate..? can pick up things quickly, but not a task i have needed to do, so at very least pointers to better articles that are available would also be hugely helpful.

thanks

jingo_man

---

### Post by dcstar on 2013-02-07
> **jingo_man said:**
> i'm using someone else's package, which doesn't contain much error handling and zero logging.

how can i simply add in, without any other impact to the normal script operation, every command that gets outputted to console also is put into a specified logfile?
...........
```
man tee
```

---

