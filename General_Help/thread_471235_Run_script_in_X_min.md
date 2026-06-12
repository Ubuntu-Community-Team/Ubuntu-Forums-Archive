---
title: "Run script in X min"
date: 2007-06-11
forum: General Help
---

### Post by Kuraudo on 2007-06-11
I'm trying to hibernate my system after X min. How can I do that? I guess it's the /etc/acpi/hibernate.sh script I should run but how can I make it run after say 30 min from now?

---

### Post by reclusivemonkey on 2007-06-12
```

at now + 30 minutes

```

You will then be in the "at" shell; just add /etc/acpi/hibernate.sh, but if this will only run as root, then you will need to do it as root; so using sudo at should work.

---

