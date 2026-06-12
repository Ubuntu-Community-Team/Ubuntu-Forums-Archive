---
title: "boot hanging"
date: 2012-12-23
forum: General Help
---

### Post by Shrawn on 2012-12-23
Each time it hangs at a different point. Here are a few example outputs.

```
Starting CPU interrupts balancing daemon
Stopping Mount filesystems on boot
...
Stopping save kernel messages
...
Starting configure network device
``````
Stopping save kernel messages
Stopping enable remaining boot-time encrypted block devices
Stopping Mount filesystem on boot
...
Checking battery state...
``````
...
Starting KVM [fail]
...
mountall: Plymouth command failed
mountall: Disconnected from Plymouth
```I've had this install for over a year before this occurred. The only thing I can think of that I've done recently is mount two partitions (windows partitions and a storage partition that I was using with windows). I also moved a folder from the windows partition to /home/user/. No idea if that's a bad? The text for that folder was highlighted when I ran ls in /home/user.

NOTE: I can still boot into Windows 7

So far I've tried a few things after googling around: 

[LIST]
[*]turning off and unplugging for 10 minutes.
[*]leaving it for up to 15 minutes to see if it would get through the hang
[*]getting rid of "quiet splash" in grub
[*]trying everything in recovery mode. I have access to root there so I'm hoping I can make whatever changes are necessary there. I couldn't however unmount the other partitions or delete the folder that I moved accross to /home.
[/LIST]
I don't know if this is relevant but when I ran df -h in the recovery shell i got;

/dev/sda5 <correct data>
udev <correct data>
tmpfs <correct data>
df: '/run/lock': no such file or directory
df: '/run/shm'" no such file or directory

Whats going on there?

Any help would be great and if you need anymore specific details relating to the problem please ask.

---

