---
title: "Can't Change Directory"
date: 2007-06-13
forum: General Help
---

### Post by golfy on 2007-06-13
Hi, I am new to ubuntu and am trying to install some software. When I go cd /media the terminal changes to media$

when i go cd /home it changes to home$

but when I go cd /home/ubuntu/Desktop/ or cd /home/ubuntu/Desktop/liarliar-0.5.2 then it comes up with no file or directory (or similar) 

Can you tell me what I am doing wrong - I am using the live CD.

Original question is on the thread below

[http://ubuntuforums.org/showthread.php?t=472006](http://ubuntuforums.org/showthread.php?t=472006)

Thanks

Dave

---

### Post by zer0x41 on 2007-06-13
> **golfy said:**
> Hi, I am new to ubuntu and am trying to install some software. When I go cd /media the terminal changes to media$

when i go cd /home it changes to home$

but when I go cd /home/ubuntu/Desktop/ or cd /home/ubuntu/Desktop/liarliar-0.5.2 then it comes up with no file or directory (or similar) 

Can you tell me what I am doing wrong - I am using the live CD.

Original question is on the thread below

[http://ubuntuforums.org/showthread.php?t=472006](http://ubuntuforums.org/showthread.php?t=472006)

Thanks

Dave


Your syntax is ok!
In terminal press:
```
cd /home/ubuntu/
```
and then
```
ls -l
```

Now write us what you see after the enter press!

---

### Post by golfy on 2007-06-13
Hi zer0x41

Thanks for the info - I tried that but got this

ubuntu@ubuntu:~$ cd /home/ubuntu/
ubuntu@ubuntu:~$ ls -1
Desktop
ubuntu@ubuntu:~$ cd /liarliar-0.5.2
bash: cd: /liarliar-0.5.2: No such file or directory
ubuntu@ubuntu:~$

The liarliar-0.5.2 folder was visible on the desktop using the browser - any more help would ge great.

Dave

---

### Post by stchman on 2007-06-13
> **golfy said:**
> Hi zer0x41

Thanks for the info - I tried that but got this

ubuntu@ubuntu:~$ cd /home/ubuntu/
ubuntu@ubuntu:~$ ls -1
Desktop
ubuntu@ubuntu:~$ cd /liarliar-0.5.2
bash: cd: /liarliar-0.5.2: No such file or directory
ubuntu@ubuntu:~$

The liarliar-0.5.2 folder was visible on the desktop using the browser - any more help would ge great.

Dave

You will need to type the following:

cd /home/ubuntu/Desktop

Then see if there is the liar folder in there.

---

