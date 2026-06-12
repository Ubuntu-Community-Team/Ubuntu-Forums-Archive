---
title: "LVM Swap Space"
date: 2021-05-02
forum: General Help
---

### Post by doubletop12 on 2021-05-02
Ubuntu 20.04 LTS - I've just moved my system disk from an 80Gb drive to 500Gb with DDRescue. Used Gparted to extend the partition to the full size of the disk and then lvresize to expand the two logical volumes

```
sudo lvs
  
  LV     VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  root   ubuntu-vg -wi-ao---- 448.80g                                                    
  swap_1 ubuntu-vg -wi-ao----  16.95g
```

  
  However after the resize of the swap LVM  and
  
```
sudo swapon /dev/mapper/ubuntu--vg-swap_1
```

and then

```
sudo swapon --show
NAME      TYPE      SIZE USED PRIO
/dev/dm-1 partition 976M 524K   -2
```


So what am I missing? Why is my active swap file showing to be /dev/dm-1 at 976M and not /dev/mapper/ubuntu--vg-swap_1 at 16.96G?

What is the relationship?

Pete

---

### Post by doubletop12 on 2021-05-02
OK fixed it myself thanks I missed the  step

```
eng-1:~$ free
              total        used        free      shared  buff/cache   available
Mem:        3901664     2207944      729236      436476      964484     1014128
Swap:        999420      785288      214132

eng-1:~$ cat /proc/swaps
Filename                Type        Size    Used    Priority
/dev/dm-1                               partition    999420    785288    -2

eng-1:~$ sudo swapoff /dev/mapper/ubuntu--vg-swap_1

eng-1:~$ free
              total        used        free      shared  buff/cache   available
Mem:        3901664     2837008      108856      555812      955800      267576
Swap:             0           0           0

**eng-1:~$ sudo mkswap /dev/mapper/ubuntu--vg-swap_1**
mkswap: /dev/mapper/ubuntu--vg-swap_1: warning: wiping old swap signature.
Setting up swapspace version 1, size = 17 GiB (18203275264 bytes)
no label, UUID=6c831739-623d-4923-9378-b1c8a45c10bf

eng-1:~$ sudo swapon -v /dev/mapper/ubuntu--vg-swap_1
swapon: /dev/mapper/ubuntu--vg-swap_1: found signature [pagesize=4096, signature=swap]
swapon: /dev/mapper/ubuntu--vg-swap_1: pagesize=4096, swapsize=18203279360, devsize=18203279360
swapon /dev/mapper/ubuntu--vg-swap_1

eng-1:~$ swapon --show
NAME      TYPE      SIZE USED PRIO
/dev/dm-1 partition  17G   0B   -2
```

OK 17Gb maybe a tad large for a swapfile but thats OK

Pete

---

### Post by TheFu on 2021-05-03
Over the years, I've found that 4.1G to be the only size for a swap file/partition necessary.

On servers, by RAM and know the workload so that no swap is ever needed.

On desktops, the point of swap changes based on the physical RAM. On systems with 4G or less RAM, a normal user with a modern browser can easily use over 4G of RAM, add in a few other programs and the OS, then getting to 6G used can happen.  Swap is there to make things slower so the user will "feel" that slowness, check the available memory and close programs until everything fits inside the physical RAM again.  Systems with 8, 16, 32, 64G of RAM can end up using swap and, again, it is about that "slow feeling" for the user to know when RAM use is tight. 

IF this question is solved, please use the THREAD TOOLS button to make it that way.  This helps people find a good answer+solution and prevents people looking to help from wasting time on already SOLVED questions.  Thanks.

---

