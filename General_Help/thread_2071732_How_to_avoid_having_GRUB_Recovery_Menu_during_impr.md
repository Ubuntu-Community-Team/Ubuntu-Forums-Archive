---
title: "How to avoid having GRUB Recovery Menu during improper shutdown"
date: 2012-10-16
forum: General Help
---

### Post by wilsonmak on 2012-10-16
Hi all,

I don't know when the GRUB Menu comes up while the system shutdowns improperly.  

Is there a way to prevent this? It's because I have an application that does not have a keyboard.  I need to press "Enter" to continue to boot up the box.  Or other way to continue boot up without pressing "Enter" key.

P.S. I'm using Ubutun 10.10

Thanks,
Wilson

---

### Post by s1baker on 2012-10-16
have you tried to update your grub?

```
sudo update-grub
```

---

### Post by wilsonmak on 2012-11-05
Thank you!
Does it relate to the GRUB version?  I will give it a try anyway.
Or can I force not to show this GRUB menu?

Thanks,
Wilson

---

