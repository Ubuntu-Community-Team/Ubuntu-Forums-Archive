---
title: "Dell Latitude E6500 - Touchpad does not work"
date: 2014-08-28
forum: General Help
---

### Post by luke35 on 2014-08-28
Hey all,
Just installed Ubuntu 14.04.1 on a Dell Latitude E6500 and the touchpad doesn't seem to be working. Anybody have any tricks that I could try? 

Thanks in advance!

---

### Post by varunendra on 2014-08-29
Welcome to the forums luke35!

> **luke35 said:**
> Anybody have any tricks that I could try?

Some old ones : [http://ubuntuforums.org/showpost.php?p=12880188](http://ubuntuforums.org/showpost.php?p=12880188) (Change the name of the touchpad to match yours; see the initial posts on the thread to see how to determine that).

If these don't help, please post the outputs of -
```
xinput
synclient
lsmod
grep -i touchpad /var/log/syslog
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by luke35 on 2014-08-31
Sorry. I just found that the touchpad was disabled in BIOS. How embarrassing!! Thanks for the advice though.

---

### Post by varunendra on 2014-09-01
No problem! Even better in sense that it wasn't Ubuntu's fault of any kind :p

Hope you'd enjoy the OS as well as the community here. :)

---

