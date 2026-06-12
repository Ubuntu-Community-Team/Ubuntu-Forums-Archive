---
title: "[SOLVED] Restricted Drivers Manager for Feisty Server VM"
date: 2007-09-02
forum: General Help
---

### Post by JawsThemeSwimming428 on 2007-09-02
I downloaded a VM of 7.04 Server and used sudo apt-get install ubuntu-desktop to use the desktop version. I am trying to enable restricted drivers for my nVidia GeForce 8600GT graphics card but when I click on the Restricted Drivers  manager I get and error message that says I need to install linux-restricted-modules-2.6.20-16-server. When I fire up Synaptic that package doesn't exist. Is there something else I need to do to convert this to a desktop install only?

---

### Post by lcg on 2007-09-02
> **JawsThemeSwimming428 said:**
> I downloaded a VM of 7.04 Server and used sudo apt-get install ubuntu-desktop to use the desktop version. I am trying to enable restricted drivers for my nVidia GeForce 8600GT graphics card but when I click on the Restricted Drivers  manager I get and error message that says I need to install linux-restricted-modules-2.6.20-16-server. When I fire up Synaptic that package doesn't exist. Is there something else I need to do to convert this to a desktop install only?

This sounds to me like you are using a server kernel. AFAIK, the server kernels do not have restricted modules. Try installing linux-generic and see if that works.

HTH,
Lars

---

### Post by JawsThemeSwimming428 on 2007-09-02
I did install the generic module and it didn't work. The VM is of Ubuntu 7.04 Server. I wasn't sure if running sudo apt-get install ubuntu-desktop would allow me to use the server packages as well as the desktop packages. I still receive the error.

---

### Post by lcg on 2007-09-03
> **JawsThemeSwimming428 said:**
> I did install the generic module and it didn't work. The VM is of Ubuntu 7.04 Server. I wasn't sure if running sudo apt-get install ubuntu-desktop would allow me to use the server packages as well as the desktop packages. I still receive the error.

What kernel is your system running now? Please post the output of
```
uname -a
```

Regards,
Lars

---

### Post by JawsThemeSwimming428 on 2007-09-03
I'm running 2.6.20-16-386...thanks for your help!

---

### Post by lcg on 2007-09-06
> **JawsThemeSwimming428 said:**
> I'm running 2.6.20-16-386...thanks for your help!

OK.

However, this really doesn't tell me whether your system by default boots the -server or the -generic kernel. The output of uname would be more helpful to diagnose the problem, which is why I asked you for it.

Regards,
Lars

---

