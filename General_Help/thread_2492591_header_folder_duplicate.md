---
title: "header folder duplicate"
date: 2023-11-16
forum: General Help
---

### Post by kalish2 on 2023-11-16
Hello, I am desperately trying to use a virtual box and apparently I need to sign some (stuff?) at each session. I don't know why but the secure boot is not always showing, and in any case, it refuses my password. So apparently I need to modify the sign-file located in scripts, which are located in  usr/src/linux-headers-6.2.0-36-generic/ . Or are they? There are actually two header directories, usr/src/linux-headers-6.2.0-35-generic/ and usr/src/linux-headers-6.2.0-36-generic/ both look quite the same. when I run uname -r I get the answer that I am using the 36 kernel. 
My question then:
 should I erase the usr/src/linux-headers-6.2.0-35-generic/ directory?
And maybe an unrelated question, that I might be advised to ask in a different topic: I am supposed
 to modify the sign-file with a script, but what's already written is non sens, so it might already be a key of some sort. Should I really add the script to that part or entirely erase the sign-file file and replace it with the script?

---

### Post by kalish2 on 2023-11-16
Ok apparently it's completely normal that Ubuntu keep several of them.

---

