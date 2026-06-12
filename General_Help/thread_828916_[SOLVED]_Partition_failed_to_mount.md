---
title: "[SOLVED] Partition failed to mount"
date: 2008-06-14
forum: General Help
---

### Post by martin-seng on 2008-06-14
Hello, 

I'm kinda new to linux OS, but i feel happy using it, it's awesome! Thanks to worldwide contribution to this wonderful operating system!

I installed UBUNTU hardy into my ASUS F5RL and everything went fine. I partitioned my 160GB hardisk to "File System (ext3)" and another one called "96.0 GB Media (NTFS)" with windows vista ultimate inside but i deleted all include the windows system files...(i hope i'm doing the right thing, am i?)

Then i found a problem with Rhythmbox, it wont detect my library on the "96.0 GB media", not until i open file browser and click on the "96.0 GB Media". So i wanted to solve this problem but right clicking on the "96.0 GB Media", choose property and change the "filesystem" to NTFS and then BOOM! I cant access this partition anymore...The system will pop-up a message saying "The volume uses the NTFS file system which is not supported by your system"

Now my question is how to solve this dear ubuntuforum users? I have all my data inside this partition and hoping not to reformat it...I need help...


Martin

---

### Post by rraj.be on 2008-06-14
First install ntfs-3g

Go to Applications-->Accesories-->Terminal and 

Type this in terminal to install

```
sudo apt-get install ntfs-3g
```

Reboot and try to mount your drive.

I think there is no need to reboot but i dont know surelly.

---

### Post by martin-seng on 2008-06-14
hi rraj.be, 

Thank you for reply. I tried ntfs-3g and doesn't have the luck. It worked for you? Do you did the the way i did changing a drive's filesystem by hand?

---

### Post by rraj.be on 2008-06-14
No i haven't yet had such prob's.


Had you tried with NTFS config tool.

Its in 

```
Apllications-->System tools-->NTFS config tools
```


i am bit confused why.

Just wait some one to answer.
I am too trying.

---

### Post by martin-seng on 2008-06-14
Hi rraj.be, 

Yes i tried ntfs-3g, no luck. But this program solved my problem:

Disk Management

I installed it from the add/remove under application. And launch it by

```
System>Administration>Storage Device Manager
```

Martin

---

### Post by rraj.be on 2008-06-14
Much happy to here that.

Just mark the thread SOLVED by going to Thread tools at the top and selecting Mark this thread as solved, if your problem is solved.

this may help some other person with same problem.

---

