---
title: "[Ubuntu 18.04.2 LTS] script for watching a certain process if running"
date: 2019-07-01
forum: General Help
---

### Post by zhelev81 on 2019-07-01
Hello, 

anybody can help me to create a script for watching a certain process if running, if not running to start it. My scrip for start looks like this right now.

```
#!/bin/sh

st_user="MYUSER"

screen -A -m -d -S MYPROCESS \
su - $st_user /home/MYUSER/servers/scripts/MYSCRIPT.sh
```

```
#!/bin/sh

cd /home/MYUSER/servers/MYSCRIPT-folder/
/home/MYUSER/servers/MYSCRIPT-folder/MYSCRIPT.pl
```

i just want to track this process all the time if it is running , if it not then start the screen again automatically.

I hope someone can tell me how

---

### Post by wildmanne39 on 2019-07-03
Thread closed. Please do not post duplicates, it dilutes community effort.

If you find you posted in the wrong forum please click the report button and the staff will take a look, if you do not receive a reply in twelve hours you can bump your thread to keep it in view.

Thanks

---

