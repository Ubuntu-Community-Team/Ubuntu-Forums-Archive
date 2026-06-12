---
title: "Is there a way to give my boot folder more room?"
date: 2013-05-02
forum: General Help
---

### Post by hiddeninfluence on 2013-05-02
I have just upgraded to Ubuntu 13.04 and upon start up, there is an error message that reads "the boot volume has 0 bytes disk space remaining" it then says I can free up disk space by removing unused programs or files, or by moving files to another partition. Which files can I remove/ move to free up some space? or how to I give The boot folder more space?

---

### Post by oldos2er on 2013-05-02
Can you post the output from ```
df -h
```
There are tips [here]("http://ubuntuforums.org/showthread.php?t=1122670") on freeing up disk space.

---

### Post by hiddeninfluence on 2013-05-02
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu-root   55G   18G   34G  35% /
none                     4.0K     0  4.0K   0% /sys/fs/cgroup
udev                     1.9G  4.0K  1.9G   1% /dev
tmpfs                    393M  960K  392M   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     2.0G  756K  2.0G   1% /run/shm
none                     100M   40K  100M   1% /run/user
/dev/sdb2                229M  225M     0 100% /boot
/dev/sdb1                190M  126K  190M   1% /boot/efi
/home/adam/.Private       55G   18G   34G  35% /home/adam
/dev/sdc1                932G  547G  385G  59% /media/adam/My Passport

---

### Post by ibjsb4 on 2013-05-02
You can remove the old kernels from Boot.  There are many ways to do that.  I use Synaptic, but I understand Ubuntu-Tweak makes it real simple to do.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+old+kernels&sa=Search&cof=FORID:9)

---

### Post by hiddeninfluence on 2013-05-02
thank you very much this has helped and worked and fixed all my other problems as well :)

---

### Post by ibjsb4 on 2013-05-02
Don't forget

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And welcome to the forums :)

---

