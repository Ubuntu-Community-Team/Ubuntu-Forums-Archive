---
title: "VMware Server"
date: 2006-11-11
forum: General Help
---

### Post by JoshHendo on 2006-11-11
Hello.

I am having problems with installing VMware server downloaded from the vmware server website.

When I try to run vmware in the terminal, it comes back with:

```

vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```

I have tried re-installing it multiple times and re-configuring it, but I can't seem to get it to run.

Is there anything that I could do to change this? I am thinking it may have something to do with my wireless card, but I can't be sure.

---

### Post by .t. on 2006-11-11
Try deleting /etc/vmware and starting again

---

### Post by ifokkema on 2006-11-13
Or, just delete /etc/vmware/not_configured and see how it runs...

---

### Post by temcat on 2006-11-13
Also check if you have xinetd installed.

---

### Post by .t. on 2006-11-13
I didn't need it...

---

### Post by krismatth3 on 2006-11-13
Have you run 
```

/usr/bin/vmware-config.pl

``` 

as root?

Why do you think it has something to do with your wireless card?

---

### Post by gusjones on 2006-11-24
I had a similar problem.

I got the same message after installing vmware server, which appeared to work fine, but after a reboot it kept telling me that it was not configured.

So when I saw this thread I just deleted the not_configured file and hey presto vmware server now works fine.

:D

---

