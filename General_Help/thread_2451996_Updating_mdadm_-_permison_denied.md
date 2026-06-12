---
title: "Updating mdadm - permison denied"
date: 2020-10-14
forum: General Help
---

### Post by helen314 on 2020-10-14
I cannot update mdadm.conf - receiving "permission denied ".


a@a-SATA:~$ sudo mdadm --detail --scan >> /etc/mdadm.conf
bash: /etc/mdadm.conf: Permission denied
a@a-SATA:~$ 

What am I missing ? 
I did not change anything intentionally and have no idea why it quit working and is giving
'permissions denied ' error. 

Here is partial output from " ls -l " 


drwxr-xr-x  2 root root    4096 Oct 11 18:38 mdadm
-rw-r--r--  1 root root     732 Oct 13 14:12 mdadm.conf

---

### Post by TheFu on 2020-10-14
The 
```
>> /etc/mdadm.conf
```
part is running with your userid for that part of the process.
Each part of redirection or pipes runs in a new process.

Trying to jump into intermediate admin tasks without the proper background will always have little issues like this until the necessary background and skills have been learned.
Start here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

A common solution for something like this is to use **tee**.
```
sudo mdadm --detail --scan | sudo tee -a /etc/mdadm.conf
```
There are other methods. Just depends who you ask.

BTW, I think that's the incorrect output file location too.

---

### Post by helen314 on 2020-10-14
> **TheFu said:**
> The 
```
>> /etc/mdadm.conf
```
part is running with your userid for that part of the process.
Each part of redirection or pipes runs in a new process.

Trying to jump into intermediate admin tasks without the proper background will always have little issues like this until the necessary background and skills have been learned.
Start here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

A common solution for something like this is to use **tee**.
```
sudo mdadm --detail --scan | sudo tee -a /etc/mdadm.conf
```
There are other methods. Just depends who you ask.

BTW, I think that's the incorrect output file location too.

Interesting reply. 
Did not really answer WHY  my command did not work,
just replaced with "pipe". 
Made uncalled for remarks about learning and skills.  
CASE CLOSED

---

### Post by CelticWarrior on 2020-10-14
The remarks were very much called for and should give you pause to think about since it's becoming a staple of your threads.
You ask about something, often with fundamental misunderstandings, and when people point out the problems and give you a correct answer that you don't like you typically assume they don't read your post and/or don't want to answer your questions.

Please take a different approach from now on. Please read the links expert users post because more often than not they show exactly what you need to understand and what you've been doing wrong and don't want to admit. This one is textbook example of WHY your command didn't work:
> [COLOR=#000000]*The*[/COLOR]
[COLOR=#000000][I]Code:
>> /etc/mdadm.conf[/I][/COLOR]
[COLOR=#000000]*part is running with your userid for that part of the process.*[/COLOR]
[COLOR=#000000]*Each part of redirection or pipes runs in a new process.*[/COLOR]


---

