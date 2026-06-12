---
title: "Monitor cron in real time"
date: 2022-06-28
forum: General Help
---

### Post by veedub67 on 2022-06-28
Hello,

Am trying to follow the instructions here

[https://askubuntu.com/questions/966194/16-04-how-do-i-make-cron-create-cron-log-and-monitor-it-in-real-time/966195#966195](https://askubuntu.com/questions/966194/16-04-how-do-i-make-cron-create-cron-log-and-monitor-it-in-real-time/966195#966195)

And create the wcron command

```
echo "#!/bin/bash" >wcronecho "watch -n 10 tail -n 25 /var/log/cron.log" >>wcron
chmod +x wcron
sudo cp wcron /usr/sbin
```

If I try and create line-by-line, which is what I think I'm supposed to do

I get
```
echo "#!/bin/bash" >wcron
bash: !/bin/bash: event not found

```

---

### Post by philhughes on 2022-06-28
Use single quotation marks. ! has a special meaning to bash for history substitution.

---

