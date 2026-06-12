---
title: "Gparted Not Working"
date: 2016-09-28
forum: General Help
---

### Post by bookie2 on 2016-09-28
Hi guys!
I have had problems starting gparted on 16.04.1 I have tried completely removing it and then reinstalling via command line...

The command line doesn't show any errors until I try running gparted..

I get this error:
```


/usr/sbin/gpartedbin: symbol lookup error: /usr/lib/x86_64-linux-gnu/libgiomm-2.4.so.1: undefined symbol: _ZN4Glib11VariantTypeD1Ev



```

Does anyone have any ideas?

bookie32

---

### Post by howefield on 2016-09-28
Are you running Ubuntu in a VM ?

---

### Post by bookie2 on 2016-09-28
No, but I have Vmware workstation 12 installed

---

### Post by howefield on 2016-09-28
> **bookie2 said:**
> No, but I have Vmware workstation 12 installed

I think that'll be the problem perhaps, a bug with vmware rather than an issue with gparted.

Put the error into a web search engine, you'll find threads such as..

[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/1509729](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/1509729)

with some "solved" comments near the bottom of the thread.

---

### Post by bookie2 on 2016-09-28
I had loaded the error into a web browser and tried several replies but your one worked....:D

I used this info:

```


[Michael Fox (mfox-trentu)]("https://launchpad.net/%7Emfox-trentu")             wrote             on 2015-11-15:                                                 [TABLE]
[TR]
[TD][/TD]
[TD="class: bug-comment-index"]           [ #14]("https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/1509729/comments/14")           [/TD]
         [/TR]
            [/TABLE]
                               A variant of trinkity's solution finally worked for me:
 I deleted  LD_LIBRARY_PATH.conf file in /etc/ld.so.conf.d
 and then executed the command $ sudo ldconfig
 This worked, and VMware Player still seems to work as well.
 I had tried altering the contents of that file before, but I may not  have reconfigured ld before checking, and that may have been the  problem.

              



```

Works perfectly!!

Thanks!

bookie32

---

### Post by howefield on 2016-09-28
Cool, glad you got it sorted, feel free to mark the thread as solved.

---

