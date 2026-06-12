---
title: "[SOLVED] mystery CPU usage"
date: 2008-06-04
forum: General Help
---

### Post by themoebius on 2008-06-04
Once in a while my CPU just goes to hell and works at 100% for periods of 5-15 minutes, but the crazy thing is, when I open something like top or htop I can't tell whats using it because the processes are all very low usage. They just don't add up to even close to 100%, so what the hell is using it? Durring this time my hard drive is also going. That kind of makes me think its indexing, but a) I don't have any major indexing services running that I know of and b) even if I did why isn't it shown in the process list? I've even tried running top as root.

I've attached the screenshot below as proof.

---

### Post by Lord Xeb on 2008-06-04
Go into the system monitor and select View>All Processes. Hopefully this can shed some light up the problem

---

### Post by r3by on 2008-06-04
Maybe try another monitoring program? top, atop, etc.  There was a bug with gnome-system-monitor falsely reporting 100% cpu usage; maybe this is related.

- Bug report : [https://bugs.launchpad.net/ubuntu/+s...or/+bug/187383](https://bugs.launchpad.net/ubuntu/+s...or/+bug/187383) - fixed upstream and currently in -proposed (may 08th 2008)

---

### Post by sdennie on 2008-06-04
You should be able to tell what is using the disk with:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

Wait until the machine goes crazy and then try:

```

dmesg

```

After you figure out the problematic program, do the following to stop the disk usage dumping:

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

```

---

### Post by bingoUV on 2008-06-04
when htop's cpu bar is red, it means the kernel is taking up the CPU, not a particular process. Kernel generally does not do this for selfish reasons, but because processes ask it to do. Like reading or writing hard disk. In top, you will find CPU used for such purposes in the "wa" part of CPU usage.

Hope it is demystified now.

Install iotop from repositories to get an idea of which process uses how much IO.

---

### Post by themoebius on 2008-06-04
Ahh, that kinda makes sense. So I have to figure out what process is doing all that IO. I tried to install iotop, but its not found in the repos. It looks like I can download it as an rpm though.

---

### Post by bingoUV on 2008-06-04
Finally found a (non-redhat) program that is available in default Fedora repository but not in default Ubuntu.

---

