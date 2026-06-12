---
title: "One cpu is missing after 2.6.17-10-386 install ..."
date: 2006-10-28
forum: General Help
---

### Post by ss0007 on 2006-10-28
Hi,
I have installed 2.6.17-10-386 kernel when installing nvidia driver. Now whn i open the system monitor , i see only one CPU being monitored !! I have core duo processor . 

Previuosly, i think i did an apt-get to linux-kernel-common and i saw the kernel package installed from amarnath repo. I also looked for linux 2.6.17-10-386-smp  but i saw , it 's thr only as 2.6.17-10-686-smp .

wht do i do ?
pls help ,

---

### Post by Azathoth_ on 2006-10-28
It must be a problem with system monitor. I have the same issue but i have installed gkrellm and it appears my two cpu's.

---

### Post by syadnom on 2006-10-28
this is because you installed the -386 kernel.  just an FYI, there are no multiprocessor i386 systems, so when building this kernel the multiprocessor support is disabled.  install a -686 kernel and you will get your second core.

> **ss0007 said:**
> Hi,
I have installed 2.6.17-10-386 kernel when installing nvidia driver. Now whn i open the system monitor , i see only one CPU being monitored !! I have core duo processor . 

Previuosly, i think i did an apt-get to linux-kernel-common and i saw the kernel package installed from amarnath repo. I also looked for linux 2.6.17-10-386-smp  but i saw , it 's thr only as 2.6.17-10-686-smp .

wht do i do ?
pls help ,

---

### Post by aliyanage on 2006-10-28
Hi,

did you already try the command: sudo uname -s
if you execute that command what's the output you get?

I had all my processes monitoring in the background and it only displayed one core instead both of them until I checked with this command and found out that it was a mistake regarding the display options...

---

### Post by ss0007 on 2006-10-31
Thx for all ur replies ...
686 kernel works fine now .. 
Thx

---

