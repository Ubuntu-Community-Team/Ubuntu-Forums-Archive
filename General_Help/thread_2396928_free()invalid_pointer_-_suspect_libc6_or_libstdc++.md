---
title: "free():invalid pointer - suspect libc6 or libstdc++6"
date: 2018-07-23
forum: General Help
---

### Post by kazakore on 2018-07-23
I reported a little while having an issue that I can't open KDenLive and when trying from the terminal I get the error reported "free(): invalid pointer" and following instructions I had tried removing an reinstalling the qt5 libraries and some other steps with no joy.

I just found out I get the same error when I try and open hydrogen.

Checking the dependencies of both there are two libraries used by both so I would have to guess one of these is at fault. Namely:
libc6
libstdc++6

I would try removing and reinstalling these (tried a apt-get --reinstall install of them already) but they remove many core applications including apt, and without apt I don't know if or how I would go about reinstalling everything removed.

Is there anything I can do expect reinstall the system from scratch to fix this?

I have run a basic memtest but maybe I should run one for longer. As it happens everything and on attempting to open, not a crash once running, I don't think it's a RAM issue though...

---

### Post by kazakore on 2018-07-23
Just installed US18.04 on VirtualBox and did a dist-upgrade and both kdenlive and hydrogen run there so I'm confident a reinstall would fix it. But I'd rather not resort to that! Any way to repair whatever is broken on a running system?

---

### Post by kazakore on 2018-07-24
> **kazakore said:**
> 
Is there anything I can do expect reinstall the system from scratch to fix this?


I guess I'll be reinstalling then.... :(

---

