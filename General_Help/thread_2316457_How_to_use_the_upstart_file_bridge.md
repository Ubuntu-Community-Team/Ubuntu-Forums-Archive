---
title: "How to use the upstart file bridge"
date: 2016-03-08
forum: General Help
---

### Post by spazzeri on 2016-03-08
Hello,

On Ubuntu 14.04:
In my user session, upstart-file-bridge is running.

This job is defined in ~/.config/upstart:

```

start on file FILE=~/tmp/
task
pre-start script
notify-send e:"$EVENT" f:"$FILE"
end script
script
exec xclock -update 1
end script

```

But it never starts when the ~/tmp directory changes !
Any idea what's missing ?

---

