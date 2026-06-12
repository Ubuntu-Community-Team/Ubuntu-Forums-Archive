---
title: "Ubuntu Unresponsive"
date: 2007-11-01
forum: General Help
---

### Post by MadHADR on 2007-11-01
Hi all, 

I am a new user to Ubuntu and I am having a weird problem. I have this desktop PC that I have installed 7.04 on and it does nothing but act as an iSCSI server. All of a sudden for reasons unknown, it is very unresponsive. I have rebooted it several times and the same thing occurs. I have ran top but there is no out of control activity. I have even stopped the iSCSI service but the problem remains. This was acting fine a few days ago and I am at a loss. 

Here are some issues I am seeing.

dmesg takes about 3 minutes to complete
I ran cat /var/log/messages and it was still going after about 10 minutes
general commands are extremely slow, dh, ls, pwd etc

I am self sufficient but I just need some pointers in the right direction.

Thanks,

Paul

---

### Post by Pumalite on 2007-11-01
Check memory first, then power supply and then CPU

---

### Post by MadHADR on 2007-11-01
Thanks for the tip. I reseated the memory but not sure how to "check" the CPU and PS. I also wanted to post some of my output to make sure it looks normal.


top - 14:24:43 up 29 min,  1 user,  load average: 0.00, 0.00, 0.00
Tasks:  38 total,   2 running,  36 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    515972k total,   104184k used,   411788k free,     3748k buffers
Swap:  1277128k total,        0k used,  1277128k free,    83460k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                
    1 root      15   0  2912 1848  524 S  0.0  0.4   0:01.39 init                                                                   
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                            
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                            
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                             
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0                                                               
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper                                                                
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kthread                                                                
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0                                                              
   31 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                 
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                           
  100 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                
  123 root      18   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                
  124 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                                                
  125 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 kswapd0                                                                
  126 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                  
 1804 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                  
 1805 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                
 1810 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                          
 1811 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                  
 3066 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kjournald                                                              
 3230 root      21  -4  2292  620  376 S  0.0  0.1   0:00.53 udevd                                                                  
 4557 root      18   0  1652  512  440 S  0.0  0.1   0:00.00 getty                                                                  
 4558 root      18   0  1648  508  440 S  0.0  0.1   0:00.00 getty                                                                  
 4561 root      18   0  1652  512  440 S  0.0  0.1   0:00.00 getty                                                                  
 4562 root      18   0  1648  508  440 S  0.0  0.1   0:00.00 getty                                                                  
 4563 root      18   0  1648  508  440 S  0.0  0.1   0:00.00 getty                                                                  
 4564 root      18   0  1648  508  440 S  0.0  0.1   0:00.00 getty                                                                  
 4795 root      25   0  1860  776  656 S  0.0  0.2   0:00.00 acpid                                                                  
 4809 root      18   0  1704  648  536 S  0.0  0.1   0:00.03 syslogd                                                                
 4830 root      18   0  1792  524  432 S  0.0  0.1   0:00.03 dd                                                                     
 4832 klog      18   0  2428 1372  400 S  0.0  0.3   0:00.10 klogd                                                                  
 4859 root      18   0  5080  964  632 S  0.0  0.2   0:00.00 sshd                                                                   
 4882 daemon    25   0  1908  420  300 S  0.0  0.1   0:00.00 atd                                                                    
 4893 root      18   0  2284  788  632 S  0.0  0.2   0:00.00 cron                                                                   
 4915 root      16   0  7860 2336 1904 S  0.0  0.5   0:00.03 sshd                                                                   
 4917 iscsi     15   0  7996 1548 1072 R  0.0  0.3   0:00.06 sshd                                                                   
 4918 iscsi     15   0  5404 2960 1472 S  0.0  0.6   0:00.22 bash                                                                   
 4947 iscsi     15   0  2316 1116  884 R  0.0  0.2   0:00.00 top                


iscsi@hw-iscsi-target:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hde1              27G  732M   25G   3% /
varrun                252M   36K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M   76K  252M   1% /proc/bus/usb
udev                  252M   76K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-15-generic/volatile

/dev/hde1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)

---

### Post by Pumalite on 2007-11-01
For memory you know you can do memtest. For Power Supply, take it to a shop or just change it. For CPU, an IT for sure.

---

### Post by MadHADR on 2007-11-01
Well, memlock is extrenly slow as well but I cannot tell if it is the actual memory or it is just reacting to the overall slow down of the system in general.

---

### Post by MadHADR on 2007-11-01
Sorry, memtest.

---

### Post by Pumalite on 2007-11-01
memtest takes from 12 to 24 HRS. You have to allow 8 to 12 passes.

---

### Post by MadHADR on 2007-11-02
Well, I moved the box from the bedroom to the kitchen so I could troubleshoot a little easier and now it works fine again.

WTF

---

### Post by hikaricore on 2007-11-02
Refrigerator interference?  lol

More than likely something was loose and you jared it back in place during the move.
I've had this happen with memory on atleast one occasion when I was about to toss the whole box out a window.

---

