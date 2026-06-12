---
title: "Package manager broken"
date: 2013-01-22
forum: General Help
---

### Post by ias on 2013-01-22
Hello,

I'm in Moscow, and suddenly the mouse buttons started going crazy.. then i realised something is wrong with the package manager.. 
Here is what it says on doing:

```
sudo apt-get update -f
```


Fetched 818 kB in 58s (14.1 kB/s)                                              
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
mmm@mmm-pc-tablet:~$ 

Please help!

Thanks, IS

---

### Post by Bucky Ball on 2013-01-22
[I]Thread moved to [B]General Help

Reason: [/B][/I]Not a security discussion.

---

### Post by ias on 2013-01-22
> **Bucky Ball said:**
> [I]Thread moved to [B]General Help

Reason: [/B][/I]Not a security discussion.

Ok, thanks. Were do i find it now? -- 

OK. GOT IT.

---

### Post by Soul-Sing on 2013-01-22
```
sudo rm /var/lib/apt/lists/* -vf

```

```
sudo apt-get update
```

---

