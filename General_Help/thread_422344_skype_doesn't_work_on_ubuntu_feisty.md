---
title: "skype doesn't work on ubuntu feisty"
date: 2007-04-25
forum: General Help
---

### Post by aubrey on 2007-04-25
The following is the error on my side, really appreciate for any help and suggestions.

Thanks,
-Aubrey

=========================================
aubrey@ubuntu-feisty:~$ uname -a
Linux ubuntu-feisty 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux
aubrey@ubuntu-feisty:~$ skype
Segmentation fault (core dumped)

---

### Post by aubrey on 2007-04-26
Didn't someone encounter the same issue as mine?
Odd, :(

---

### Post by haricharan on 2007-04-26
where did you install skype from??...i am using skype on feisty and it works fine for me....do you have an svn version??

---

### Post by pieterventer on 2007-05-21
> **haricharan said:**
> where did you install skype from??...i am using skype on feisty and it works fine for me....do you have an svn version??
I did my install from automatix and have the same problem try skype alpha 1.4 a again the same problem &#8220; Segmentation fault (core dumped)&#8221; had the same problem in Ubuntu 6.06 LTS and now in ubuntu feisty please help. when a try to open skype again message "please reinstall" .

---

### Post by oldHat on 2007-05-21
I had some problems using skype and scim together. 

If you're using scim you might be having the same problem. 

If so, you could try this from the command line:  XMODIFIERS=@im=none QT_IM_MODULE=xim skype

---

### Post by pieterventer on 2007-05-21
I try the above and still not working, same error  &#8220; Segmentation fault (core dumped)&#8221;

---

### Post by pieterventer on 2007-05-31
Segmentation Fault occurred when running c program that is reading or writing non-exist segment(physical memory space). Example, declare an array of int x[5] and you try putting or reading 6th item(s) that the cpu system to crash or segmentation fault is a type of error which occurs when u try to access a non existant physical memory address. Sometimes during execution of a C program u freed memory and then within the scope of the same program try again to use the same memory, then also the seg. fault occurs, this is due to the fact that untill the completion of the program the memory utilised is not returned to the operating system.

My processor is Celeron D 3200 LGA775 pin I install from &#8220;synaptic package manager&#8221; &#8220;microcode.ctl&#8221; (Intel IA32/IA64 CPU Microcode Utility) and &#8220;libc6-i686&#8221; (GNU C Library Shared libraries [i686 optimized]) and now skype is working with no problems.

---

