---
title: "Edgy generic kernal won't boot"
date: 2006-11-01
forum: General Help
---

### Post by m.musashi on 2006-11-01
Let me start by saying I've been combing the forums regarding the generic kernel and I admit I'm not quite understanding. It seems that the generic kernel is just that - generic. It works on all systems.

In my case, I have a core duo laptop that was running dapper with the 686 kernel. Since edgy was supposed to improve some laptop features, I went ahead and did the upgrade. When it was finished, it had both the generic and 386 kernels (maybe because I had beryl and it needs that???). Both were installed by the upgrade - I didn't add the 386 kernel. Of course, when I boot with the 386 kernel I do not have dual core support. I tried to boot with the generic kernel but it doesn't. It just sits there with a flashing cursor and does nothing - no error, nothing.

Can anyone explain what a dual core computer should be using and if it's the generic, how to I get it to boot? Will I not be able to run beryl with the generic kernel? Will it support dual core? I may just wipe the slate clean and install from scratch but I'd rather take the opportunity to add to my knowledge base rather than take the easy way out.

Thanks in advance.

---

### Post by m.musashi on 2006-11-02
After a bit more research, I think I can answer one of my own questions. It seems the generic kernel is the one I should use on a dual-core (or any other cpu). As I understand it, the generic kernel will offer the same (better?) performance as the 686-smp. If I'm mistaken here, please set me straight.

However, I still cannot figure out why the generic kernel won't boot or why the 386 was also installed during the upgrade unless it had to do with beryl.

I'm afraid if I remove the 386 kernel the computer won't boot at all. As it stands, only the 386 kernel boots. None of the dapper kernels or the generic will (including the recovery options). I'd greatly appreciate any insight into how to fix this. I really want to see how edgy performs on a laptop but without the dual core support it feels like using only half the computer :).

---

### Post by reazn on 2006-11-03
I'm having the same issue..

after upgrading to edgy, i went and installed the 686 kernel, not thinking the generic one would support smp, but supposedly it does.

I've tried booting it, but it just freezes, tried with recovery mode and it seems to be freezing when mounting the root filesystem.. 

I've just re-installed it and i'll try again now.

---

### Post by barbarian on 2006-11-03
Yes I can confirm it, black screen after reboot with linux-image-2.6.17-10-generic. It forced me, to roll back to linux-image-2.6.15-27-k7:(

I have 32bit Athlon 2500 XP Barton

---

### Post by m.musashi on 2006-11-03
> **reazn said:**
> I'm having the same issue..

after upgrading to edgy, i went and installed the 686 kernel, not thinking the generic one would support smp, but supposedly it does.

I've tried booting it, but it just freezes, tried with recovery mode and it seems to be freezing when mounting the root filesystem.. 

I've just re-installed it and i'll try again now.

Are you installing on a laptop? Did a fresh install work? I haven't done that yet but I suppose it's the easiest solution. I guess this is why it's called edgy:).

---

### Post by reazn on 2006-11-04
no not a laptop, but i have a pentium d (dual core).

this didn't fix it either, im still using 2.6.17-10-386

will post in here if i find a solution.. i want smp!

---

### Post by m.musashi on 2006-11-04
> **reazn said:**
> no not a laptop, but i have a pentium d (dual core).

this didn't fix it either, im still using 2.6.17-10-386

will post in here if i find a solution.. i want smp!

I broke down and just reinstalled fresh. The result - generic kernel boots and I have dual core support. Conky said something like "generic on i686" for the kernel entry, and both cores scale independently. Clearly something is being recognized. I think my problem was the result of a buggy upgrade perhaps confounded by a lot of customizing on my part. The fresh install works just fine. Of course, the instructions for beryl say to install the 386 kernel so I don't know if that means you can have smp or beryl but not both in edgy.

---

### Post by braiden on 2006-11-06
I also had the same problem after upgrading to 6.10. I fixed the problem by removing and reinstalling the linux-generic packages;

Try;

sudo dpkg-reconfigure linux-image-2.6.17-10-generic

reboot, and see if it works. If not; reinstall the packages.

dpkg -r linux-generic \
        linux-image-2.6.17-10-generic \
        linux-restricted-modules-generic \
        linux-restricted-modules-2.6.17-10-generic

(I might be missing a package or two. I just removed everything to satisfy dependencies.)

then apt-get install them back. Worked for me at this point.

If it still doesn't work. Try removing 'quiet splash' from your boot loader, you should be able to see the error preventing your boot.


Cheers.

---

### Post by reazn on 2006-11-07
> **braiden said:**
> I also had the same problem after upgrading to 6.10. I fixed the problem by removing and reinstalling the linux-generic packages;

Try;

sudo dpkg-reconfigure linux-image-2.6.17-10-generic

reboot, and see if it works. If not; reinstall the packages.

dpkg -r linux-generic \
        linux-image-2.6.17-10-generic \
        linux-restricted-modules-generic \
        linux-restricted-modules-2.6.17-10-generic

(I might be missing a package or two. I just removed everything to satisfy dependencies.)

then apt-get install them back. Worked for me at this point.

If it still doesn't work. Try removing 'quiet splash' from your boot loader, you should be able to see the error preventing your boot.


Cheers.

i've tried reinstalling the kernel.. 

this is giving me the sh*ts

---

### Post by m.musashi on 2006-11-07
> **reazn said:**
> i've tried reinstalling the kernel.. 

this is giving me the sh*ts

Are you running beryl? I've found that with beryl the generic kernel doesn't boot. Perhaps that is just my system but the how to for beryl does say to install the 386 kernel. I haven't found much info but in my case beryl and the generic kernel seem incompatible.

---

### Post by aleko52 on 2006-11-10
I had the same problem, try this:

sudo dpkg --purge linux-restricted-modules-2.6.17-10-generic

sudo apt-get install linux-restricted-modules-2.6.17-10-generic

That solved my problem, now Beryl works with the generic kernel

---

