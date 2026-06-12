---
title: "Swap filling up but not emptying."
date: 2013-05-25
forum: General Help
---

### Post by Henkdroid on 2013-05-25
Hi all, I've recently noticed that my swap is getting completely full after I've been using my laptop for a short period of time.
When I look at top with the swap column the numbers reported there are far lower than shown with System Monitor. [IMG]https://www.dropbox.com/s/aavhqr1j7n6fsyh/Screenshot%20from%202013-05-25%2023%3A03%3A32.png[/IMG] [IMG]https://www.dropbox.com/s/aavhqr1j7n6fsyh/Screenshot%20from%202013-05-25%2023%3A03%3A32.png[/IMG]
I've only noticed it after Chrome updated to version 27 and extensions kept crashing and pages ran out of memory so I don't know if they're linked. Also when I turned off swap the pages still ran out of memory even when I still had some memory left. Also when I completely close Chrome the swap usage doesn't go down.

Computer specs: Lenovo Thinkpad T61, Ubuntu 13.04 64bit, 2GB RAM, 500GB hard drive, 2GHz Core 2 Duo T7250, Intel 965GM graphics.

Does anyone know how to help?

PS: I don't know if the screenshots I've linked will work so here's the links [https://www.dropbox.com/s/aavhqr1j7n6fsyh/Screenshot%20from%202013-05-25%2023%3A03%3A32.png](https://www.dropbox.com/s/aavhqr1j7n6fsyh/Screenshot%20from%202013-05-25%2023%3A03%3A32.png) [https://www.dropbox.com/s/6j236fcukdl0uek/Screenshot%20from%202013-05-25%2023%3A05%3A37.png](https://www.dropbox.com/s/6j236fcukdl0uek/Screenshot%20from%202013-05-25%2023%3A05%3A37.png)

---

### Post by HiImTye on 2013-05-25
try
```
sudo swapoff -a; sudo swapon -a
```

---

### Post by Henkdroid on 2013-05-26
I tried that but it says it cannot allocate memory. When you swapoff it tries to put what was in swap into RAM but there's not enough RAM.

---

### Post by Henkdroid on 2013-05-26
I've tried not using Chrome for a while, using Firefox instead and the same happens so I think I can rule out Chrome.

---

### Post by vanadium on 2013-05-26
> **Henkdroid said:**
> I tried that but it says it cannot allocate memory. When you swapoff it tries to put what was in swap into RAM but there's not enough RAM.

With 2 GB, that is not quite normal. Close all applications, then try the commands again: if it still says it cannot allocate memory, then definitely there is something wrong. In system monitor, processes tab, try to see what is using the memory (you can sort on memory use by clicking the header of the Memory column).

In general, it is normal that swap remains in use even if enough RAM has been freed again.

---

### Post by Impavidus on 2013-05-26
It sounds like there is a memory leak somewhere. Have you tried running your browsers with all plugins disabled? I think there might be a bug in one of your plugins.

---

### Post by efflandt on 2013-05-27
What programs are you running? It definitely sounds like a memory leak, unless you are doing some major graphics or video editing or ripping disks while using tmpfs. The only memory leak I have seen in years was when I was running 11.04 beta and its network manager was leaking.

I run Ubuntu (although 64-bit 12.04) from a 2 core 1 GHz tablet PC with 2 GB RAM booted from SD card using tmpfs (in RAM) for /tmp **without any swap**. It cannot hibernate because its SD slot is internally USB connected, so it does not need swap for that.

My desktop PC (up 20+ hrs) is currently using 765 MB with firefox and a terminal open.  The 4.9 GB cached data is from running tf2 game in Steam earlier.
```
efflandt@xps8100-1204:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7913       5783       2130          0         85       4931
-/+ buffers/cache:        765       7147
Swap:            0          0          0
```

---

### Post by groggin on 2013-05-27
2 gigs of RAM is very minimal on a 64 bit system ...???

---

### Post by Henkdroid on 2013-05-27
Hmm, I got rid of Xorg edgers and it seems to have fixed the problem.

---

