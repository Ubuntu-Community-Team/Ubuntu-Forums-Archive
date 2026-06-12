---
title: "Can't install anything"
date: 2007-11-06
forum: General Help
---

### Post by Caz'ar Xiladys'varion on 2007-11-06
Sometimes when I try to install things I get this:

error: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Apparently from what I've googled I need to get hold of compat-libstdc++-33 but my package manager can't find it, and I don't know where to download it. Any help? Thx.

---

### Post by knightzor on 2007-11-06
i think you need to install this package "libstdc++6 - The GNU Standard C++ Library v3"

sudo apt-get install libstdc++6 

see if that helps

---

### Post by Caz'ar Xiladys'varion on 2007-11-06
I already have that installed

---

### Post by knightzor on 2007-11-06
hmm have a read of this it mite help solve your problem. seems to be a similar issue

[http://www.ibm.com/developerworks/forums/thread.jspa?threadID=179835](http://www.ibm.com/developerworks/forums/thread.jspa?threadID=179835)

---

### Post by thecoolcat on 2007-11-08
> **Caz'ar Xiladys'varion said:**
> Sometimes when I try to install things I get this:

error: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

Apparently from what I've googled I need to get hold of compat-libstdc++-33 but my package manager can't find it, and I don't know where to download it. Any help? Thx.

I got similar messages. See this for the message I got : [http://ubuntuforums.org/showthread.php?t=604848](http://ubuntuforums.org/showthread.php?t=604848)

I added all repos: You can add repos under system, administration, software sources. The ubuntu software and updates tab.

After adding all repos, I could add softwares without any problem. Worked for me. You may try.

---

