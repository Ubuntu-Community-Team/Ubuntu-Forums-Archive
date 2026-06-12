---
title: "Linux: Does it have a defrag/scandisk like windows?"
date: 2007-12-05
forum: General Help
---

### Post by immolat3 on 2007-12-05
So, let me give a little background. I'm a long time troller of Ubuntu and Linux and finally two weeks ago made the switch to running Ubuntu on my Desktop AND Laptop, aside from using VirtualBox for a few apps i need for school/work, i haven't looked back at Windows since! I'm loving every bit of Linux. However, I have had a few lock ups where I had to Control+Alt+F1 into terminal mode and sudo reboot that way. So I was wondering if there was some sort of integrity disk scanner that I could use to make sure everything is running alright//files aren't corrupt, much like Scan Disk or Disk Defrag in windows...or are these tools not even necessary?

Some system specs, incase it matters:

Ubuntu 7.10 64-Bit
2.4ghz AMD Athlon 64-Bit
2GB DDRam
NVidia Geforce 8600GS
250GB IDE HD (500GB SATA coming soon!)


Also, how is Linux in recognizing SATA hard drives as slave drives? I'm getting a 500gb for Christmas and i'm not sure if ill get SATA or IDE, Im assuming it detects it and lets me partition it through Gnome Partition Manager which I installed through Synaptic? 

ANyhow, thanks! :guitar:

---

### Post by -grubby on 2007-12-05
fdisk

---

### Post by bodhi.zazen on 2007-12-05
No, not like windows

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

	[http://www.itworld.com/Comp/3380/nls_unixfrag040929/index.html](http://www.itworld.com/Comp/3380/nls_unixfrag040929/index.html)

	[http://www.linuxquestions.org/questions/showthread.php?t=55710](http://www.linuxquestions.org/questions/showthread.php?t=55710)

My guess is you have a hardware problem.

---

### Post by immolat3 on 2007-12-05
no no, when my computer locked up i was messing around with stuff i knew could definitly cause a crash. i was just merely wondering IF there was such a thing for linux.

---

### Post by bodhi.zazen on 2007-12-05
Lol !

---

### Post by HermanAB on 2007-12-05
Fsck is what you are looking for.

If you are running ext3, then it will be scheduled to run every couple of months.  It is very fast so you won't even notice.

Cheers,

Herman

---

### Post by ryanVickers on 2007-12-05
> **immolat3 said:**
> no no, when my computer locked up i was messing around with stuff i knew could definitly cause a crash. i was just merely wondering IF there was such a thing for linux.

someone totally needs to invent a absolutely crash proof (except for hardware failures or incompatibilities) OS :p

it could like reserve at least 5% of CPU and RAM at all times, and ... lol

---

### Post by atlfalcons866 on 2007-12-06
ext3 by default fsck its self after 30 mounts. you can change it by 
> sudo tune2fs -c 100 /dev/sda1

you change to the 100 to whatever amount of mounts you want. i do 150 and it is fine.

as for defragging you dont need to. the highest amount of fragmentation i had was 4.4%.

---

### Post by ryanVickers on 2007-12-06
yeah, and my record was 2.6 or something :p

---

### Post by atlfalcons866 on 2007-12-06
i tryed out vista on my computer. it wiped ubuntu because i told it not too typical of windows to do that. on my 160Gb harddrive it was already 18% fragmented after the vista install. largest extent of free space was 4.5GB. shows how bad ntfs is at allocating space.

---

### Post by atlfalcons866 on 2007-12-06
i have since dumped windoze vista for good. i have no plans to leave Kubuntu XD

---

