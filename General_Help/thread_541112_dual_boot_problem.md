---
title: "dual boot problem"
date: 2007-09-02
forum: General Help
---

### Post by linuxnoob40 on 2007-09-02
i was dual booting fine until i reformatted windows last night now it just jumps right to windows without giving me a boot option. can someone please help me get back into my ubuntu partition
thank you.

---

### Post by Zecking on 2007-09-02
i have the same problem...i know its a easy fix... but forgot how to do it:(

edit: i just found an interesting post ...it should help..  [http://www.linux.com/articles/114157](http://www.linux.com/articles/114157) 
 dont have time to try it myself ...but give it a try, let me know how it works out

---

### Post by merlinus on 2007-09-02
Boot from the livd cd, open a terminal and:

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```

Substitute results from find for (hdx,y) and setup (hdx).

-merlin

---

### Post by linuxnoob40 on 2007-09-05
ok i tried this and maybe i did it wrong? under find it found hd0,1 so replaced hdx,1 with hd0,1 and hdx with hd0,1 but when i rebooted it jumped over the boot selection and went straight to windows?

---

### Post by merlinus on 2007-09-05
Seems from what you wrote that it should be:

root (hd0,1}
setup (hd0)

You also might boot from the live cd and post results of:

```

sudo fdisk -l

```

entered in a terminal.

-merlin

---

### Post by linuxnoob40 on 2007-09-06
that did the trick thank you =)

---

### Post by merlinus on 2007-09-06
You are very welcome.  Glad it worked!

-merlin

---

