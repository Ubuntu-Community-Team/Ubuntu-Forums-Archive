---
title: "First window in chrome isn't displaying properly..."
date: 2022-04-04
forum: General Help
---

### Post by dbee on 2022-04-04
So the first chrome window i open doesn't display properly. It's missing the minimize/maximize icons.

[https://ibb.co/fGQmyk0]("https://ibb.co/fGQmyk0")

See top bar on window image.

> dara@dara-HP-Stream-Laptop-11-y0XX:~$ google-chrome-stable --version
Google Chrome 99.0.4844.84 

> dara@dara-HP-Stream-Laptop-11-y0XX:~$ uname -a
Linux dara-HP-Stream-Laptop-11-y0XX 5.4.0-107-generic #121-Ubuntu SMP Thu Mar 24 16:04:27 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux


---

### Post by him610 on 2022-04-04
Latest Chrome Version 100.0.4896.60 (Official Build) (64-bit)
You should update without delay. There is a zero-day exploit in the wild that Chrome 99 is susceptible to.
The upgrade may address your issue.

---

### Post by dbee on 2022-04-04
Yep. That fixed it, thanks.

I ran a 

> sudo apt upgrade

and it updated google-chrome-stable 

What i don't get though, if there is a security vulnerability for Chrome. Why am i not notified in my Chrome window that there's an update available?

---

### Post by dbee on 2022-04-06
So the upgrade appears to fix the problem on my HP Pavilion, but not on my other system - xubuntu?

---

