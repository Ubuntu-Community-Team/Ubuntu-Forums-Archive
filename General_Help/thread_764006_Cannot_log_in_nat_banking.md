---
title: "Cannot log in nat banking"
date: 2008-04-23
forum: General Help
---

### Post by guano on 2008-04-23
Hello all.

I'm running Hardy here, and cannot access my bank account. When I open the page

[https://www2.bancobrasil.com.br/aapf/login.jsp]("https://www2.bancobrasil.com.br/aapf/login.jsp")

I can see the virtual keyboard, but when I cick the "Entrar" (enter), the applet just restarts, and won't login.
Using IcedTea plugin.

Has anyone seen this behaviour?

tks

---

### Post by spydon on 2008-04-23
Have you tried to install the regular Sun JRE?
```
sudo apt-get install sun-java6-plugin
```

---

### Post by guano on 2008-04-25
> **spydon said:**
> Have you tried to install the regular Sun JRE?

Yes, I tried that in the first place. With sun-plugin, the applet (virtual keyboard) won't even show. With icedtea, it shows, but won't login.

tks

---

### Post by spydon on 2008-05-05
Weird... Have you tried in a diffrent browser?

---

### Post by guano on 2008-05-05
Working fine now. I removed all icedtea-related stuff, reinstalled sun-java-6 and did a  update-alternatives --config java.

cheers

---

