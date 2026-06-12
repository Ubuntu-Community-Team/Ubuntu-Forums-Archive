---
title: "Ctrl+Shift+C sending ^C"
date: 2012-11-15
forum: General Help
---

### Post by chrisinpants on 2012-11-15
An issue has evolved on my box when using terminal (x or other) when trying to copy (by pressing Ctrl+Shift+C) a cancel is sent (^C). The copy works but it's a real pain completing long lines of code. The problem is there in any environment I use (Ubuntu, xubuntu, lxde etc).

---

### Post by Myoldmopar on 2012-11-15
Does your shift key work in other apps?

---

### Post by Myoldmopar on 2012-11-15
Oh, I see, the copy does work, but it also sends Ctrl-C...

---

### Post by Vaphell on 2012-11-15
that should not happen though. ctrl+shift+c doesn't send ^C on my box.

---

### Post by Abhinav Kumar on 2012-11-15
> **chrisinpants said:**
> An issue has evolved on my box when using terminal (x or other) when trying to copy (by pressing Ctrl+Shift+C) a cancel is sent (^C). The copy works but it's a real pain completing long lines of code. The problem is there in any environment I use (Ubuntu, xubuntu, lxde etc).
Hi,

Lets check if your Shift key is working correctly or not.
Type the following in terminal

```

xev | egrep Shift

```Then , press Shift button and see if you see Shift is being displayed in terminal or not.
Left Shift is displayed as Shift_L
Right Shift is displayed as Shift_R

:)
Regards,
Abhinav

---

### Post by chrisinpants on 2012-11-15
Wow that's some definitive diagnostic which is indicting yes it is working as it should be. I'm having issues copying anything in terminal when in xfce but I've just logged in as a new user (to ubuntu 2D) and it's working as it should be again, so I guess it's not system wide. I'm going back to no copy land now...

Update - I'm back in as my usual user in Ubuntu 2D and it's working as it should be, so I guess I'll keep trying other desktops. I'm running out of choices now.

---

### Post by Vaphell on 2012-11-15
control question: why don't you use highlight/middleclick-paste? it's much more convenient than keyboard copypasta.

---

### Post by chrisinpants on 2012-11-15
I do sometimes but then sometimes the mouse is further than I need to reach and I get all spoilt for choice :/. It's part of the beauty.

Anyway u2d is doing me fine atm, maybe I'll come back here if the feeling fades. Thanks for the tips y'all.

---

