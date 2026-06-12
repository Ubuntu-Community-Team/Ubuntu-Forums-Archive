---
title: "No more updates prompted... not sure why"
date: 2015-04-27
forum: General Help
---

### Post by azitizz on 2015-04-27
Hi There, I wondering if someone may have an answer as to why my system seems to no longer be prompting me to install new updates of any kind. In my software update window, in the setting, everything is checked off in order to tell me when updates are available on a daily basis.

I've done a fresh install of 14.04 on my Toshiba Satellite L350d in the last couple of months. For about half the time I was getting the daily or almost daily prompts for installing new updates. It started dawning on me a few weeks ago that I haven't been seeing any.

Something seems to be is amiss. Any Ideas of pointers to diagnose?

Thanks

---

### Post by Bashing-om on 2015-04-27
azitizz; Hello;

I too run 14.04 , and lately there has been few updates to be installed. This day I did get an update for tzdata ( my mirror is a Texas.edu site).
But anyway, to see the status of the package management system, do so from terminal:
terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

```

and a tale
[INDENT][INDENT][INDENT]will be told
[/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2015-04-27
> **Bashing-om said:**
> azitizz; Hello;

I too run 14.04 , and lately there has been few updates to be installed. This day I did get an update for tzdata ( my mirror is a Texas.edu site).
But anyway, to see the status of the package management system, do so from terminal:
terminal commands:
```

sudo apt-get install
sudo apt-get upgrade

```

and a tale[INDENT][INDENT][INDENT]will be told
[/INDENT]
[/INDENT]
[/INDENT]

Did you really mean those two commands or was it meant to be ```
sudo apt-get update
sudo apt-get upgrade
```
I think that your first command will output errors if there is no connection to repos but I just wondered why not the update/upgrade duo that I expected.

---

### Post by Bashing-om on 2015-04-27
Hey AJ ...

My bad ! You are so correct .. My mind must have been elsewise. Sheesshh ; I will correct .

Thanks once more for having my back.

[INDENT][INDENT]maybe I best 3rd time proof read 
[/INDENT][/INDENT]

---

