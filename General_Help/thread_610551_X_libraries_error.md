---
title: "X libraries error"
date: 2007-11-12
forum: General Help
---

### Post by aek21 on 2007-11-12
Hello everybody.
I am a new member in ubuntuforums, and also a new linux-user. I have installed ubuntu 7.10.
My problem is that when i try to compile any .tar.gz program (source code) it returns after a while:

```
checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!
```

I have installed gcc, g++, build-essential libraries, x-window-system-core, but... always the same error.

Any idea what happens?

Thanks for your time.

PS I am not expert in linux. I use it for about a month (since 7.10 was released)

---

### Post by bingoUV on 2007-11-12
install xserver-xorg-dev using apt-get / synaptic / add-remove software .

---

### Post by aek21 on 2007-11-12
> **bingoUV said:**
> install xserver-xorg-dev using apt-get / synaptic / add-remove software .

thanks! now it goes on.

Then i installed qt, ok with that.

but i have another error:

```
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
```

what to do now? (i think i must install kdelibs, am i correct?)

---

### Post by bingoUV on 2007-11-13
Not sure, could be kdelibs. Is there some package name ending with dev, and starting with kde? That might provide the headers.

---

### Post by yugan on 2008-06-10
> **bingoUV said:**
> Not sure, could be kdelibs. Is there some package name ending with dev, and starting with kde? That might provide the headers.


i guess 

"kdebase-dev"

---

