---
title: "growisofs settings"
date: 2006-07-24
forum: General Help
---

### Post by calagan on 2006-07-24
I'm having trouble burning .iso images on DVD+R with growisofs on my Ubuntu 6.06 LTS.
I use the command below taken from the growisofs man page example, since I don't need multisession. 
```
growisofs -dvd-compat -Z /dev/dvd=image.iso
```
Everything seems to work out fine, no error message, but in the end, my DVD-R is unreadable.

What strikes me is that I'm able to burn the same image successfully with K3B, which seems to be using growisofs (it tells you it's using growisofs 5.21 when you start burning). Am I missing a parameter in growisofs?

Cal

---

### Post by kabus on 2006-07-24
> **calagan said:**
> Am I missing a parameter in growisofs?


This won't help you much but I use exactly the same command to burn DVDs and it works.

---

### Post by calagan on 2006-07-24
Thanx kabus, that sure helps my self-esteem.
Would you mind letting me know what version of growisofs you're using?
```
growisofs -version
```
Are you using Ubuntu 6.06 LTS?

---

### Post by kabus on 2006-07-24
I'm not running Ubuntu at the moment so I can't check, sorry.
But I've burned DVDs that way in all versions of Ubuntu including early Dapper development releases.

---

