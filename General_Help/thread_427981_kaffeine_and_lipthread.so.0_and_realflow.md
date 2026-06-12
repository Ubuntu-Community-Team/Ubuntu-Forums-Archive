---
title: "kaffeine and lipthread.so.0 and realflow"
date: 2007-04-29
forum: General Help
---

### Post by skopa on 2007-04-29
i don't know if it's specifically a kaffeine problem but this is it:
i'm trying to install/make realflow 4 start which needs libpthread.so.0 which does not really exists, so i create a symlink with that name to libpthread.so.20.0.27
well then when i try to start kaffeine i'm getting the following:

kaffeine: /usr/lib/libpthread.so.0: no version information available (required by kaffeine)
kaffeine: /usr/lib/libpthread.so.0: no version information available (required by /usr/lib/libDCOP.so.4)
kaffeine: /usr/lib/libpthread.so.0: no version information available (required by /usr/lib/libqt-mt.so.3)

:confused: 
how can i solve this so everybody in my system is happy?

i'm on ubuntu feisty amd64 and not really an expert

---

### Post by skopa on 2007-04-30
anybody?
any suggestions at least to whom should i report this?

---

### Post by skopa on 2007-05-02
an answeeeeeeeeeer?

---

### Post by veeraa on 2007-09-07
Kaffine works for me staraight away. I'm not able to reproduce the problem in my case. Can you explain what you did a bit more. Are you using the latest version from a differrent gcc or something?

But I' helped a friend with realflow on Ubuntu 7.04. He installed realflow but was unable to start using ./realflow because it cribbed about something like libpthread.so not found. I found that 'realflow' was actually a script which sets up the environment before running realflow.bin. An ldd realflow.bin was able to resolve the link to lbpthread.so. But the program refused to budge. I tried setting LD_PRELOAD as well but things still failed. The culprit here is the LD_ASSUME_KERNEL. Commenting this out (putting a '#' at the start of the line) solved the problem. Use this option only if you run into problems with ld.so(the dynamic loader). Otherwise the realflow window should open up and ask for a license.

---

### Post by veeraa on 2007-09-08
BTW all those things which I described above was on intel core 2 duo with i386 ubuntu 7.04.

---

### Post by 500cuts on 2008-06-06
Commenting out LD_ASSUME_KERNEL totally works.  Thanks.

---

