---
title: "How to change kernel, or get kernel sources?"
date: 2006-10-30
forum: General Help
---

### Post by scuzzo84 on 2006-10-30
I upgraded Ubuntu to 6.10 and it broke vmware. Anyways I am setting up vmware and im on the config part and im stuck on"

 ```

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 

The directory of kernel headers (version 2.6.17-10) does not match your running
kernel (version 2.6.17-10-386).  Even if the module were to compile 
successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]
```

before this step I was stuck to as my /usr/src directory was empty so I downloaded the kernel "2.6.17-10" and extracted it and got further in the steps, but I am stuck here and it says that my kernel is "2.6.17-10-386" and not "2.6.17-10" as the source is under /usr/src/linux which I extracted. So I cant find any kernel to download and extract that is "2.6.17-10-386" and I cant seem to install a generic kernel that will say "2.6.17-10" instead of what I have now. I tried "sudo aptitude install linux-generic" and I still have the kernel with 386 at the end.

What can I do to get past this step?

---

### Post by blind0wl on 2006-10-30
Can you post the output of uname -r

---

### Post by scuzzo84 on 2006-10-30
> **blind0wl said:**
> Can you post the output of uname -r

2.6.17-10-386

---

### Post by blind0wl on 2006-10-30
and whats the output of:

```
ls -al /usr/src/
```

---

### Post by scuzzo84 on 2006-10-30
> **blind0wl said:**
> and whats the output of:

```
ls -al /usr/src/
```


hkhalid@hccnas:~$ ls -al /usr/src/
total 12
drwxrwsr-x  3 root src  4096 2006-10-30 20:07 .
drwxr-xr-x 11 root root 4096 2006-09-27 12:13 ..
drwxr-xr-x 19 root root 4096 2006-10-27 13:42 linux
hkhalid@hccnas:~$ 

"linux" the directory is from a tarball of linux 2.6.17-10

---

### Post by blind0wl on 2006-10-30
have you tried 

```
apt-get install linux-headers-`uname -r`
```

instead of manually grabbing the source?

---

### Post by scuzzo84 on 2006-10-31
ok I just installed the linux headers, like 3 different versions from synaptic and that fixed it thanks

---

