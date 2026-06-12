---
title: "Out of disk space (not)"
date: 2013-04-28
forum: General Help
---

### Post by FalcMcFakeJr on 2013-04-28
Hi, I am running Ubuntu 12.04 LTS 64 bit, my problem is that anything I do will give me an error of that there is not enough disk space left. Disk usage analyzer tells me that I have used 61,8 GB and I have 201,7 GB left. I am willing to run any commands or give any information, I also have Windows 7 Home Premium without internet connection on the same computer.

---

### Post by Bashing-om on 2013-04-28
FalcMcFakeJr; Hi ! Welcome to the forum .

Well, that error is generally indicative that a partition is full (rather than the whole disk).
To have a looksee as to what is transpiring; terminal commands:
```
du -h
du -h --max-depth=1 | sort -hr
```

Post those outputs - between code tags for readability - and we will see what can/should be removed to regain disk space.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by Mopar1973Man on 2013-04-28
Another way to see it is using Gparted. Which is typically not installed.

To install gparted
```
sudo apt-get install gparted
```

When you run it you'll get a graphical view of the partitions.

[ATTACH=CONFIG]241928[/ATTACH]

---

### Post by FalcMcFakeJr on 2013-04-29
Thanks Mopar1973man, but the problem is that I can not download anything because of that it says that there is not enough space left.
Thanks anyways.

---

### Post by FalcMcFakeJr on 2013-04-29
This is what the command with --max-depth=1 gives me.
```

du: tiedostoa ”./proc/2582/task/2582/fdinfo/4” ei voi käsitellä: Tiedostoa tai hakemistoa ei ole
du: tiedostoa ”./proc/2582/fd/4” ei voi käsitellä: Tiedostoa tai hakemistoa ei ole
du: tiedostoa ”./proc/2582/fdinfo/4” ei voi käsitellä: Tiedostoa tai hakemistoa ei ole
36G    .
22G    ./home
7,2G    ./host
3,1G    ./usr
2,9G    ./root
522M    ./var
509M    ./lib
88M    ./boot
9,5M    ./etc
8,7M    ./bin
8,6M    ./sbin
1,1M    ./run
25K    ./tmp
12K    ./lost+found
4,0K    ./dev
2,0K    ./media
1,0K    ./srv
1,0K    ./selinux
1,0K    ./opt
1,0K    ./mnt
1,0K    ./lib64
0    ./sys
0    ./proc

```

---

### Post by Impavidus on 2013-04-29
The presence of a /host directory indicates this is a wubi install (installed using a windows installer instead of booting from a dvd or usb drive). Is that correct? If so, then read on.

Wubi installs can be at most 30GB, even if the host partition is larger. Your root partition may be full and your /host directory contains the 30GB root.disk file, which is where your root partition is stored, and the swap file. This accounts for the 61GB total usage.

There is some space left in your /host directory, where you can move some of your data. You may also use other windows partitions. In all cases, be careful as writing to the windows C partition sometimes causes system corruption, rendering Windows and, because this is wubi, Ubuntu unbootable. Alternatively, you may consider to do a full install. This will give you a partition as large as you want, in addition to making Ubuntu totally independent of Windows, decreasing the risk of system corruption.

---

### Post by FalcMcFakeJr on 2013-04-29
So, the problem is that the partition is too small and I need to install it through a cd?
But even if I delete 5 MB of memory,  I cant download a 1 KB file.

---

### Post by bcbc on 2013-04-29
What's the output of ```
df -h
```

---

### Post by bcbc on 2013-04-29
Here's a guide on how to check if it's a wubi install, and (even if not) free up some space: [http://askubuntu.com/questions/107470/how-can-i-check-how-much-space-there-is-left-on-wubi-versus-how-much-space-it-ta]("http://askubuntu.com/q/107470/14916")

---

### Post by FalcMcFakeJr on 2013-05-09
It works after installing from CD.
Thanks!

---

