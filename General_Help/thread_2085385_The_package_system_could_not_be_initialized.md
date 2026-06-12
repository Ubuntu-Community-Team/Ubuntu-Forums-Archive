---
title: "The package system could not be initialized"
date: 2012-11-18
forum: General Help
---

### Post by amir786_z on 2012-11-18
Hi there guys i have the following error popping up, when i open my package manager.
The package system could not be initialized, your configuration may be broken.

Thanks.

---

### Post by ibjsb4 on 2012-11-18
Try

sudo dpkg --configure -a

See if that will do any good

---

### Post by raja.genupula on 2012-11-18
> **ibjsb4 said:**
> Try

```
sudo dpkg --configure -a
```

See if that will do any good

+1 

but one more thing needed to do .
thats 

```
sudo apt-get install -f
```.

---

### Post by amir786_z on 2012-11-29
> **raja.genupula said:**
> +1 

but one more thing needed to do .
thats 

```
sudo apt-get install -f
```.

Thanks for replaying but still crashes with an error :(

amir@amir-HP-Pavilion-dv5-Notebook-PC:~$ sudo dpkg --configure -a
[sudo] password for amir: 
amir@amir-HP-Pavilion-dv5-Notebook-PC:~$ 
amir@amir-HP-Pavilion-dv5-Notebook-PC:~$ 
amir@amir-HP-Pavilion-dv5-Notebook-PC:~$ sudo apt-get install -f
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/deb.torproject.org_torproject.org_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
amir@amir-HP-Pavilion-dv5-Notebook-PC:~$

---

### Post by amir786_z on 2012-12-01
no one knows about this issue??:(

---

### Post by amir786_z on 2012-12-11
Can someone tell me the solution of this problem..??

---

### Post by ibjsb4 on 2012-12-12
This should do it

```
sudo rm /var/lib/apt/lists/* -vf && sudo apt-get update
```

Also sorry for the delay, your post somehow got dropped.

---

### Post by amir786_z on 2012-12-13
Thanks it worked :)

---

