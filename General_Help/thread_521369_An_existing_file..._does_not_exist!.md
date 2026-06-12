---
title: "An existing file... does not exist!"
date: 2007-08-09
forum: General Help
---

### Post by MaxxJ on 2007-08-09
Hello,

I'm trying to start that TeamSpeak server I added to my Ubuntu server and look what I'm having as a [weird] problem :

[Screenshot]("http://img378.imageshack.us/img378/1336/screenshotqt2.png")

No matter if I'm root, or not, calling it from the same directory or anywhere else... I don't know what to think about this!

MJ

---

### Post by apetresc on 2007-08-09
We had a problem like this yesterday. It was caused because the user had a 64-bit computer, but was trying to run a 32-bit binary.

Is your processor 32-bit or 64-bit?
Is the binary 32-bit or 64-bit?

If you're not sure about the first question, use ```
cat /proc/cpuinfo
```
If you're not sure about the second question, use ```
file server_linux
```

If they are not both one or the other, it will not work :(

---

### Post by MaxxJ on 2007-08-09
It's a 64-bits CPU with very probably a 32-bits application... Always thought it should work anyway! I'll try to find a 64-bits version. I guess there's no way to make it work?!

Thank you!

MJ

---

