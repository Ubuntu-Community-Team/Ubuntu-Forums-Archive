---
title: "Missing 14gb of Ram in a 64bit installation"
date: 2014-03-16
forum: General Help
---

### Post by reed-hummel on 2014-03-16
Hey guys, maybe you can help me.

I recently installed Saucy on an old windows 7 computer, and it runs pretty smoothly at the moment. 
However, I was having some problems with memory, and so I looked at the system monitor, and it only shows two gigabytes of ram. I'll post the output of free

```
henderson@shuttle:~$  free -h | awk 'NR>0{arr[$2]}END{for(i in arr) print i}' | grep G
2.0G

```


I ran lshw, and it returned the 16 gb I have installed:

```
henderson@shuttle:~$ sudo lshw -class memory | grep GiB -m 1 
[sudo] password for henderson: 
       size: 16GiB


```
Any suggestions as to how I can get the other 14gb to show up and be used?

Thanks

-R

---

### Post by sanderj on 2014-03-16
You can run my script to analyse what is going with your RAM:

```
wget https://dl.dropboxusercontent.com/u/1222680/check-my-memory.py
python check-my-memory.py
```

That will give you the first analysis.

If you trust my script, run it as root:

```
sudo python check-my-memory.py
```

Post the output here. Here's mine:

```
sander@flappie64:~$ sudo python check-my-memory.py 
check-my-memory.py - version: SJ 2013-02-22
OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 1 memory module(s)
BIOS offers 4028 MB as usable
Memory seen by OS 3887 MB
BIOS version 05/22/2013
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit

SUMMARY:
Memory difference between DIMM hardware and BIOS offering 68 MB
Memory difference between BIOS offering and memory seen by OS 141 MB
Memory difference between DIMM hardware and memory seen by OS 209 MB

ADVICE:
Nothing unusual found, so no advice for your setup

Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 4GiB
          description: DIMM [empty]
          description: SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
          size: 4GiB

Finished
sander@flappie64:~$ 
```

---

### Post by reed-hummel on 2014-03-16
Great, thanks for the info!
I ran your script as root, and it displayed something about the bios not offering all of my memory. I'll post the output.
```
henderson@shuttle:~$ sudo python check-my-memory.py
[sudo] password for henderson:
check-my-memory.py - version: SJ 2013-02-22
OK, you're root
ANALYSIS:
Total of physical memory modules found 16384 MB in 2 memory module(s)
BIOS offers 2046 MB as usable
Memory seen by OS 2002 MB
BIOS version 12/01/2005
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit


SUMMARY:
Memory difference between DIMM hardware and BIOS offering 14338 MB
Memory difference between BIOS offering and memory seen by OS 44 MB
Memory difference between DIMM hardware and memory seen by OS 14382 MB


ADVICE:
Your BIOS is not offering all of your physical memory. Try to update your BIOS, and/or enable 'memory hole remapping / hoisting' in your BIOS to get more usable memory


Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 16GiB
          description: DIMM
          size: 8GiB
          description: DIMM
          size: 8GiB


Finished

```So, should I look into updating my BIOS now? And what is memory hole remapping/hoisting, and does that make more sense?
Thanks a ton!

---

### Post by sanderj on 2014-03-16
Wow: you have a BIOS from 2005? Can that be correct? In other words: is the system / motherboard 9 years old?
Can you find a BIOS update?
And: check the make/brand of the mobo and then what amount of RAM it can handle; 16GB was unusual in 2005. 

Ignore the memory hole remapping/hoisting for now; it would only be relevant if you would get 3 or 3.2 GB, not with your current 2 GB  RAM

EDIT:

What is your output for:

```
$ sudo dmidecode | grep -i "Maximum Capacity"
	Maximum Capacity: 8 GB
```

And:

```
$ sudo dmidecode | grep -i -A3 -e "bios information" -e "system information"
BIOS Information
	Vendor: Hewlett-Packard
	Version: 68SRR Ver. F.41
	Release Date: 05/22/2013
--
System Information
	Manufacturer: Hewlett-Packard
	Product Name: HP ProBook 4530s
	Version: A0001D02
```

---

### Post by reed-hummel on 2014-03-16
Well, I guess my BIOS *could* be from 2005. We really haven't used this computer in a long time. Windows 7 couldn't support the sound card, so we packed it up, and I just recently pulled it out and put 13.10 on it. 
Output for your first command is this:
```
sudo dmidecode | grep -i "Maximum Capacity"
[sudo] password for henderson: 
    Maximum Capacity: 4 GB

```

Here's the second command:
```
sudo dmidecode | grep -i -A3 -e "bios information" -e "system information"
BIOS Information
    Vendor: Phoenix Technologies, LTD
    Version: 6.00 PG
    Release Date: 12/01/2005
--
System Information
    Manufacturer: Shuttle Inc
    Product Name: SK21V10
    Version: 
``` 
It looks like I should find out how to update my BIOS, right?

---

### Post by sanderj on 2014-03-16
Yes, try to find a BIOS upgrade, hopefully on the Shuttle website (as it was sold as a system, not a bare motherboard)

---

### Post by reed-hummel on 2014-03-16
Well, it looks like I can't find my model on the Shuttle website, likely as it is too old. I really appreciate your help though. I am going to mark the thread as solved now, because if I'd been able to find the BIOS, I would have fixed the problem.
Thanks a lot!
-R

---

### Post by sanderj on 2014-03-16
Could you try this: remove one memory module, and see what amount of memory you get reported: 2GB, 1GB, or something else?

And are you able to find one module of 4GB, or two modules of 2GB, and try that out?

---

### Post by reed-hummel on 2014-03-17
I'll see what I can do. I don't think I have a 4GB module, or even two 2GB, so I will see about what I can do as to removing one module. It may
be a while though, so don't wait up. Thanks for the help, again!
-R

---

