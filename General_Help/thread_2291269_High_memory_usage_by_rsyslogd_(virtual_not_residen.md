---
title: "High memory usage by rsyslogd (virtual not resident)"
date: 2015-08-18
forum: General Help
---

### Post by username9 on 2015-08-18
Good evening.

So, after using Linux for a while, I noticed that each rsyslogd thread is taking a lot of memory 252MB Virtual Memory.

I read that virtual memory is allocated but not used, but regardless, that never has happened before:

[IMG]http://imagizer.imageshack.us/v2/1024x768q90/538/qcMZAO.png[/IMG]


The output of free -mh command:
[IMG]http://imageshack.com/a/img910/3551/rwLjN2.png[/IMG]


So, how do I correct this issue (if it needs to be corrected)?

Regards.

---

### Post by username9 on 2015-08-19
Up :p

---

### Post by username9 on 2015-08-20
Bump...

---

### Post by matt_symes on 2015-08-20
Hi

Can you copy and paste the text from the free command and please post the output of this command as well.

```
ps -L -C rsyslogd -o command,vsize,rss,%mem,size
```

Pictures are no good when I'm using my phone.

I'll take a look tomorrow UK time.

Kind regards

---

### Post by username9 on 2015-08-20
> **matt_symes said:**
> Hi

Can you copy and paste the text from the free command and please post the output of this command as well.

```
ps -L -C rsyslogd -o command,vsize,rss,%mem,size
```

Pictures are no good when I'm using my phone.

I'll take a look tomorrow UK time.

Kind regards

Hello.

Thank you for taking your time to reply :-)

The result of the free -mh command:
```

:~$ free -mh
             total       used       free     shared    buffers     cached
Mem:          3.9G       3.7G       169M       3.5M       7.2M       165M
-/+ buffers/cache:       3.5G       342M
Swap:         1.1G       4.8M       1.1G
```

The results of the command you asked:
```

:~$ ps -L -C rsyslogd -o command,vsize,rss,%mem,size
COMMAND                        VSZ   RSS %MEM  SIZE
/usr/sbin/rsyslogd -n       258664  2864  0.0 222460
/usr/sbin/rsyslogd -n       258664  2864  0.0 222460
/usr/sbin/rsyslogd -n       258664  2864  0.0 222460
/usr/sbin/rsyslogd -n       258664  2864  0.0 222460

```

Regards.

---

### Post by matt_symes on 2015-08-21
Hi

Looks similar to what I have.

What version of rsyslogd are you running ?

```
rsyslogd -v
```

Kind regards

---

### Post by username9 on 2015-08-21
> **matt_symes said:**
> Hi

Looks similar to what I have.

What version of rsyslogd are you running ?

```
rsyslogd -v
```

Kind regards

Hello.

The output of the ***rsyslogd -v*** command is the following:

```
rsyslogd 8.4.2, compiled with:
        FEATURE_REGEXP:                         Yes
        GSSAPI Kerberos 5 support:              Yes
        FEATURE_DEBUG (debug build, slow code): No
        32bit Atomic operations supported:      Yes
        64bit Atomic operations supported:      Yes
        memory allocator:                       system default
        Runtime Instrumentation (slow code):    No
        uuid support:                           Yes
        Number of Bits in RainerScript integers: 64


See http://www.rsyslog.com for more information.

```

You said that the output is similar to yours, so is rsyslog also taking a lot of RAM in your system?

Best regards.

---

### Post by matt_symes on 2015-08-21
Hi

You have a slightly newer version of rsyslog than me which mostly likely explains the small increase in size that you have over mine.

But anyway the sizes you are seeing on the threads are rather misleading as they include shared libraries that are mapped into the virtual address space of each thread but only one copy needs to be loaded for all the threads. If the threads share libraries with other processes then these are also mapped.

I'm currently typing on my phone so typing long posts is hard. If you can wait till tomorrow I'll give a far more detailed explanation.

But you have nothing to worry about there.

Kind regards

---

### Post by SeijiSensei on 2015-08-21
> **username9 said:**
> The results of the command you asked:
```

:~$ ps -L -C rsyslogd -o command,vsize,rss,%mem,size
COMMAND                        VSZ   RSS %MEM  SIZE
/usr/sbin/rsyslogd -n       258664  2864  0.0 222460
/usr/sbin/rsyslogd -n       258664  2864  0.0 222460
/usr/sbin/rsyslogd -n       258664  2864  0.0 222460
/usr/sbin/rsyslogd -n       258664  2864  0.0 222460

```

Each individual instance is only using 2864K; the VSZ includes all the shared libraries that rsyslogd uses.

---

### Post by username9 on 2015-08-21
> **matt_symes said:**
> Hi

You have a slightly newer version of rsyslog than me which mostly likely explains the small increase in size that you have over mine.

But anyway the sizes you are seeing on the threads are rather misleading as they include shared libraries that are mapped into the virtual address space of each thread but only one copy needs to be loaded for all the threads. If the threads share libraries with other processes then these are also mapped.

I'm currently typing on my phone so typing long posts is hard. If you can wait till tomorrow I'll give a far more detailed explanation.

But you have nothing to worry about there.

Kind regards

Thanks.

If you can spare some time to explain, it would be great. :)

Regards.

> **SeijiSensei said:**
> Each individual instance is only using 2864K; the VSZ includes all the shared libraries that rsyslogd uses.

Hello.

That's why I if I should be worried (as it was virtual and not resident). 

The thing is some monitoring tools keep sending warnings and so on, and some documentation I read offers conflicting information.

Regards.

---

