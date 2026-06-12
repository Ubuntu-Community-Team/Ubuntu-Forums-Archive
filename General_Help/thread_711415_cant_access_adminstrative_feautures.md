---
title: "cant access adminstrative feautures"
date: 2008-02-29
forum: General Help
---

### Post by calculated_coffee_drinker on 2008-02-29
And whenever I try sudo commands I get this error:
```
sudo: unable to lookup 2f:ff via gethostbyname()
```
I cannot access add/remove either it just freezes.
This never happens on my other computer maybe its a problem with this one. This one is a duo core intel 2.8 ghz i gig of ram.

---

### Post by pointone on 2008-02-29
Post the output of "cat /etc/hosts".

---

### Post by calculated_coffee_drinker on 2008-02-29
Ok it shows this.
```
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by calculated_coffee_drinker on 2008-02-29
Should I try installing knoppix or another form of linux instead?

---

### Post by taurus on 2008-02-29
Did you play around with your /etc/hosts?  It's missing one important line at the top.

```
127.0.0.1               localhost.localdomain localhost
```

---

### Post by calculated_coffee_drinker on 2008-02-29
No it says bash: /etc/hosts: Permission denied
.
:confused:

---

### Post by taurus on 2008-02-29
You have to boot into recovery mode from GRUB menu and add that line to your /etc/hosts.

```
nano -B /etc/hosts
```
Save the changes with <Ctrl>o and exit with <Ctrl>x.  Then reboot with

```
shutdown -r now
```

---

### Post by calculated_coffee_drinker on 2008-02-29
> **taurus said:**
> You have to boot into recovery mode from GRUB menu and add that line to your /etc/hosts.

```
nano -B /etc/hosts
```
Save the changes with <Ctrl>o and exit with <Ctrl>x.  Then reboot with

```
shutdown -r now
```

It wont let me do that.

---

### Post by taurus on 2008-02-29
It won't let you do what?  Did you boot into recovery mode from GRUB menu?

---

