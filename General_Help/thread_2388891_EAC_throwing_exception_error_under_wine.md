---
title: "EAC throwing exception error under wine"
date: 2018-04-08
forum: General Help
---

### Post by jamesisin on 2018-04-08
I am looking to fix a wine problem in another thread.  In the interim I have created a new login account and have followed these instructions to install EAC under that profile:

[https://ubuntuforums.org/showthread.php?t=2092214](https://ubuntuforums.org/showthread.php?t=2092214)

EAC is throwing an error and I found this response to that error (in the above thread):

```
EAC 1.1 doesn't start up and gives this error message

unhandled exception at 0308AE90 -> ACCESS_VIOLATION

but after running the command

cd ~/.wine/dosdevices/c\:/Program\ Files\ \(x86\)/Exact\ Audio\ Copy/regsvr32 sql*

it works!!!
```

Obviously this person has not entered the correct command.  Any idea what they meant to type?

---

### Post by jamesisin on 2018-04-08
Like so...

```
cd ~/.wine/dosdevices/c\:/Program\ Files\ \(x86\)/Exact\ Audio\ Copy/
regsvr32 sql*
```

---

### Post by Fifoxtasy on 2018-04-09
Change to eac directory and run command:
regsvr32 sql*

---

