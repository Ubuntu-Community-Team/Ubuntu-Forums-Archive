---
title: "SATA problems, keep disconnecting"
date: 2007-11-08
forum: General Help
---

### Post by Green_Star on 2007-11-08
Hi,

I have two drives first drive where OS installed is old style too many pins hard drive(I guess it is PATA) and second drive is  new SATA drive which is used for media like mythtv etc. SATA is keep disconnecting/not responding randomly (my Ubuntu box 7.10 file manager window, the folder where I mounted showing either locked or empty with some error message). I do not know where to look for the problem. the only thing I can do in this situation is rebooting. 

Can some one guide me where do i need to see the the problem logs or what kind of commands i need to issue to reconnect without rebooting. And is there any way I can put a background process when ever that drive is disconnected or not responding it should popup a message.

Thanks in advance.

Edit:
I have 500W power supply, I also observed that when ever I use mythtv, my SATA is not responding after playing any recorded show a while. And when ever i run Mythtv, my CPU usage is around 100%, as of my observation  live show is fine, but didnt tested much. (I am guessing CPU is 100% because of my display drivers, I was failed many times to setup newly released ati drivers for my Radeon X1300 ). please see below link.
[https://lists.ubuntu.com/archives/kernel-bugs/2007-February/025111.html](https://lists.ubuntu.com/archives/kernel-bugs/2007-February/025111.html)

Is anyway disconnecting my one of the fan help me solving this problem?

---

### Post by atlfalcons866 on 2007-11-08
whats the sata chip model or motherboard?

---

### Post by Green_Star on 2007-11-08
I have following mother board.
GIGABYTE GA-K8N Pro-SLI 939 NVIDIA nForce4 SLI ATX AMD Motherboard with 1394b

---

### Post by atlfalcons866 on 2007-11-08
maybe its because you are mixing sata and ata at the same time.

---

### Post by Shazaam on 2007-11-08
> **atlfalcons866 said:**
> maybe its because you are mixing sata and ata at the same time.

Doesn't matter. I run XP on a PATA and Linux on a SATA (dual boot) with no problems.

---

### Post by Green_Star on 2007-11-09
> **atlfalcons866 said:**
> maybe its because you are mixing sata and ata at the same time.

Hmm....

If that is true, then Ubuntu needs to fix this asap, but I strongly believe that shouldn't be happen.

Any way I successfully installed new ATI drivers, now it is taking less CPU when I run videos or mythtv, yesterday no drive freezing, I haven't ran much time, I will keep testing and let you know if that happens again. I guess it is because of not having enough power to run drive when CPU using much power. hmmm....

---

### Post by Green_Star on 2007-11-12
Nope,

I guess it is not a high CPU usage issue, or not enough power to run SATA. It was disconnected again yesterday, I believe it was happened when Mythtv recording something into that disk. Can some one tell me where to see the error logs to know what exactly the problem? And also can some one tell me how to made the SATA to work again without reboot?

---

### Post by Green_Star on 2007-11-12
Do you guys think I need to open a bug in launchpad?

---

### Post by Green_Star on 2007-11-12
I guess this is kernal problem.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603)


..

---

