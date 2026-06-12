---
title: "Processes in Ubuntu 14.04 hangs after running for about a week"
date: 2015-12-02
forum: General Help
---

### Post by anpartha on 2015-12-02
[COLOR=#111111][FONT=Ubuntu]We are running Ubuntu 14.04 (with Linux kernel 3.13.0-29) VM on an openstack RHEL 7 nova host with KVM and we notice that sometimes a number of processes are hanging after a few days. Left for a long time in this state, even SSH to the VM fails. We upgraded to Linux 3.19.0-33 kernel image and we see the same issue. We have one instance where we are able to SSH into the instance and noticed that a number of processes are hanging likely in disk I/O. Troubleshooting commands such as top, vmstat etc are hanging but dmesg works. We collected /proc/diskstatswhich is as follows:[/FONT][/COLOR]
root@Avi-Controller:/home/admin# cat /proc/diskstats  
   1 0 ram0 0 0 0 0 0 0 0 0 0 0 0  
   1 1 ram1 0 0 0 0 0 0 0 0 0 0 0  
   1 2 ram2 0 0 0 0 0 0 0 0 0 0 0  
   1 3 ram3 0 0 0 0 0 0 0 0 0 0 0  
   1 4 ram4 0 0 0 0 0 0 0 0 0 0 0  
   1 5 ram5 0 0 0 0 0 0 0 0 0 0 0  
   1 6 ram6 0 0 0 0 0 0 0 0 0 0 0  
   1 7 ram7 0 0 0 0 0 0 0 0 0 0 0  
   1 8 ram8 0 0 0 0 0 0 0 0 0 0 0  
   1 9 ram9 0 0 0 0 0 0 0 0 0 0 0  
   1 10 ram10 0 0 0 0 0 0 0 0 0 0 0  
   1 11 ram11 0 0 0 0 0 0 0 0 0 0 0  
   1 12 ram12 0 0 0 0 0 0 0 0 0 0 0  
   1 13 ram13 0 0 0 0 0 0 0 0 0 0 0  
   1 14 ram14 0 0 0 0 0 0 0 0 0 0 0  
   1 15 ram15 0 0 0 0 0 0 0 0 0 0 0  
   7 0 loop0 0 0 0 0 0 0 0 0 0 0 0  
   7 1 loop1 0 0 0 0 0 0 0 0 0 0 0  
   7 2 loop2 0 0 0 0 0 0 0 0 0 0 0  
   7 3 loop3 0 0 0 0 0 0 0 0 0 0 0  
   7 4 loop4 0 0 0 0 0 0 0 0 0 0 0  
   7 5 loop5 0 0 0 0 0 0 0 0 0 0 0  
   7 6 loop6 0 0 0 0 0 0 0 0 0 0 0  
   7 7 loop7 0 0 0 0 0 0 0 0 0 0 0  
253 0 vda 22268 0 1467482 8840 3305379 153869 50854080 3201712 128 113003472 3146293200  
253 1 vda1 906 0 7248 288 0 0 0 0 0 288 288  
253 2 vda2 702 0 5616 148 0 0 0 0 0 148 148  
253 3 vda3 20628 0 1454314 8396 2934939 153869 50854080 3134592 128 112937796  3146225736  
253 16 vdb 2094 0 29738 556 0 0 0 0 0 548 556  
[COLOR=#111111][FONT=Ubuntu]It seems like the number of in-flight requests to the disk is 128. This is running on a SSD disk. Have any of you seen a similar issue? Is there a kernel or driver issue that you can refer us to?[/FONT][/COLOR]

---

### Post by TheFu on 2015-12-04
I've only seen something similar with USB2/3 disks on certain host machines. USB has queuing issues, sometimes.
If the hostOS is short of RAM, i.e., VMs are overcommitted, that could be part of the issue too.

But I honestly don't have a clue about your specific situation. Sorry.  Is normal system monitoring setup that provides a complete picture of the host and all the guests running on that machine?  That's where I'd start. We use Munin, but nagios, cacti, SysUsage, etc.... can be used too.

---

