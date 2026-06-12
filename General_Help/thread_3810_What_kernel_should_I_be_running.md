---
title: "What kernel should I be running?"
date: 2004-11-09
forum: General Help
---

### Post by Julius on 2004-11-09
I have an AMD Athlon 1GHz proccessor, and I recently downloaded the linux-686 kernel package.
I'm not sure I should be running the 686 one or the k7 one.

Any suggestions?

---

### Post by allen on 2004-11-09
[QUOTE=Julius]I have an AMD Athlon 1GHz proccessor, and I recently downloaded the linux-686 kernel package.
I'm not sure I should be running the 686 one or the k7 one.

Any suggestions?[/QUOTE]
 I'm on an AMD AthlonXP 2600+ and went with the k7 one after a quick google.

---

### Post by fng on 2004-11-09
go for the k7 !!

---

### Post by Julius on 2004-11-09
I'm running the K7 kernel now :) Don't notice any big differencies :P

---

### Post by Opiate on 2004-11-09
Running the -k7 kernel on a mobile barton. No noticeable difference but kept it anyways for good measure :)

---

### Post by dawynn on 2004-11-09
I've got an Athlon with only a 1.2 GHz processor -- so just slightly faster than your system.  I've been running the K7 kernel previously in Debian, now in Ubuntu with no problems.

---

### Post by astroholic on 2004-11-09
[QUOTE=Julius]I have an AMD Athlon 1GHz proccessor, and I recently downloaded the linux-686 kernel package.
I'm not sure I should be running the 686 one or the k7 one.

Any suggestions?[/QUOTE]
 I have an AMD Athlon and installed the k7 kernel with a problem.  I didn't notice any differences, except that my NVIDIA drivers ran slow.  If I switch to the 686 kernel, NVIDIA runs smoothly.  Just some food for thought.

Astro

---

### Post by Julius on 2004-11-09
Second question: I noticed a huge disk usage since I installed the 686 and K7 kernels. (50 mb for the k7 kernel and I dont remember how much for the 686).
Now that I will not use 386 anymore, is there anyway to uninstall it definitely? I checked it for uninstall in synaptic, but it just released less than a megabyte :P 

I'm running ubuntu on a 5GB partition, that's why I care :P Anyway, I set 5GB because this was going to be my "testing partition"  :P Now that I've decided to use linux as my main OS (Haven't touched windows for more than two weeks), guess I'll have to reformat my whole HD. I'll have to have windows still installed because my bro  refuses to use linux :P

---

### Post by Opiate on 2004-11-09
[QUOTE=Julius]Second question: I noticed a huge disk usage since I installed the 686 and K7 kernels. (50 mb for the k7 kernel and I dont remember how much for the 686).
Now that I will not use 386 anymore, is there anyway to uninstall it definitely? I checked it for uninstall in synaptic, but it just released less than a megabyte :P 

I'm running ubuntu on a 5GB partition, that's why I care :P Anyway, I set 5GB because this was going to be my "testing partition"  :P Now that I've decided to use linux as my main OS (Haven't touched windows for more than two weeks), guess I'll have to reformat my whole HD. I'll have to have windows still installed because my bro  refuses to use linux :P[/QUOTE]

sudo apt-get remove linux-386

?

---

### Post by Julius on 2004-11-09
I did that already with synaptic. I was expecting it to remove the grub entry for it and to do the inverse things it did when installed :P

---

### Post by jdong on 2004-11-09
Note that AMD Athlons and Durons are actually **k6**'es, not k7's! (Trust me -- I've been a Gentoo user for too long.)

gcc-wise, athlons should be optimized with -march=athlon or -march=k6. Athlon Thunderbirds [subset of athlon k6's] should be optimized with -match=athlon-tbird.

Only Athlon XP's may be optimized with -march=athlon-xp, which is synonymous with -march=k7. Again, k7 (athlon XP) is NOT k6 (athlon).

I don't know what kind of trouble you may get with running k7 code on a k6, but that may explain the NVidia slowness...


Athlon's should use i686 kernels.

---

### Post by uggeli on 2004-11-29
So you're saying that I should install i686 kernel to my AMD Athlon Thunderbird instead of k7 kernel? Just wanted to be sure cause in ['Tweaking Ubuntu after your first installation.-HOWTO'](http://ubuntuforums.org/showthread.php?t=3713) there are mention:

9. Installing a CPU specific kernel.
Quote:
1. sudo apt-get install linux-686 for newer Intel/AthlonXP
2. sudo apt-get install linux-k7 for any AMD Processors
3. sudo apt-get install linux-686-smp for Dual Intel Processors


And that may confuse allso some other newbies than me, so if you could say once more which is the way I should do?

---

### Post by eruin on 2004-11-29
[QUOTE=jdong]Note that AMD Athlons and Durons are actually **k6**'es, not k7's! (Trust me -- I've been a Gentoo user for too long.)

gcc-wise, athlons should be optimized with -march=athlon or -march=k6. Athlon Thunderbirds [subset of athlon k6's] should be optimized with -match=athlon-tbird.

Only Athlon XP's may be optimized with -march=athlon-xp, which is synonymous with -march=k7. Again, k7 (athlon XP) is NOT k6 (athlon).

I don't know what kind of trouble you may get with running k7 code on a k6, but that may explain the NVidia slowness...


Athlon's should use i686 kernels.[/QUOTE]
 Eh, athlons are all k7.
K6 are the old k6-named processors, ie k6-II, k6-III, etc. Old stuff.

athlon, athlonxp are k7 - march athlon / athlonxp
athlon64 is k8

---

