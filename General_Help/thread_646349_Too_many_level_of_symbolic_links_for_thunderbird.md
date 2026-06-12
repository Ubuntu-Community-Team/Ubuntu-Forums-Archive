---
title: "Too many level of symbolic links for thunderbird"
date: 2007-12-21
forum: General Help
---

### Post by mohtasham1983 on 2007-12-21
Hi ubuntuers,

I've been receiving this error when running thunderbird from the menu because the command to run it is thunderbird %u. But when I run it using only thunderbird it's fine. I don't have any problem with running thunderbord by this way, but the problem is that when I click on some email address in firefox, thunderbird doesn't open automatically and I have to do everything manually which is headache if you want to do it more than 50 times.

I issued this command which I got the following results:

[PHP]ls -ld /usr/bin/thunderbird[/PHP]

[PHP]lrwxrwxrwx 1 root root 32 2007-12-21 01:02 /usr/bin/thunderbird -> /usr/lib/thunderbird/thunderbird
[/PHP]

Any idea how I can get rid of this message?

---

