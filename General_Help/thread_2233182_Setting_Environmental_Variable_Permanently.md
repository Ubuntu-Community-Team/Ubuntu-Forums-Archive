---
title: "Setting Environmental Variable Permanently"
date: 2014-07-07
forum: General Help
---

### Post by kaushal007 on 2014-07-07
Hello Friends,
following environmental Variable i need to set permanently under my Ubuntu 12.04  how do i proceed.??

while working on my application every day i need to perform following task, i want to make this permanently
export              LIBRARY_PATH=/usr/lib/$(gcc-print-multiarch)
export          C_INCLUDE_PATH=/usr/include/$(gcc-print-multiarch)
export CPLUS_INCLUDE_PATH=/usr/lib/$(gcc-print-multiarch)

Regards

kaushal

---

### Post by sudodus on 2014-07-07
Welcome to the Ubuntu Forums :-)

Put those command lines into your **~/.bashrc **file (if it is enough to have it in your own bash environment). Then they will get into all new terminal windows an text screens.

An alternative to have them globally is to put them into **/etc/bash.bashrc** (and reboot).

---

### Post by monkeybrain20122 on 2014-07-07
Question. Shouldn't they be put in ~/.profile (for user) and /etc/environment (globally) instead?

---

### Post by sudodus on 2014-07-07
Maybe that is better :-)

---

