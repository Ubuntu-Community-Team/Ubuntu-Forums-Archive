---
title: "Making swap lowest priority"
date: 2008-04-03
forum: General Help
---

### Post by Gesent on 2008-04-03
Hi

I have installed ubuntu server in a box with a network filesystem and I've activated a swap file (with dd, mkswap and swapon). However since disk operations are very slow with iscsi I'd like to avoid using swap at all unless it's necessary to avoid the server crashing. Is there any way to do that?

And before you mention it, I know swapon can take a priority option but that only sets the priority among swap files or devices, not between using ram or swap. How do I tell linux to not touch the swap unless the ram is 100% full?

Thanks in advance.

---

### Post by kerry_s on 2008-04-03
add->
vm.swappiness=10
vm.overcommit_memory=2
vm.overcommit_ratio=90

to-> /etc/sysctl.conf

but why don't you just use dynamic swap instead, it will create swap files only when needed, so you don't have to do it manually and it's deleted when no longer needed.

sudo apt-get install swapd

you can do some research there are other programs that do dynamic swap.
swapd is the 1 i used when i had lots of ram and the swap partion would barely get used if at all, so i just didn't use a swap partion.

---

### Post by Gesent on 2008-04-03
> **kerry_s said:**
> add->
sudo apt-get install swapd


That is exactly what I was looking for. Btw the default swap size of swapd is 4MB which is too little imho. Is there any way to pre-format the swap files so I dont suffer a slow down every time they are activated?

---

### Post by kerry_s on 2008-04-04
> **Gesent said:**
> That is exactly what I was looking for. Btw the default swap size of swapd is 4MB which is too little imho. Is there any way to pre-format the swap files so I dont suffer a slow down every time they are activated?

you can adjust the size of the swap file in /etc/swapd.conf
i had mine set at 128mb, which was more than enough.
you can also adjust the check time, i think the default was like 3min, which is kind of long, i reduced it to a minute and had it set to activate when ram reached 75%, so the swap file would be ready before the ram was maxed.

---

