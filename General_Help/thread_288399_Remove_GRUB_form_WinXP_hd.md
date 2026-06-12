---
title: "Remove GRUB form WinXP hd"
date: 2006-10-29
forum: General Help
---

### Post by noerrorsfound on 2006-10-29
When I have a hard drive plugged in that has only WinXP installed, I get "GRUB Error 21".

Previously I had installed Ubuntu to my slave hard drive when the Windows XP hard drive was plugged in as master.

I reinstalled Ubuntu, this time having it's hard drive as master and not having the Windows XP one in (which fixed a previous problem).

If I try to put the Windows XP drive in (taking out the Ubuntu) I get the error 21.

If I leave the ubuntu one in and put the XP one as the slave then I see some other error.

I'd like to dual boot, but more importantly this hard drive needs to be able to run without that error 21.

The problem I had previously was that Ubuntu would get stuck at "can't access tty; job control turned off" after I rebooted into Windows XP and then back into Ubuntu. That was when I had the XP hd as master.

---

### Post by jd65pl on 2006-10-29
Put in your windows XP boot cd and boot in recovery mode then do

```
[FONT=courier]fixmbr[/FONT]
```

This should get rid of grub

---

