---
title: "Deleted /etc/acpi/battery, HELP!"
date: 2008-03-13
forum: General Help
---

### Post by anindya_m on 2008-03-13
Hi, I am running Feisty Fawn (7.04) on a laptop. While doing some script editing I inadvertently deleted the file /etc/acpi/battery. Can someone please post the contents so that I can restore it. I would greatly appreciate any help.

---

### Post by {BzF}~JOKesTER on 2008-03-13
This Is The File In Mine - I'm In 7.10 Though...

15-anacron.sh

Heres The File::):)


Hope This Helps You!!!:popcorn:

---

### Post by anindya_m on 2008-03-13
Hi, thanks for the file. Is /etc/acpi/battery a symbolic link to this file? I ask because I have the same file in both battery.d and suspend.d directories.

---

### Post by {BzF}~JOKesTER on 2008-03-13
I Think So Yes.:)

---

### Post by anindya_m on 2008-03-13
Okay great. So which file does it point to (not that it matters, since both files are identical, but just out of curiosity). Thanks again for your help :)

---

### Post by {BzF}~JOKesTER on 2008-03-13
Sorry But I Don't Really Know For Sure.:lolflag:

---

### Post by anindya_m on 2008-03-13
I mean, what is the output of 

```
ls -l /etc/acpi/battery
```

?

---

### Post by {BzF}~JOKesTER on 2008-03-13
-rwxr-xr-x 1 root root 168 2007-03-04 23:38 15-anacron.sh

---

### Post by anindya_m on 2008-03-13
Ok. Thanks!

---

### Post by {BzF}~JOKesTER on 2008-03-13
If You'd Like To Thank Me Press The "Thank" Button

---

