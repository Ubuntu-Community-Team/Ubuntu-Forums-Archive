---
title: "System Program Problem Detected"
date: 2012-10-23
forum: General Help
---

### Post by Randy Schilling on 2012-10-23
Starting a week ago or so, every time I login to Ubuntu, I get
a little window that tells me:

System Program Problem Detected
Do You want to report the problem now?

I reported it once.   

I haven't noticed any problem, beside the popop getting to be annoying.

How can I find what is the problem and hopefully correct it?

---

### Post by 2F4U on 2012-10-23
If you opt to report the problem the system should  show you details about what will be reported. Do you experience any negative effects as a result of the problem report?

---

### Post by ~LoKe on 2012-10-23
I was getting this constantly, too.  To be honest, I just disabled it.

```
gksu gedit /etc/default/apport
```
change **enabled=1** to **enabled=0**.

---

### Post by Randy Schilling on 2012-10-23
Yes, reporting does lead to more details:

Sorry, the application session-installer has closed unexpectedly.

and

Problem report applies to a program that is not installed anymore
(/usr/src/php/php-t..4.8/tmp.php.ini).

I inadvertently ignored some error messages in my first php5 installation.
I've repeated that installation, this time correcting the errors,
and I no longer get the "system program problem detected" message.

Thanks Thanks Thanks - Randy

---

