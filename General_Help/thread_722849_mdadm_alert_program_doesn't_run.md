---
title: "mdadm alert program doesn't run"
date: 2008-03-12
forum: General Help
---

### Post by todlangweilig on 2008-03-12
I have set up a RAID 0 array, /dev/md0, successfully. I am trying to get a small python program, that I wrote for dealing with mdadm events, to work. I couldn't get mdadm to execute the program however. So I wrote/copied a small shell script to see if I could get mdadm to work with that, it doesn't. And this is where I am now. 

First things first, which config file am I supposed to use, /etc/mdadm/mdadm.conf or /etc/mdadm.conf? It seems that from the mdadm man page, that Im supposed to use the first. Either way, I have a PROGRAM statement in both config files. 

Here is the relevant part of my mdadm.conf file:
```
PROGRAM /home/serv1/py-mdadm/testshell.sh
```

My testshell.sh program works as expected when executed from the command line. I have also executed chmod +x on it as well. 
```
#! /bin/bash         
echo Hello World

ls > filename.txt 
```

To test out this shell script, I am using the following command. I know it's atleast partially working because it logs a TestMessage event in the syslog. 
```
sudo mdadm --monitor -scan -1yt -program /dev/md0
```

I don't know what else to do at this point, and I would really like to get this working. Any help would be appreciated.

---

### Post by todlangweilig on 2008-03-13
*bumb* I'd really like to get this to work

---

### Post by Tedderouni on 2008-04-17
Hi,

Did you ever get this working?  I'm having the same problem.

I wrote a script called mdadm-send-alerts.  I can't even get mdadm to execute it.  I can test the script successfully, so i know that works... to test it, for now i'm just having it echo the first argument:

```
# /usr/bin/mdadm-send-alerts test-arg
test-arg
#
```

... but when i try to use mdadm on it,  I get nothing:

```
# mdadm --monitor --test --program=/usr/bin/mdadm-send-alerts -c /etc/mdadm.conf --oneshot /dev/md0
#
```


...so it's not even executing it for some reason.  Were you able to determine what the problem was?

Thanks!
-Ted

---

### Post by todlangweilig on 2008-04-18
I was never able to figure out what the problem was, nor was I able to get it to work. I have just been too busy to worry about it. I would say that your best bet would be to post your question on the mdadm mailing list, I've read that it's the best place to get your question answered. I've been too busy/lazy to do that either. I've having some trouble finding it, here is a link that may help some. 

[http://neil.brown.name/blog/mdadm]("http://neil.brown.name/blog/mdadm")

If you find out what the problem is, please post it here for the rest of us. If I get around to it, I'll do the same.

---

### Post by Tedderouni on 2008-06-29
Hi,

It's been a while, but I've been playing with this again lately.  This thread seems to have solved my problem (specifically, the post by Kevlaur, post #7):

[http://ubuntuforums.org/showthread.php?p=4552684]("http://ubuntuforums.org/showthread.php?p=4552684")

I guess there must have just been something wrong with my script, because the mdadm test runs the one from the above thread with no problems.

---

### Post by todlangweilig on 2008-06-30
Well, that seemed to solve the problem. thanks a lot.:)

---

