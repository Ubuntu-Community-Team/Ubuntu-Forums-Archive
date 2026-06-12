---
title: "Ubuntu login not accepting correct password"
date: 2017-02-19
forum: General Help
---

### Post by saibaggins on 2017-02-19
Hi, 

I can't log in to my ubuntu (14.04 afaik). I'd consider I might have forgotten the password but this started the other day and I noticed that if I went to the top right and clicked 'switch user' then it would accept my password and log me in. However, after rebooting there is no user to switch to I can't log in. 

I'd try switching to a tty but ctfl-alt-fkey doesn't work. Disable? Enter key doesn't work either, wierdly I've used the onscreen keyboard and that enter key doesn't work either. In bios enter key works fine. 

Does anyone have any clues as to what might have happened? I don't think I've had this machine online since this started playing up. 

I think my data is not encrypted so i should be able to rescue this with a reinstall without any complication.

---

### Post by CharlesA on 2017-02-19
Are you able to login to a virtual terminal by hitting Ctrl + Alt + F1 ?

If not, try resetting your password.. see here: [http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

---

### Post by uNoubu8a on 2017-02-19
> **saibaggins said:**
> **I'd try switching to a tty but ctfl-alt-fkey doesn't work**. Disable? Enter key doesn't work either, wierdly I've used the onscreen keyboard and that enter key doesn't work either. In bios enter key works fine. 

> **CharlesA said:**
> Are you able to login to a virtual terminal by hitting Ctrl + Alt + F1 ?

^^

---

### Post by wildmanne39 on 2017-02-19
*Thread moved to **General Help**.*

---

### Post by CharlesA on 2017-02-19
> **work-work said:**
> ^^

Keyboard mappings sound off, which sounds strange. Shouldn't affect recovery mode though.

---

### Post by saibaggins on 2017-02-19
Thank you Charles! 

went in to recovery mode and chose 'resume normal boot'. Same login screen only this time password and return key works. Any clues on resetting whatever it is that is changing the keyboard mappings why i try boot normally?

---

### Post by CharlesA on 2017-02-19
> **saibaggins said:**
> Thank you Charles! 

went in to recovery mode and chose 'resume normal boot'. Same login screen only this time password and return key works. Any clues on resetting whatever it is that is changing the keyboard mappings why i try boot normally?

Does it work after you reboot normally?

You can try checking in the keyboard settings to see if anything is off, but that sure is strange.

---

