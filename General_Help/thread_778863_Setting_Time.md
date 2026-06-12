---
title: "Setting Time"
date: 2008-05-02
forum: General Help
---

### Post by kshane on 2008-05-02
Hi all!

I am using Hardy and have found that my system time got changed after installing another OS.  I get the window to make the changes, but everything is grayed out - unable to click anything except "CLOSE"..  Can some one help?

Thanks!

Kevin

---

### Post by Monicker on 2008-05-02
Odd. On mine I have an Unlock button when I go adjust the time and date, which lets me get access to it.  You don't have that button?

---

### Post by kshane on 2008-05-02
> **Monicker said:**
> Odd. On mine I have an Unlock button when I go adjust the time and date, which lets me get access to it.  You don't have that button?

It was there, but grayed-out.  

However, after doing a search on Google, I found the commandline way to do it and it worked fine:

```

date 051918002007.00

```

Thanks!

Kevin

---

### Post by ibutho on 2008-05-02
Another option for setting time is using ntpdate e.g.
```
sudo ntpdate ntp.someserver.com
```

---

