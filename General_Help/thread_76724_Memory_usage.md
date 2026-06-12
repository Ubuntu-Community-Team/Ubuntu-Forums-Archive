---
title: "Memory usage?"
date: 2005-10-15
forum: General Help
---

### Post by karl.william on 2005-10-15
Hi, I'm an old Debian user, have been using Ubuntu before thou, both on this machine, and my fathers.. 

but, in debian, my memory usage were about 400-500mB, depending on what I did, If I played WoW thru Cedega, it was much higer. But now, just installed Breezy, it starts good, about 300mB usage, but after about an hour of usage, the memory is usage is about 1gB, and wont go down :S dossen't mather if I close the apps I have runnin' it stays up, and won't go down.

anyone ells having this problem? can it be a bug or something?

//William

---

### Post by aysiu on 2005-10-15
I haven't had that problem because I don't even have one GB of memory. I have 512 MB, and it never gets used up. What apps are you running? And what comes up when type ```
top
``` into a terminal?

---

### Post by karl.william on 2005-10-15
the apps I'm using the most is mozilla firefox, kopet, krusader and amaroK..

I'v was looking at top a while ago, as usual firefox takes about 90mB, but xorg takes about 200mB is that normal?  anyway I killd the kbluetoothd and the kmix processes, mainly becurse I don't use them, didn't think much about it, didn't look at top after it eather, then, I got a little bit AFK, and now when I got back, I ran top, and my memory usage were down to 400mB again :) I don't know if it can be connected with the who processes I killd before? 

//William

---

### Post by Delvien on 2005-11-06
[QUOTE=karl.william]the apps I'm using the most is mozilla firefox, kopet, krusader and amaroK..

I'v was looking at top a while ago, as usual firefox takes about 90mB, but xorg takes about 200mB is that normal?  anyway I killd the kbluetoothd and the kmix processes, mainly becurse I don't use them, didn't think much about it, didn't look at top after it eather, then, I got a little bit AFK, and now when I got back, I ran top, and my memory usage were down to 400mB again :) I don't know if it can be connected with the who processes I killd before? 

//William[/QUOTE]


I tooo have been having this problem , with my laptop with 512, Kubuntu starts at 246 mb, and after  about an hour it goes to 400-500 and stays there, MAJOR memory leakage issues with KDE. If it doesnt get fixed i might switch back to gnome  :(

---

### Post by GoldBuggie on 2005-11-07
Maybe I'm going out on alimb here but I was under the impression that linux likes memory. With this I mean that linux apps and other things likes to take advantage of every memory it can get so when it sees free memory it uses it for cache.

When I do top I get
```
Mem:    499872k total,   490872k used,     9000k free,    57576k buffers
```
But when I go into KInfoCenter and look at Memory I see that almost halv of that used memory is cache. That isn't a bad thing is it? Linux likes to use your memory.

Anybody please correct me and add to this info if they can say more.

---

### Post by dtfinch on 2005-11-07
Cache memory is almost as good as free. Really free memory is just when it doesn't have anything to cache. It'll keep a little bit of really free memory that it can give to processes immediately and convert cache to free as needed, or swap stuff out if it thinks it's given away too much cache. Sometimes swapping out used space in favor of cache is good, but not always. Just how much it does this can be controlled by messing with the setting called swappiness. Running "echo 10 > /proc/sys/vm/swappiness" as root would lower swappiness to 10, so less would be swapped in favor of cache. The default swappiness is 60. The high default helps to maintain good performance if you really don't have much ram, but it can be more of a burden if you have lots. To make it permanent, I think you just add "vm.swappiness = 10" to /etc/sysctl.conf.

If your system is not running slowly, then there's probably no reason to mess with swappiness. It's normal for nearly all unused memory to turn into cache over time.

---

### Post by Cufishing on 2005-11-07
I also noticed that after a while, the 'Disk Cache' runs pretty high. I had almost 86% usage, with 60% hogged by DC. Is this normal? I did a quick 'ctrl-alt-backspace' and everything went back to normal.

As I watched, the disk cache built up, at about 32K a second, and the free mem was dropping at about the same rate.

---

### Post by dtfinch on 2005-11-07
Maybe if the slocate/updatedb cron job was running, that might cause cache to gradually rise and make the system feel somewhat sluggish for a while. I normally disable the job except on systems that I leave running overnight.

---

### Post by ankush_jhalani on 2005-11-17
I understand tht linux likes free memory for caching, but my doubts are;
1) whts it caching, when im not running any applications and the ram usage is still 400MB plus
2) My pc is starting to lag in applications. 
Someone help.

---

### Post by shakin on 2005-11-17
From the command line run 'free'. Does it show any swap file usage? If not, don't worry about it because everything is fine. If you are using swap then you'll need to figure out which app is leaking by running your computer from a clean boot with each of your main apps running one at a time for an hour or so.

It's not necessarily bad to have some swap file usage, but you don't want much, especially when there is still some free RAM.

---

### Post by tonysathre on 2005-11-17
i have had the same problem once and a while, what i did was just do a ctrl-esc and end the process, not sure why just closing the program didnt kill the process but it seemed to work

---

