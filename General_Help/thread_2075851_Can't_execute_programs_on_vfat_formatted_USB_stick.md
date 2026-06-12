---
title: "Can't execute programs on vfat formatted USB stick"
date: 2012-10-24
forum: General Help
---

### Post by Magnentius on 2012-10-24
Hi all,

I am using Lubuntu 12.10. I have a USB stick with just vfat formatting on which are several odt files and also some of my own binary executables which I compiled from my own CPP files.

When I want to start these executables in the terminal however, I see "access denied".

```
magnentius@magnentius-pc:/media/magnentius/KINGSTON/cpp$ ./cpprog
bash: ./cpprog: Access denied

```

I understand why this happens of course, because vfat can't log the executable permission (chmod +x). It shouldn't happen however, because one should be able to run an executable from an USB stick, and in Ubuntu this was always possible. It isn't in Lubuntu however.

So what can I do about this to make this possible?

Thanks in advance for your answer!

---

