---
title: "Autostart program minimized with xfce?"
date: 2012-11-09
forum: General Help
---

### Post by SteveDeFacto on 2012-11-09
I made a simple script to run devilspie wait a few seconds then run steam minimized. If I run it from terminal it works fine but when I try to run it on autostart devilspie does not minimize steam.


Here is the script:
devilspie & sleep 3 && steam steam://open/games -silent

I just want to make my hacked steam beta start like it does in windows...

---

### Post by LewisTM on 2012-11-09
Autostart entries don't use bash to interpret command line syntax like & and &&.
Try this:
```
bash -c "devilspie & sleep 3 && steam steam://open/games -silent"
```
Cheers!

---

### Post by SteveDeFacto on 2012-11-09
> **LewisTM said:**
> Autostart entries don't use bash to interpret command line syntax like & and &&.
Try this:
```
bash -c "devilspie & sleep 3 && steam steam://open/games -silent"
```
Cheers!

Yeah, I did that. Then I tried putting a script in my usr/bin directory and running the script with xfce autostart. Still does not work. Steam loads but it's not minimized. It's as if devilspie does not work until after the system is finished starting.

---

### Post by pqwoerituytrueiwoq on 2012-11-09
devilspie is not gdevilspie, you made a typo

that app will minimize steam every time you open it, i used this script with thunderbird, before i found a addon to do it
```
#!/bin/bash
thunderbird > /dev/null &
while [ "`wmctrl -l | grep 'Mozilla Thunderbird'`" == "" ]; do
    sleep 0.1;
done
wmctrl -c "Mozilla Thunderbird"
sleep 1
wmctrl -c "Mozilla Thunderbird"
exit
```you should be able to mod it for steam, Thunderbird was set to minimize on close

---

### Post by SteveDeFacto on 2012-11-09
> **pqwoerituytrueiwoq said:**
> devilspie is not gdevilspie, you made a typo

that app will minimize steam every time you open it, i used this script with thunderbird, before i found a addon to do it
```
#!/bin/bash
thunderbird > /dev/null &
while [ "`wmctrl -l | grep 'Mozilla Thunderbird'`" == "" ]; do
    sleep 0.1;
done
wmctrl -c "Mozilla Thunderbird"
sleep 1
wmctrl -c "Mozilla Thunderbird"
exit
```
you should be able to mod it for steam

I don't understand what you mean. I never typed gdevilspie?

---

### Post by pqwoerituytrueiwoq on 2012-11-09
are you sure about that
> **SteveDeFacto said:**
> devilspie & sleep 3 && steam steam://open/games -silent
should be **g**devilspie & sleep 3 && steam steam://open/games -silent

---

### Post by SteveDeFacto on 2012-11-09
> **pqwoerituytrueiwoq said:**
> are you sure about that

should be **g**devilspie & sleep 3 && steam steam://open/games -silent

Will this work?

```
#!/bin/bash
steam steam://open/games -silent > /dev/null &
while [ "`wmctrl -l | grep 'Steam'`" == "" ]; do
    sleep 0.1;
done
wmctrl -c "Steam"
sleep 1
wmctrl -c "Steam"
exit
```

EDIT: Nope didn't work...

---

### Post by pqwoerituytrueiwoq on 2012-11-09
with steam open post output of ```
wmctrl -l
```

---

### Post by Toz on 2012-11-09
This thread is being closed for review. There is a concern regarding the bypass of Steam usage terms and conditions with the phrase **hacked steam beta**.

---

