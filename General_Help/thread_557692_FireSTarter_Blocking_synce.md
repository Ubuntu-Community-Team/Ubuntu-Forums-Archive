---
title: "FireSTarter Blocking synce"
date: 2007-09-23
forum: General Help
---

### Post by Death_Sargent on 2007-09-23
For some reason i have to turn off my firewall to use synce with my mpx220 phone

atached screen shots shoes what connections are active with my phone.

---

### Post by JBAlaska on 2007-09-23
Have you tried right clicking on the offending event and clicking allow?

---

### Post by Death_Sargent on 2007-09-23
It doesn't actually list it as an event. its just blocks the action

---

### Post by por100pre1 on 2007-09-23
If it doesn't show up in the Events tab, add it manually in Policy.

---

### Post by Death_Sargent on 2007-09-25
After manually adding the destination and originating ip's and ports as open there was still no effect.

---

### Post by Death_Sargent on 2007-09-25
found this can some one help me apply this

[http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2003_device_via_USB#Configuring_the_Firewall](http://www.synce.org/index.php/Connecting_your_Windows_Mobile_2003_device_via_USB#Configuring_the_Firewall)

---

### Post by por100pre1 on 2007-09-25
Check this [page]("http://www.fs-security.com/docs/policy-page.php"). If that doesn't work, then do this:

```
sudo iptables -A INPUT -p tcp --dport 5678 -j ACCEPT
```

```
sudo iptables -A INPUT -p tcp --dport 5679 -j ACCEPT
```

and check it with this:

```
sudo iptables -L
```

---

