---
title: "[SOLVED] Bash Restart Firefox"
date: 2008-02-26
forum: General Help
---

### Post by ronan1289 on 2008-02-26
Occasionally firefox will freeze up on me (usually when I try to load too many things at once) and I'll end up using the "Force Quit" button in my gnome panel. When I try to restart firefox, however, I get a message saying that firefox is already running and that I need to end the process before I can start a new one. In the past, I've fixed this by using [ps -ef | grep "firefox"] and then killing every process ID that has to do with firefox, but I figured there must be a better way. I tried creating a bash script that would do this for me automatically, but I have virtually no knowledge of bash scripting and I cannot seem to get the script to work. The contents of the script are as follows:

#!/bin/bash
pkill "firefox"
/usr/bin/firefox

When I run the script, the terminal displays "Terminated" but nothing else happens. If I leave firefox open, the script will close it, but firefox won't restart. Any help for improving this script?

---

### Post by y-lee on 2008-02-26
```
pkill "firefox-bin"
```

---

### Post by ronan1289 on 2008-02-26
Thanks

---

### Post by y-lee on 2008-02-26
No problem go ahead and mark this as solved if that worked for ya, it makes the forums easier to use for all. See the link in my sig if ya don't know how :)

---

