---
title: "Computer crashes"
date: 2016-12-21
forum: General Help
---

### Post by richprim on 2016-12-21
I am having a problem with a HP pavilion computer.
Intermittently it will just freeze up.
When restarted it says cleaning orphaned inode, might have missed the correct spelling on what is being cleaned.
Ubuntu 16.10 OS

Rich Prim

---

### Post by oldos2er on 2016-12-21
Moved to General Help.

Can you please post the computer's hardware specs? Is this a recent problem? Fresh installation of Ubuntu, or otherwise? Need more info to diagnose the problem.

---

### Post by richprim on 2016-12-21
Its a Intel core, 2 duo , CPU E6750 2.66 Ghz * 2   Ram memory is 7.8 gig.
I have run the mem test from a gparted live disk with no errors.
I have had intermittent problems in the past, after versioin 16.04 came out.
16.10 was a online upgrade.
Hope this is what you need.
Thank you Rich Prim

---

### Post by oldos2er on 2016-12-21
The "clearing orphaned inode" message can have different causes, at least from what I can find. Is this a laptop or desktop? If laptop are you using hibernation? How are you shutting down the computer?

---

### Post by ajgreeny on 2016-12-21
It may be worth seeing the output of commands ```
df -h
``` and then ```
df -hi
``` to see if you are running out of inodes on your disk.

Do you have lots of kernels on your system which may also have header packages still installed?  Header packages use a huge number of inodes.
Let's see the output of ```
ls /boot | grep vmlinuz
```

---

### Post by richprim on 2016-12-21
Its a desktop and I did notice it happened after the computer was idle a while.
It has also happened in the middle of working I think I was on AOL and it froze in the middle of scrolling down a email.
Rich Prim

---

### Post by richprim on 2016-12-21
```
rich@rich-KC787AAR-ABA-d4996t:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           799M  9.4M  790M   2% /run
/dev/sda1       1.8T  908G  832G  53% /
tmpfs           3.9G  412K  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
tmpfs           799M   56K  799M   1% /run/user/1000
rich@rich-KC787AAR-ABA-d4996t:~$ df -hi
Filesystem     Inodes IUsed IFree IUse% Mounted on
udev             993K   549  993K    1% /dev
tmpfs            998K   734  998K    1% /run
/dev/sda1        117M  636K  116M    1% /
tmpfs            998K     9  998K    1% /dev/shm
tmpfs            998K     5  998K    1% /run/lock
tmpfs            998K    16  998K    1% /sys/fs/cgroup
tmpfs            998K    30  998K    1% /run/user/1000
rich@rich-KC787AAR-ABA-d4996t:~$ 
```
Here it is

---

### Post by richprim on 2016-12-21
I got no response from ls /boot | grep vmlinux
rich@rich-KC787AAR-ABA-d4996t:~$ ls /boot | grep vmlinux
rich@rich-KC787AAR-ABA-d4996t:~$ ls /boot | grep vmlinux
rich@rich-KC787AAR-ABA-d4996t:~$ 
Rich

---

### Post by ajgreeny on 2016-12-21
> **richprim said:**
> I got no response from ls /boot | grep vmlinux
rich@rich-KC787AAR-ABA-d4996t:~$ ls /boot | grep vmlinux
rich@rich-KC787AAR-ABA-d4996t:~$ ls /boot | grep vmlinux
rich@rich-KC787AAR-ABA-d4996t:~$ 
Rich
It should have been **ls /boot | grep vmlinu[COLOR="#FF0000"]z**[/COLOR], not **ls /boot | grep vmlinu[COLOR="#FF0000"]x[/COLOR]**
Try again.

However, I don't think it's going to help us as you do not have any problem with inodes filling any partition.

---

### Post by richprim on 2016-12-21
rich@rich-KC787AAR-ABA-d4996t:~$ ls /boot | grep vmlinuz
vmlinuz-4.4.0-45-generic
vmlinuz-4.4.0-47-generic
vmlinuz-4.4.0-51-generic
vmlinuz-4.4.0-53-generic
vmlinuz-4.4.0-57-generic
rich@rich-KC787AAR-ABA-d4996t:~$

---

### Post by richprim on 2016-12-21
About an hour ago I got a OS update, I installed it.
Rich Prim

---

### Post by richprim on 2016-12-21
About an hour ago I did a OS update.

Rich

---

### Post by richprim on 2016-12-22
Yesterday I did get and installed a Operating system update, will report if that helped.

Rich Prim

---

### Post by ajgreeny on 2016-12-22
What exactly do you mean by "Operating system update"?

---

### Post by richprim on 2016-12-28
After the last OS update I don't seem to have the problem of the computer freezing up.

I did have a freeze in Chrome Web Browser but that could be a Chrome problem.

Rich Prim

---

### Post by ajgreeny on 2016-12-29
Great! Please mark as SOLVED from the Thread Tools menu up-top if this problem really is now solved to your satisfaction. It is a great help to users searching the forum.

---

