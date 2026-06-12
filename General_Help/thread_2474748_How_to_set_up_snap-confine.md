---
title: "How to set up snap-confine"
date: 2022-05-06
forum: General Help
---

### Post by psychohermit on 2022-05-06
Greetings folks,

How do I set up snap-confine?  I have copied /etc/apparmor.d/usr.lib.snapd.snap-confine.real to /etc/apparmor.d/usr.lib.snapd.snap-confine trying to get snap-confine working.  No joy, when I try to run anything that is snap based I get 
```

snap-confine has elevated permissions and is not confined but should be. Refusing to continue to avoid permission escalation attacks

```

Thanks in advance for any assistance you can offer.
--glenn

---

### Post by #&amp;thj^% on 2022-05-06
will this work?
```

sudo apparmor_parser -r /etc/apparmor.d/*snap-confine*
sudo apparmor_parser -r /var/lib/snapd/apparmor/profiles/snap-confine*
```
No restart required.

---

### Post by psychohermit on 2022-05-06
No that didn't work.  I had to reinstall snapd so firefox would work to post this.

Thanks,
--glenn

---

### Post by poorguy on 2022-05-06
[https://stackoverflow.com/questions/70053614/snap-confine-has-elevated-permissions-and-is-not-confined-but-should-be-refusin](https://stackoverflow.com/questions/70053614/snap-confine-has-elevated-permissions-and-is-not-confined-but-should-be-refusin)

---

### Post by psychohermit on 2022-05-06
poorguy, I found the answer in the thread that you posted.  

systemctl enable --now snapd.apparmor.service

Thank you very much.

--glenn

---

