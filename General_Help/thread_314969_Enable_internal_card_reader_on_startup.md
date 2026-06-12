---
title: "Enable internal card reader on startup"
date: 2006-12-08
forum: General Help
---

### Post by ThrobbingBrain66 on 2006-12-08
From another thread in these forums, I figured out how to get my card reader working.  From a terminal I have to enter
```
sudo setpci -s 05:06.2 4c.b=0x02
```
and then everything is golden.  Now I want to do this at startup everytime so I don't have to do it manually.  I thought I understood that I needed to create a script with those contents in /etc/inti.d/ and then make it executable. Which i thought i did with 
```
sudo chmod +x /etc/init.d/card-reader.sh
```

The contents of card-reader.sh is as follows:
```
#!/bin/bash

setpci -s 05:06.2 4c.b=0x02

exit

```

However, when I restart, the script must not run because when I insert my card my box hard freezes and i have to reboot.  Can anyone tell me what I'm missing?

thanks

---

### Post by ThrobbingBrain66 on 2006-12-08
anyone?  bed time for me right now, so I'll take a look at what I did again tomorrow, but any advice would be great.

thanks

---

