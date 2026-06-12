---
title: "username"
date: 2008-02-10
forum: General Help
---

### Post by stilsane on 2008-02-10
A friend installed Ubuntu for me on an old computer, then forgot the username he used.  He remembers the password, but not the username.  I found a solution on this site: Is /home as a command during startup, but the system does not recognize the command.  Any other suggestions?  Thanks.  Keep in mind that I'm a newbie.

---

### Post by sowelie on 2008-02-10
The command is actually ls /home, but you'll have to get to a prompt to do that.  Try going into safe mode.

---

### Post by p_quarles on 2008-02-10
> **sowelie said:**
> The command is actually ls /home, but you'll have to get to a prompt to do that.  Try going into safe mode.
More specifically, recovery mode from the boot menu. Just after the BIOS finishes, press escape to see the menu, then select "Recovery Mode."

Then, ```
ls /home
```
and the directory that is listed will be your username.

---

### Post by seventhc on 2008-02-10
> **p_quarles said:**
> More specifically, recovery mode from the boot menu. Just after the BIOS finishes, press escape to see the menu, then select "Recovery Mode."

Then, ```
ls /home
```and the directory that is listed will be your username.
forgot the closing bracket, fixed :)

---

### Post by p_quarles on 2008-02-10
Oops. Fixed it, and thanks. ;)

---

### Post by stilsane on 2008-02-10
Thanks for your help.  I'll try it and let you know.  Is it the letter"I" or the numeral "1" I should be using in the Is?

---

### Post by jtravnick on 2008-02-10
its the letter L in lower case

---

### Post by overdrank on 2008-02-10
> **stilsane said:**
> Thanks for your help.  I'll try it and let you know.  Is it the letter"I" or the numeral "1" I should be using in the Is?

HI and that is a small L and also at the login screen you should see the user name in the lower right hand corner.

---

### Post by stilsane on 2008-02-10
Thank you!  No wonder I was having such trouble.  Maybe I need new glasses too!

---

