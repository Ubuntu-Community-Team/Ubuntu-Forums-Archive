---
title: "Unkillable mount"
date: 2014-02-07
forum: General Help
---

### Post by Gonzalo_de_la_Vega on 2014-02-07
Hi,
about two hours ago I tried to mount a USB disk in a Dell tower server to make a backup. The mount command never mounted the disk, couldn't be interrupted with Ctrl+C and now I can't kill it either with kill. It is just hanging there consuming as much CPU as possible (I could "renice" it to 19) but it won't respond to any signal. The parent process is no longer running and the disk is no longer plugged in. Is there any way to kill it without rebooting?

dmesg shows this message along with a "call trace":
[5123399.109795] INFO: task khubd:48 blocked for more than 120 seconds.

Any help would be appreciated.

---

### Post by deadflowr on 2014-02-07
Edit: Deleted entry.
I now realize this has nothing to do with mount and is a simple hardware problem.
The posts below this will help figure out the solution of killing children and grandchildren processes.
Good Luck.

---

### Post by Bashing-om on 2014-02-07
Gonzalo_de_la_Vega; Well,

Tough to do anything now that the usb drive has been removed. But, we can try:
What results ?
Package manager got a lock ?
```

sudo fuser -vki /var/lib/dpkg/lock
sudo rm -f /var/lib/dpkg/lock
##Do not think this will help, but won't hurt to see##
sudo fuser -cuk /var/cache/apt/archives/lock
sudo rm -f /var/cache/apt/archives/lock

```
##Maybe see if the system still sees the drive as connected ?##
 You can use these  commands to find out which process was keeping the device busy: and perhaps un-mount it.
```

fuser -m /dev/sdb1 ##assumes "sdb1" as the usb device identifier
    /dev/sdb1: 538 ##example return##
ps auxw|grep 538
kill -9 538
umount /dev/sdb1

```
Worth a try, but, just do not know.


There are those things that seem right
[INDENT][INDENT]but can lead to disaster
[/INDENT][/INDENT]

---

### Post by bc.haynes on 2014-02-07
What does the -9 do in the kill command?

---

### Post by Iowan on 2014-02-07
TMI, but here is a list (from **man kill**) of signals that can be used with the command.> DESCRIPTION
       The  default  signal  for  kill is TERM. Use -l or -L to list available
       signals.  Particularly useful signals include  HUP,  INT,  KILL,  STOP,
       CONT,  and  0.   Alternate  signals  may be specified in three ways: -9
       -SIGKILL -KILL.  Negative PID  values  may  be  used  to  choose  whole
       process  groups;  see the PGID column in ps command output. A PID of -1
       is special; it indicates all processes except the kill  process  itself
       and init.

SIGNALS
       The  signals  listed  below  may  be available for use with kill.  When
       known constant, numbers and default behavior are shown.

       Name     Num   Action    Description
       0          0   n/a       exit code indicates if a signal may be sent
       ALRM      14   exit
       HUP        1   exit
       INT        2   exit
       KILL       9   exit      cannot be blocked
       PIPE      13   exit
       POLL           exit
       PROF           exit
       TERM      15   exit
       USR1           exit
       USR2           exit
       VTALRM         exit
       STKFLT         exit      might not be implemented
       PWR            ignore    might exit on some systems
       WINCH          ignore
       CHLD           ignore
       URG            ignore
       TSTP           stop      might interact with the shell
       TTIN           stop      might interact with the shell
       TTOU           stop      might interact with the shell
       STOP           stop      cannot be blocked
       CONT           restart   continue if stopped, otherwise ignore
       ABRT       6   core
       FPE        8   core
       ILL        4   core
       QUIT       3   core
       SEGV      11   core
       TRAP       5   core
       SYS            core      might not be implemented
       EMT            core      might not be implemented
       BUS            core      core dump might fail
       XCPU           core      core dump might fail
       XFSZ           core      core dump might fail



---

### Post by Bashing-om on 2014-02-07
@ bc.haynes;

Short version:
There are other interrupt levels of kill that may be sent but here '9" is sent ->
No nonsense taken and no messing about, just kill that process:
send signal 9 (SIGKILL) which is used for forced termination to PID #<whatever>.

[INDENT]wonderful little system that it is
[/INDENT]

---

### Post by bc.haynes on 2014-02-08
Thank you, **Iowan **& **Bashing-om** for the tutorial. You guys really get around....that's good for me....I have a lot of questions.

---

### Post by Gonzalo_de_la_Vega on 2014-02-10
Thanks for all your replies.

Clearly I have omitted some important information, so let me rectify that:
This is a Ubuntu Server 12.04 LTS, with kernel 3.2.0-27-generic running on a Dell PowerEdge T110 II server with two 500Gb disks with software RAID and has a couple of Xen VMs running on it. I plugged a USB external disk that worked correctly on my laptop (Ubuntu Desktop 13.04).
The mount process that I can't kill is running on DOM0. There is no fuse, I ran mount manually and it never exited. I have tried killing mount with SIGKILL and other signals, but the process is still there, using 100% of one CPU.
I searched about this but, in short, what I found is:
* Kill the parent process
* umount what is being mounted, so that mount catches the signal.
* Send SIGKILL, which will work though it may take some time, but it should always work... but 65 hours is A LOT of time for a computer. 

Non of that worked, obviously.

What I don't understand is that even if the problem comes from hardware (whatever the problem is), why is it that I can't kill mount which is a user space process. I would understand not be able to rmmod the USB storage module... which I can't right now anyway, because the modules is being used.

---

