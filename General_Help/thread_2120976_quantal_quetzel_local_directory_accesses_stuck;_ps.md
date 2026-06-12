---
title: "quantal quetzel: local directory accesses stuck; ps reports WCHAN of rpc_wa STAT D+"
date: 2013-02-28
forum: General Help
---

### Post by ArlieS on 2013-02-28
Hi Folks,

This morning my system had apparantly done a spontaneous reboot. When I got it back up and logged in, I found that any attempt to list the files in a directory hung. This started with an attempt to load a VM in vmware player; it hung trying to list the available .vmx files. I then hung both ls and df. On the other hand, everything else I tried worked. This persisted for many minutes - long enough for me to do a lot of research. I'll call it 10 minutes, but that's conservative; it might have been half an hour.  

Then, as I was starting to compose this message, I found the problem had stopped. The only thing I did between when I know it was hung and when I know it was not hung that seems likely to have affected anything was hit "cancel" in the vmware player screen - but the fact that succeeded may mean the hang was already over.

Here's some excerpts from ps axlwww, during the hang. 

F   UID   PID  PPID PRI  NI    VSZ   RSS WCHAN  STAT TTY        TIME COMMAND
0  1000  4428  4369  20   0  24068   696 rpc_wa D+   pts/3      0:00 ls --color=auto -aF
0  1000  4591  4536  20   0  24068   696 rpc_wa D+   pts/5      0:00 ls --color=auto
0  1000  4731  4674  20   0  24068   692 rpc_wa D+   pts/6      0:00 ls --color=auto /
0  1000  4505  4442  20   0  11408   752 rpc_wa D+   pts/4      0:00 df -h

Here's uname -a:

Linux uastephens 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I couldn't remember how to do a sysrq on a system without a sysrq key, and the recovery occured while I was figuring that out - it looks to me like the lock and task states would have been very interesting to someone. 

Now that the hang is over, vmware player is finding my files, so I imagine it was a victim, not a contributor to the problem. ls and df are also working fine. 

I have not installed any updates in what's probably a couple of weeks now, after a painful and still incompletely unresolved experience with updates that broke X rather badly, which no one seems to have a clue how to address. (I found that falling back to the 3.5.0-17-generic kernel provides a workaround.) 

The machine is an nfs client. None of the file file systems being accessed were NFS mounts. There are no NFS mounts in my $PATH. dmesg includes a number of messages like:

[   23.148599] userif-2: sent link up event.<5>[  219.402313] nfs: server sfo1-nacl1-eng-2 not responding, still trying
[  238.320274] nfs: server mint not responding, still trying
[  269.637190] nfs: server mint not responding, still trying
[  339.256817] nfs: server mint not responding, still trying
[  372.761908] nfs: server sfo1-nacl1-eng-1.nbttech.com not responding, still trying
[  430.605220] nfs: server mint not responding, still trying
[  622.628658] nfs: server mint not responding, still trying
[  980.909707] nfs: server sfo1-nacl1-eng-2 OK
[  996.240947] nfs: server mint OK
[  996.240978] nfs: server mint OK
[  996.241024] nfs: server mint OK
[  996.242969] nfs: server mint OK
[ 1126.048414] nfs: server sfo1-nacl1-eng-1 OK

Here's /etc/fstab. Note the "intr"

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=e31cf0c1-2a37-466e-ab00-4ec416e435af /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d5d974eb-121f-4063-b1c7-31a7c1ef3a55 none            swap    sw              0       0
mint:/vol/prime/main /u    nfs    rw,bg,nfsvers=3,tcp,timeo=600,hard,intr,nobootwait    0    0
sfo1-nacl1-eng-2:/qa_bugs/exproot /mnt/qa-bugs nfs rw,bg,nfsvers=3,tcp,timeo=600,rsize=32768,wsize=32768,hard,intr,nobootwait 0 0
sfo1-nacl1-eng-2:/builds/exproot  /mnt/builds  nfs  rw,bg,nfsvers=3,tcp,timeo=600,rsize=32768,wsize=32768,hard,intr,nobootwait 0 0
sfo1-nacl1-eng-2:/qaresults/exproot             /mnt/qa-results        nfs     rw,bg,nfsvers=3,tcp,timeo=600,rsize=32768,wsize=32768,hard,intr,nobootwait 0 0
sfo1-nacl1-eng-1.nbttech.com:/vol/traces          /mnt/dev-traces           nfs    rw,bg,nfsvers=3,tcp,timeo=600,rsize=32768,wsize=32768,hard,intr,nobootwait 0 0
mothership:/support/exproot          /mnt/support           nfs     rw,bg,nfsvers=3,tcp,timeo=600,rsize=32768,wsize=32768,hard,intr,nobootwait 0 0

Messages and files lightly editted to remove domain names. 

IMHO, this smells like a kernel bug, probably involving a lock held that  should not have been. Given what I found in dmesg, it looks as if an  nfs-related hang spilled over into accesses to local file systems, probably due to the nfs client code holding an inappropriate lock.

---

### Post by rnerwein on 2013-02-28
hi
it's not a bug i think. i bet your nfs-server is gone or the network make the problem. the processes hang in io wait (D) in ps -ef and wait_chane in ps aux.
you can't kill them because they are kernel running in a non interuptable state and the nfs filesystem(s) are hard mounted. this is a must if you write to
the files. softlink should only be used when read-only mounted. if you even write to the files and if you use soft-mounting for nfs you can run in unexpected errors !
ciao

---

### Post by ArlieS on 2013-02-28
> **rnerwein said:**
> hi
it's not a bug i think. i bet your nfs-server is gone or the network make the problem. the processes hang in io wait (D) in ps -ef and wait_chane in ps aux.
you can't kill them because they are kernel running in a non interuptable state and the nfs filesystem(s) are hard mounted. this is a must if you write to
the files. softlink should only be used when read-only mounted. if you even write to the files and if you use soft-mounting for nfs you can run in unexpected errors !
ciao

That would be reasonable _if_ I were trying to access files or directories that were mounted over nfs. I'm used to that behaviour. 

But I was trying to access local files, except for the df example. I believe all the ls instances were in my home directory, and I'm not crazy enough to nfs mount that :-( 

Also amusingly - I was able to ssh to another linux system (not ubuntu) during my hang, which mounts some of the same filesystems. No hang there. But given network topology, it may well be 'closer' to the file servers than I am. And I'm not 100% sure I'd have done any ls or equivalent on that machine.

---

