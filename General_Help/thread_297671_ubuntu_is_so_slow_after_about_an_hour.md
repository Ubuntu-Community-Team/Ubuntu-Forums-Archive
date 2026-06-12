---
title: "ubuntu is so slow after about an hour"
date: 2006-11-11
forum: General Help
---

### Post by billylh on 2006-11-11
i have edgy installed on an athlon xp 1800 with 512mb of ram and everythign is fine after a fresh boot or reboot but after about an hour the system slows down and everything takes really long to load(ie, firefox takes about 10 minutes to load).  i dont understand what could be going on. the system was installed about a week ago and its been doing it since the beginning.  any help would be greatly appreciated.

~bh

---

### Post by jordilin on 2006-11-11
open a console terminal and type:
```
top
```
and tell us which processes are on top of the list. Perhaps sth is consuming your cpu or memory.

---

### Post by billylh on 2006-11-11
top - 13:40:12 up  3:15,  2 users,  load average: 2.37, 2.31, 2.30
Tasks:  94 total,   1 running,  93 sleeping,   0 stopped,   0 zombie
Cpu(s): 15.9%us,  0.7%sy,  0.0%ni, 81.7%id,  0.0%wa,  1.0%hi,  0.7%si,  0.0%st
Mem:    516052k total,   509852k used,     6200k free,    10620k buffers
Swap:  1502036k total,    28260k used,  1473776k free,   172244k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                        
 7640 billy     16   0  539m 140m  25m S 14.6 27.9   9:59.21 gij-4.1                                        
 4059 root      15   0 81032  64m 8540 S  1.7 12.9   6:45.36 Xgl                                            
10707 billy     15   0  157m  49m  21m S  0.3  9.8   1:23.84 firefox-bin                                    
11620 billy     15   0 51864  14m 9676 S  0.3  2.9   0:05.30 gnome-terminal                                 
11643 billy     16   0  2248 1124  840 R  0.3  0.2   0:00.18 top                 


---------------------------------------------
these were the only ones that were using any of the cpu

~bh

---

### Post by polly1 on 2006-11-11
Hi

Are you using any particular program when your computer slows down, or does this happen in general use.

I suggest you type the command "top" in a terminal both at boot up and when 
your machine slows down and post the results. This will help to pinpoint any  memory hogging processes.

---

### Post by polly1 on 2006-11-11
Hi sorry

ignore my post- I got waylaid

---

### Post by billylh on 2006-11-11
top - 14:01:14 up 1 min,  2 users,  load average: 2.84, 1.18, 0.43
Tasks:  94 total,   1 running,  92 sleeping,   0 stopped,   1 zombie
Cpu(s): 16.9%us,  4.3%sy,  0.0%ni, 76.7%id,  0.7%wa,  0.7%hi,  0.7%si,  0.0%st
Mem:    516052k total,   383136k used,   132916k free,    21340k buffers
Swap:  1502036k total,        0k used,  1502036k free,   203828k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4083 root      15   0 44792  30m 7636 S  7.7  6.0   0:03.79 Xgl                
 4116 root      15   0 21636  13m 3708 S  6.3  2.7   0:01.41 Xorg               
 4759 billy     15   0 51460  14m 9564 S  4.0  2.8   0:00.80 gnome-terminal     
 4542 billy     15   0 14896 8376 6484 S  1.7  1.6   0:00.55 metacity           
 4687 billy     15   0  150m  35m  19m S  1.0  7.0   0:06.26 firefox-bin        
 4547 billy     15   0 38660  14m  10m S  0.3  3.0   0:01.43 gnome-panel   

------------------------

my computer actually froze up after the last post and these are the results of top after reboot.

---

### Post by billylh on 2006-11-11
could xgl be doing this?  i actually installed it but dont run it because it i cant get my nvidia drivers working right.  if i removed it do you think it would speed everything up?

---

### Post by polly1 on 2006-11-11
Hi

Can you click System>Administration>System Monitor>Processes and post the results. 

You do have a memory hogging program-take a look at line 4 of both "top" posts to see what I mean. The CPU usage of 15.9% and 16.9% seems reasonable.
You can try removing xgl, but this is probably not the problem.

---

### Post by billylh on 2006-11-11
[IMG]http://mail.google.com/mail/?attid=0.1&disp=emb&view=att&th=10ed9870dfa92564[/IMG]

---
my power supply burnt up on me...seem to be having alot of problems lately...hope this screenshot works/helps

---

### Post by billylh on 2006-11-11
i managed to check the processes when the system got really bogged down and it appears to be caused by gij-4.1 which uses anywhere from 50-85%(that i've seen) before it freezes up and needs to be rebooted.

---

### Post by polly1 on 2006-11-12
[QUOTE=billylh;1745756]i managed to check the processes when the system got really bogged down and it appears to be caused by gij-4.1 which uses anywhere from 50-85%(that i've seen) before it freezes up and needs to be rebooted.

Hi
I did wonder about that and found a bit more info. on this process, but it didn't mean very much to me. However, it should not be using so much cpu/memory resources. It is possible to set how much CPU time a process uses and this is called renicing, but it should only be used sparingly, such as when a computer is freezing up,as yours is.

Run "top" again and take a note of the PID number along the left hand side of the entry gij-4.1. Then type "r" (this does not have to be done in any box)  while top is running and type in this PID number. You will be asked then to type in a renice value. This scale goes from -20 (highest priority) to 19 (lowest priority). You should type in 19 and your problem of freezing should be solved.

---

### Post by commodore on 2006-11-12
I have this problem since Dapper. When I start my computer it's ok. At one point it just goes crazy, I can't do anything. It got worse with edgy. Sometimes I have only Firefox opened (one window) and I can't do anything. My computer is an Athlon 1ghz with 256mb RAM. I haven't tried the top thing yet.

---

### Post by turkenator on 2006-11-12
yeah u should post the top results so we can try and help u

---

### Post by commodore on 2006-11-12
gij and Xorg are fighting for the topmost position in top's list. I think it is gij's fault. I installed j2re but with it Azureus crashed after start :D.

---

### Post by turbojugend_gr on 2006-11-12
Java and XGL are not to be used in low-end machines, you should try to find alternatives...

---

### Post by commodore on 2006-11-12
Yeah OpenOffice is really slow but Azureus is great until it freezes everything :D.

---

### Post by billylh on 2006-11-29
> **commodore said:**
> gij and Xorg are fighting for the topmost position in top's list. I think it is gij's fault. I installed j2re but with it Azureus crashed after start :D.

i got j2re installed as well and removed gij and i get the exact same problem, azureus crashes after load.  other than that, everything works fine...sort of, but thats another post.

Thanks everyone for helping!:-D

---

