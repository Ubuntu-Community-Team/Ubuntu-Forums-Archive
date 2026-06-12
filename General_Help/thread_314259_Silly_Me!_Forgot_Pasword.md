---
title: "Silly Me! Forgot Pasword"
date: 2006-12-07
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2006-12-07
Sorry if this is the wrong place for this!! I have been using Ubuntu for so long, that when I went to retrieve some info from my Windows XP, I could not remember my password. I really need to get that info from Windows XP-This morning. Someone please help me out! :-k :confused:

---

### Post by amo-ej1 on 2006-12-07
can't you mount the xp filesystem and get the data from there ?

---

### Post by taurus on 2006-12-07
Boot into recovery mode from GRUB menu and at the prompt, change your password to a new one...

```
passwd mustangsallydd
(assuming mustandsallydd is your username...)
<new password>
<retype the new password>
shutdown -r now
```

---

### Post by amo-ej1 on 2006-12-07
didn't he mean he forgot the windows passwd ?

---

### Post by IusedTObeSOMEONEelse on 2006-12-07
Excuse me, but FEMALES also use Ubuntu, therefor it is '
**didn't 'S'he mean he forgot the windows passwd ?** Hi taurus, sorry but it's my Windows Machine :-? Thanks, Sally

---

### Post by amo-ej1 on 2006-12-07
sorry on that ](*,) 
but statistics were against you ;)

now can't you try to mount the windows parition under ubuntu and get the data from there ?

---

### Post by taurus on 2006-12-07
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Rhubarb on 2006-12-07
Or you can use the Ophcrack live CD to crack the windows password for you.
[http://ophcrack.sourceforge.net/](http://ophcrack.sourceforge.net/)

Takes around 2 minutes for the program to crack most passwords.
Only works if your password has less than 12 characters.

---

### Post by IusedTObeSOMEONEelse on 2006-12-07
Apology accepted ;) ;) , now Windows machine-not the same machine that Ubuntu is on (I know it's bad asking for help here).

---

### Post by amo-ej1 on 2006-12-07
that why we have ubuntu livecd's ;-) but using one of them and mount the disk from there.

---

### Post by taurus on 2006-12-07
If both machines connect to a router, you can use samba to mount your XP on Ubuntu.  

Or if you can't recover your password in XP, then use the LiveCD and mount your XP and copy stuff to a USB thumbdrive!

---

### Post by IusedTObeSOMEONEelse on 2006-12-07
So I am understanding that: there is no way I can use the **Windows XP disc** in **Windows recovery mode **to chang password.?

---

### Post by reztho on 2006-12-07
Use this:
[http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/)

---

### Post by rbhigday on 2007-01-02
> **taurus said:**
> Boot into recovery mode from GRUB menu and at the prompt, change your password to a new one...

```
passwd mustangsallydd
(assuming mustandsallydd is your username...)
<new password>
<retype the new password>
shutdown -r now
```

Thanks for this help, sorry to hijack the thread just wanted to say thanks :)

---

