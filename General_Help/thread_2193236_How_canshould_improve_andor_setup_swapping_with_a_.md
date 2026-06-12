---
title: "How can/should improve and/or setup swapping with a slow harddrive?"
date: 2013-12-11
forum: General Help
---

### Post by jan-goebel-g on 2013-12-11
Hi, im sorry if the forum is wrong, i couldnt decide where to post.

My problem is the following:
-Iv got a Lenovo L420 with 4gb of ram.
-4gb swap file
-Swapability at the default 60 at the moment.

Once the ram usage reaches about 2,7gb my pc gets really slow and i get why. The harddrive is slow, plain and simple (5,2k rpm hdd) and swapping to it while the pc is doing stuff its not helping. 

So, would it help to reduce swapabillity to 0, i didnt read how it works but i figure its not like 0=no swapping but something else thats why im asking here:)

Id really like the pc to not swap at all before i reach 3,3to3,5gb of ram (max should be 3,7 since the gpu needs some of it) which i really rarely reach. Mostly im getting up to 2,7gb ram and 500mb swap which results in awfull performance.


So, is there a way to setup the swapping like that or am i better off just bying another 4gb of ram and do fancy stuff like swap/cache into the ram?
Im thinking about getting some msata drive too but thats not the point of this thread:D.

Thx in advance folks, loving how ubuntu unity developed from a hardware hog to the most efficient "big" DE (kubuntu 900mb vs ubuntu 600mb used at login, LOVE IT).

---

### Post by Bashing-om on 2013-12-11
jan-goebel-g; Hi !

This ??
> 
-4gb swap file

I understand that a swap "file" can be slow, You are not using a swap partition ??
Please post the output of terminal command:
```

sudo fdisk -l

```to see if there is help for this situation.
As to a swapiness value I see 10 as a recommended value for the desk top editions (I have mine set at 10, looks good to me).

[INDENT][INDENT]best regards
[/INDENT][/INDENT]

---

### Post by leclerc65 on 2013-12-11
With 4G RAM I would set swappiness to 10 or less.

---

### Post by jan-goebel-g on 2013-12-11
Im using a swap partition of course, i set up the partitins myself so thats not the issue, thx.

Ill try setting it to 10, ill report back tomorrow if it helps.

Anybody there with some experience using ram as cache/swap in recent ubuntu?

---

### Post by leclerc65 on 2013-12-12
You can put Firefox cache to RAM by setting (about:config)

browser.cache.disk.enable 	   false 
browser.cache.memory.enable   true 
browser.cache.memory.capacity -1
  (-1 = adjust to whatever it deems appropriate, or use a value depending your system RAM)

Fore Chrome use Google.

---

### Post by jan-goebel-g on 2013-12-14
ALright swapping to 10made it better but as soon as it swaps (happened once in a couple of days) i get the same problem again while a process is writing the disk and the swap is trying to use the disk too.

I bought another 4gb of ram, gonna put zram or something like that to ram and solve it like that, 30bucks well spent id say:D

@leclerc:thx for this, im not using firefox though but i guess if i needed i could do the same with chrome too. good point that could help me later on!

---

### Post by tgalati4 on 2013-12-15
You problem sounds like you are running 32-bit linux.  I presume you are running 64-bit version to access up to 4 GB.  It might be time to upgrade to an SSD if you feel your hard disk is too slow compared to the rest of the system.

---

### Post by jan-goebel-g on 2013-12-24
> **tgalati4 said:**
> You problem sounds like you are running 32-bit linux.  I presume you are running 64-bit version to access up to 4 GB.  It might be time to upgrade to an SSD if you feel your hard disk is too slow compared to the rest of the system.
Im running 64bit, the intel gpu takes some away but thats okay.

Im posting my solution:
-Upgrade to 8gb of ram. Godlike.
-Stripping my desktop pc of his ssd (64gb).

Im fine now, the ssd is nice but the main benefit was adding the ram so it doesnt swap anymore, swapping=bad:D.

Im fine now, everything is running quickjly so i could just launch the laptop in between christmas dinner while everybody went smoking.

---

