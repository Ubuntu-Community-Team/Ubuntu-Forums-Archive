---
title: "Cron Problem"
date: 2007-05-13
forum: General Help
---

### Post by rajeshgovindan on 2007-05-13
I wanted to automate the execution of a telnet script

Installed cron
Read its manual atleast 100 times and I still not able to schedule appz

At the terminal did
```
sudo crontab -e
```

I could fill up all fields except the last field ; the command field
My script(named TST.sh in folder /home/myname/Desktop)

So what should I enter there
I tried  " /home/myname/Desktop/TST.sh " but in vain

I even tried to schedule another normal .txt file even it didn't run

Plz.help

---

### Post by Lux Perpetua on 2007-05-13
You might want to read the Wikipedia page, which has a "common mistakes" section: [http://en.wikipedia.org/wiki/Crontab](http://en.wikipedia.org/wiki/Crontab)

If that doesn't solve your problem, post the output of ```
crontab -l
```

Also, make sure the script you're trying to run is executable. What you put in the "command" field should be the same thing you would use to run the script from a console.

---

### Post by rajeshgovindan on 2007-05-14
40 16   * * *   /home/MyName/Desktop/TST.sh

This is what I get when I do 

```
crontab -l
```

But these tasks never get executed

Even simplest applications never get executed

](*,) ](*,)

---

