---
title: "Gdebi Installer quit working"
date: 2007-09-17
forum: General Help
---

### Post by oracle5 on 2007-09-17
Whenever I try to run the gdebi package installer nothing at all happens. When I run it in the terminal I get the following output.

brandon@brandon-laptop:~$ gdebi-gtk
/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/gdebi-gtk", line 31, in <module>
    from GDebi.GDebi import GDebi
ImportError: No module named GDebi.GDebi

I used dpkg to do what I wanted but I would really like for gdebi to be working again. Anybody have any ideas on how to fix this problem or are other people also suffering from this problem.

Thanks,
oracle5

---

### Post by Digitallysick on 2007-09-17
have you went into synaptic and tried to search for "gdebi" to see if you can reinstall it?

---

### Post by oracle5 on 2007-09-17
Its there and I did reinstall it but I still have the problem.

oracle5

---

