---
title: "mount: / is busy during shutdown"
date: 2013-01-14
forum: General Help
---

### Post by manmath on 2013-01-14
Hi All, I'm running Quantal Kubuntu. The system is running fairly well. But it takes long to shutdown and throws "mount:/ is busy" before halting.

Please suggest me some fix. I'm afraid uncleaned shutdown may corrupt my drive and data.

---

### Post by dannyboy79 on 2013-01-14
what button are you pushing or what command are you using to "shutdown" the system?

---

### Post by manmath on 2013-01-14
I'm just clicking "Shutdown" button of the kubuntu start menu.

---

### Post by matt_symes on 2013-01-14
Hi

What application, daemons, services do you have running when you try to shut down ?

Do you have any network services running ?

Check to see what has open files etc on the root partition using the commands *fuser* or *losf*.

You can send a SIGTERM (not a SIGKILL) to each running process before shutting  down and try to see what has a lock on your root partition. You  can use a binary search to make this quicker. See if any are not exiting promptly.

Find out what application/service is keeping your partition busy. That's where i would start.

Kind regards

---

### Post by manmath on 2013-01-14
> **matt_symes said:**
> Hi

Check to see what has open files etc on the root partition using the commands *fuser* or *losf*.

You can send a SIGTERM (not a SIGKILL) to each running process before shutting  down and try to see what has a lock on your root partition. You  can use a binary search to make this quicker....

How? Please elaborate a bit.

---

### Post by sandyd on 2013-01-14
Have you checked to see if it is related to [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1019347](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1019347) ?

---

### Post by manmath on 2013-01-14
Yes, I did check. But I really can't make out anything from it. Well, before heading anything forward here's some info you might need:

My system has 2 drives:
an ssd for / partition
an hdd for /home partition

Board is gigabyte h61m-ds2, pentium g620 proc. I'm using xorg-edgers kernel, xorg and drivers.

Is it that ssd is unmounting faster than hdd and that message is about waiting for hdd to unmount, cos imo /home is someway linked to / or what? or are xorg-edgers packages are causing it?

---

### Post by sandyd on 2013-01-15
Run this - if there is no  mount:/ is busy during shutdown, there is a fix.
```

sudo stop lightdm
sudo shutdown -h now
```
Else, we will have to diagnose it, since it should be a bug.

---

### Post by manmath on 2013-01-15
Tried:

sudo stop lightdm
sudo shutdown -h now

System shuts down but that "mount: / is busy" still shows up 2-3 seconds before the system halts.

---

### Post by rnerwein on 2013-01-16
> **manmath said:**
> Tried:

sudo stop lightdm
sudo shutdown -h now

System shuts down but that "mount: / is busy" still shows up 2-3 seconds before the system halts.
hi
don't worry. this is the secure way of the OS to bring the box down. have a look at
/etc/init.d/killprocs .
first the system wants to bring it down on the soft way and send signal 15 (SIGTERM) which can be blocked by a process ( think about DB-process which have to some work before exiting .....).  after that the system will send a kill of death (can't be blocked - signal 9 -> SIGKILL).
on strange situations e.g. a process hangs in a fast I/O eg. disk I/O caused by a corrupted hardware the process couldn't be kill and the filesystem isn't marked clean.
i think you have installed a foreign SW whith process(es) blocking SIGTERM.
ciao

---

### Post by manmath on 2013-01-16
> **rnerwein said:**
> ... you have installed a foreign SW whith process(es) blocking SIGTERM.
ciao What's foreign SW?

---

### Post by sandyd on 2013-01-16
Since you can shutdown properly with those commands, you are affected by the bug I previously mentioned ([https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1019347](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1019347))

You can try #4 in the comments if you want
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1019347/comments/4](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1019347/comments/4)

---

### Post by manmath on 2013-01-16
Oh! Tried that as well. Doesn't work in my case. Still that "mount: / is busy" comes up every time, and the shutdown takes long.

Yeah, I got some clue into the problem but don't know how to solve.

Actually Today I installed virtualbox on another kubuntu 12.10 machine. Right after that this machine also started taking long to boot and shows that "mount: / is busy" message. It also reminds me that the previous machine was working fine and shutting down gracefully till I installed virtualbox.

Please somebody suggest me what to do.

---

### Post by matt_symes on 2013-01-19
Hi

If you are using wireless, uncheck "available to all users" on the wireless dialog. 

This fixed the problem for a number of users in that bug report and may be the same for you.

Hopefully that will close whatever file is locking your root partition before shutdown.

Kind regards

---

### Post by manmath on 2013-01-20
I'm not using wireless. And as a workaround I remove as many wireless packages as possible from my install such as modemmanager, iw and a few others. But the problem persists.

---

### Post by matt_symes on 2013-01-22
Hi 

Please follow post #4 from sandy's link and post the results of the file (process.log) back here.

We cannot help if you don't help us by supplying information.

Kind regards

---

