---
title: "Date issue in 15.04"
date: 2015-10-28
forum: General Help
---

### Post by vanyinet on 2015-10-28
Starting from 15.10 these 2 commands do not have the same results:
date +%H:%M # => 08:40
date -d "-$(date +%d) days +0 minutes" +%H:%M # => 09:40

I tried in 15.04 and they are same (08:40) which is good, but why I get different in 15.10?

---

### Post by btindie on 2015-10-28
I get different values on 12.04.

What timezone are your systems set to??

Did you have a change in timezone recently for DST ending?

If I run
```
TZ=UTC date -d "-$(date +%d) days +0 minutes" +%H:%M
```
I get the same values.

---

### Post by vanyinet on 2015-10-28
Thank you,

For this: [COLOR=#000000][FONT=Ubuntu Mono]TZ=UTC date -d "-$(date +%d) days +0 minutes" +%H:%M
I got 10:02 and the time now is 12:02

I've just upgraded from 15.04 to 15.10, but previously these values were OK.

ps. I've installed a fresh Ubuntu 15.10 into Virtualbox and there are also 2 different values ... [/FONT][/COLOR][COLOR=#000000]date +%H:%M  gives me the correct value.[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]

---

### Post by vanyinet on 2015-10-29
It seems there is a big issue with timezone (DST).
Just tried Kalarm in my upgraded (and in the new Ubuntu) installation and I got this error:
>     The KDE time zone service is not available: check that ktimezoned is installed.    

What package contains ktimezoned?

Thanks.

---

