---
title: "Hibernate messed up swap"
date: 2007-05-25
forum: General Help
---

### Post by akudewan on 2007-05-25
I tried to Hibernate my machine, from K-Menu > Log Out. That didn't work, it just turned off my machine, and started as usual when I switched it back on.

I then noticed that my swap partition was not mounted. I tried "mount -a", but it gave my no error messages. Then I tried "swapon /dev/sdb3", and it mounted, giving me a warning that suspend data was detected.

Ever since, I have to mount the swap partition manually. It doesn't give the "suspend data detected" warning any more.. How can I fix this? I haven't touched my /etc/fstab, so I'm sure the problem isn't there.

---

### Post by tgalati4 on 2007-05-25
You might need to sudo mkswap /dev/sdb3

This will reformat the swap drive.  Then swapon.  I had troubles with hibernate under Kubuntu Dapper.  You do get a warning when you activate it that it might not work.  And the warning is there for a reason.

---

### Post by akudewan on 2007-05-25
Ok, I unmounted swap and ran "mkswap /dev/sdb3". Then rebooted my machine, and swap still didn't mount on startup.

Note that I got the warning with swapon only the first time, and I don't get any warning now.

---

### Post by akudewan on 2007-05-26
*bump*, can anyone help ?

---

### Post by akudewan on 2007-05-26
I ran mkswap again, and changed my fstab to use /dev/sdb3 instead of the UUID. Its working fine now.

---

