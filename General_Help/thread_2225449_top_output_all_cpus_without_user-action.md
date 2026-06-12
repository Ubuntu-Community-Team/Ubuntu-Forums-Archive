---
title: "top output all cpus without user-action"
date: 2014-05-21
forum: General Help
---

### Post by darkodonie on 2014-05-21
Every hour I got cron running:

```
top -d 99 -n 1 -b > /..../server_top_output.txt
```

For a tool that animates server stats. The problem is it's only spitting out one CPU, not the 8 CPU's on my virtual ubuntu server.

When in top myself, I hit `1` and it reveals all 8.. but I can't figure out how to get it into my cronjob command.

Any help or guidance would be greatly appreciated.

---

### Post by Yellow Pasque on 2014-05-21
Get top the way you want it (i.e press '1' top show all CPU's), and then press 'W' (Shift + w) to write a configuration file. I tested it with your command and it works.

---

### Post by darkodonie on 2014-05-21
Cleaver! Exactly what I was looking for. Thank you so much! :)

---

### Post by Habitual on 2014-05-21
wrt: ~/.toprc
I use this in mine:
```
RCfile for "top with windows"        # shameless braggin'
Id:a, Mode_altscr=0, Mode_irixps=1, Delay_time=3.000, Curwin=0
Def    fieldscur=AEHIOQTWKNMbcdfgjplrsuvyzX
    winflags=30137, sortindx=13, maxtasks=20
    summclr=1, msgsclr=1, headclr=3, taskclr=1
Job    fieldscur=ABcefgjlrstuvyzMKNHIWOPQDX
    winflags=62777, sortindx=0, maxtasks=0
    summclr=6, msgsclr=6, headclr=7, taskclr=6
Mem    fieldscur=ANOPQRSTUVbcdefgjlmyzWHIKX
    winflags=62777, sortindx=13, maxtasks=0
    summclr=5, msgsclr=5, headclr=4, taskclr=5
Usr    fieldscur=ABDECGfhijlopqrstuvyzMKNWX
    winflags=62777, sortindx=4, maxtasks=0
    summclr=3, msgsclr=3, headclr=2, taskclr=3

```

seems to show me all CPUs and shows the full path of each command.

Hope that's helpful.

---

