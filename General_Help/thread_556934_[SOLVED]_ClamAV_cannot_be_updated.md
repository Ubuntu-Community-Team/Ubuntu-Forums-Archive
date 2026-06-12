---
title: "[SOLVED] ClamAV cannot be updated"
date: 2007-09-22
forum: General Help
---

### Post by PmDematagoda on 2007-09-22
I tried updating ClamAV using ```
sudo freshclam
```, but got an error with this message:-

```

ClamAV update process started at Sat Sep 22 09:29:18 2007
WARNING: Can't query current.cvd.clamav.net
WARNING: Invalid DNS reply. Falling back to HTTP mode.
Reading CVD header (main.cvd): OK
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
Reading CVD header (daily.cvd): OK
daily.inc is up to date (version: 4357, sigs: 21553, f-level: 21, builder: sven)
WARNING: Current functionality level = 20, recommended = 21
Please check if ClamAV tools are linked against proper version of libclamav
DON'T PANIC! Read http://www.clamav.net/support/faq

```

Does anyone know why this problem occurs and what I should do to solve it?

---

### Post by jocko on 2007-09-22
Have you done what it tells you to do?
Go to the page it suggests and read the faq.
And the reason it's not getting updated is because it is already up to date (read all the text you pasted in your post.):
```
Reading CVD header (main.cvd): OK
main.inc[COLOR=Red] is up to date[/COLOR] (version: 44, sigs: 133163, f-level: 20, builder: sven)
Reading CVD header (daily.cvd): OK
daily.inc[COLOR=Red] is up to date[/COLOR] (version: 4357, sigs: 21553, f-level: 21, builder: sven)
```

---

### Post by PmDematagoda on 2007-09-22
I did read the FAQ, but couldn't make much headway into it.:confused:

I just need to know if ClamAV updates itself regularly, I have a 24 hour DSL connection, so that would help ClamAV if it does.

---

### Post by PmDematagoda on 2007-09-22
> **jocko said:**
> Have you done what it tells you to do?
Go to the page it suggests and read the faq.
And the reason it's not getting updated is because it is already up to date (read all the text you pasted in your post.):
```
Reading CVD header (main.cvd): OK
main.inc[COLOR=Red] is up to date[/COLOR] (version: 44, sigs: 133163, f-level: 20, builder: sven)
Reading CVD header (daily.cvd): OK
daily.inc[COLOR=Red] is up to date[/COLOR] (version: 4357, sigs: 21553, f-level: 21, builder: sven)
```

Ooops, (sigh), man, why didn't I read the message carefully??:confused:

Anyway thank you for your help jocko.:)

---

### Post by dcstar on 2007-09-22
> **PmDematagoda said:**
> I did read the FAQ, but couldn't make much headway into it.:confused:

I just need to know if ClamAV updates itself regularly, I have a 24 hour DSL connection, so that would help ClamAV if it does.

You can set up your system log to monitor the /var/log/clamav/freshclam.log file and you will see all relevant activity.

---

