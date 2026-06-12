---
title: "Kylix on Ubuntu 7.04"
date: 2007-09-28
forum: General Help
---

### Post by kzez1986 on 2007-09-28
I've been trying to install Kylix 3 on Ubuntu all day and I can't. I tried Kylix Open and Enterprise. Enterprise installs bad (fiels startbcb, startdelphi are missing). Next, I tried Open Edition, but after install I see an error:

jakub@jakub-desktop:~$ ./startkylix
/home/jakub/kylix_oe/bin/Kylix: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

export LD_ASSUME_KERNEL=2.4.1;./startkylix resulted in another error: /bin/bash: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory

I tried to find a solution but I don't know what to do. I would like to develop applications in C++ Builder in Linux so it is very important for me to run this app.

Thank you in advance for your help.

---

