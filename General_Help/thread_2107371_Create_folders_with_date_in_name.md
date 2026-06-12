---
title: "Create folders with date in name"
date: 2013-01-21
forum: General Help
---

### Post by X D face me on 2013-01-21
Hello everyone

i'm hosting a small game server on a 10.04 server and i want to run some automated backup. this could be done quite easily with crotab by copying the files every day to the backup location. But how can i create a folder with the current date as name so i can keep my old backups instead of overriding them

thx to any answers

X D face me

---

### Post by |{urse on 2013-01-21
mkdir `date '+%m%d%y'`  

Will create a folder with the current date, is that what you were looking for?

---

### Post by jonobr on 2013-01-21
If I recall
y= year in last 2 digits (13)
Y = full year (2013)

---

### Post by sisco311 on 2013-01-21
> **|{urse said:**
> mkdir `date '+%m%d%y'`  

Will create a folder with the current date, is that what you were looking for?

Instead of `command`, I'd use the POSIX form of command substitution: $(command). See BashFAQ 082 (link in my signature).


> **jonobr said:**
> If I recall
y= year in last 2 digits (13)
Y = full year (2013)

Yep, you are right. The man page (`man date') also explains all the available FORMAT options.

---

### Post by X D face me on 2013-01-22
the mkdir date '+%m%d%y' isn't working. i'm quite a noob on bash so please explain everything clear so i can understand it.

---

### Post by steeldriver on 2013-01-22
you need ALL the punctuation (backticks `...`) that |{urse posted - or the $(...) form as mentioned by sisco311

```
mkdir [COLOR=Red]$([/COLOR]date '+%Y-%m-%d'[COLOR=Red])[/COLOR]
```Alternative formats that you might want to consider are '+%F' or '+%x'

---

### Post by X D face me on 2013-01-22
thanks!!!!!! works now

---

