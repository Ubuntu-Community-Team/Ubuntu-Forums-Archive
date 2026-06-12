---
title: "Keyboard layout(?) not working properly anymore"
date: 2014-08-18
forum: General Help
---

### Post by UncleMonty on 2014-08-18
For some reason when I select a pound sign (over the number 3) I get a #. When I select inverted commas (over the number 2) I get @. How I can troubleshoot this problem please? (I am using Ubuntu 14.04).

---

### Post by coffeecat on 2014-08-18
What you are expecting sounds like the UK keyboard layout, but you have the US keyboard set in System Settings -> keyboard -> click the text entry link. If you then click on + you can add the English (UK) keyboard and move it to the top of the list with the up arrow button. It might also be worth checking to see what your locale is set to with this terminal command:

```
locale
```

---

### Post by UncleMonty on 2014-08-18
locale
LANG=en_GB.UTF-8
LANGUAGE=en_GB:en
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=

---

### Post by UncleMonty on 2014-08-18
Fixed. Thanks :)

---

### Post by coffeecat on 2014-08-18
Glad to hear it. :)

---

