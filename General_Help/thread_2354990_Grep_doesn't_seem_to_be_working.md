---
title: "Grep doesn't seem to be working"
date: 2017-03-08
forum: General Help
---

### Post by Randymanme on 2017-03-08
Hello, all,
 
 At [https://www.cyberciti.biz/faq/linux-xen-vmware-kvm-intel-vt-amd-v-support/](https://www.cyberciti.biz/faq/linux-xen-vmware-kvm-intel-vt-amd-v-support/) , I see that to find out if my notebook supports virtualization, type into the terminal: # grep --color vmx /proc/cpuinfo.  But when I do so, I don&#8217;t get any output.
 
 I have ack-grep 2.14-4, agrep 4.17-9, and grep 2.25-6 installed on Ubuntu 16.10.   
 
 What do I need to do to find out if my notebook supports virtualization?

---

### Post by howefield on 2017-03-08
Don't use the leading # symbol, ie the command is..

```
grep --color vmx /proc/cpuinfo
```

---

### Post by Randymanme on 2017-03-08
Viola!  

Thanks.

---

### Post by howefield on 2017-03-08
> **Randymanme said:**
> Thanks.

You're welcome. :)

---

