---
title: "Can't sudo [Resolved]"
date: 2006-11-08
forum: General Help
---

### Post by Epica on 2006-11-08
I cannot sudo despite my account being in the sudoers file.
Every time i try the sudo command it comes up with this

> sudo: unable to lookup commander-desktop via gethostbyname()


* note commander being my username

Please help ASAP as i don't have another account with sudo ability :(

---

### Post by taurus on 2006-11-08
What does your /etc/hosts look like and do you belong to groups adm & admin?

```
id
cat /etc/hosts
```

---

### Post by Epica on 2006-11-08
I edited my hosts file recently to block ads from doubleclick etc. Is there a special entry for this file that is needed for sudo to work?

thanks in advance

---

### Post by bsussman on 2006-11-08
not special - just restore your backup of the file and add your anti-ad lines after that is there.

I advise you to leave the IPV6 stuff - you're probably not using IPV6 but there might be background things that expect those lines to be there.

---

### Post by Epica on 2006-11-08
big problem i can't sudo to change the file back and i've lost the backup.
please excuse me i'm a n00b ](*,)

---

### Post by taurus on 2006-11-08
Boot into recovery mode from GRUB menu and edit your /etc/hosts from there...

```
nano -w /etc/hosts
```

---

### Post by Epica on 2006-11-08
thanks but what i wanted to know was is there anything else i need apart from

127.0.0.1 localhost

in the file?

---

### Post by taurus on 2006-11-08
Here is what I use for my /etc/hosts...

```

127.0.0.1       localhost
127.0.1.1       Taurus.com   Taurus

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
Otherwise, you can make the first line to look like the one below and forget about the second line then...

```

127.0.0.1     localhost  localhost

```

---

### Post by CatKiller on 2006-11-08
> **Epica said:**
> thanks but what i wanted to know was is there anything else i need apart from

127.0.0.1 localhost

in the file?

It should start

```
127.0.0.1 localhost commander-desktop
```

provided **commander-desktop** is still what it says in **/etc/hostname**.

---

### Post by Epica on 2006-11-10
worked fine. thanks for the help :)

---

