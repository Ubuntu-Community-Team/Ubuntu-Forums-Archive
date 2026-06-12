---
title: "[SOLVED] Alt F2 doesn't respond"
date: 2007-10-08
forum: General Help
---

### Post by dmacdonald111 on 2007-10-08
Hi all.

I seem to be having problems with the Alt-F2 key combination not responding. I'm using compiz and my title bars have disappeared. I know how to solve this, but I don't get the dialog box when I press those keys. Does anyone have any ideas as to what could be wrong?

TIA

---

### Post by Cannaregio on 2007-10-08
> **dmacdonald111 said:**
>  I'm using compiz and my title bars have disappeared.

Title bars disappearing means compiz isn't working as it should.
Reinstall metacity.
```
sudo apt-get install --reinstall metacity
```
Check if alt+F2 works in metacity.
Reinstall compiz.

If it fails, create a new user profile and try using him instead.
This works most of the time.

---

### Post by dmacdonald111 on 2007-10-08
Thank you. I did what you suggested and everything (including the Alt-F2) is working now.

---

