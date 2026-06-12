---
title: "manpage for pthread_once is missing"
date: 2022-04-04
forum: General Help
---

### Post by pep37619 on 2022-04-04
I'm running Ubuntu 20.04 LTS, and the manpage for pthread_once appears to be missing:

```
ppelleti@midnight-star:~$ man pthread_once
No manual entry for pthread_once
```

However, I seem to have all of the other pthread manpages:

```
ppelleti@midnight-star:/usr/share/man/man3$ ls -lh pthread*
lrwxrwxrwx 1 root root   22 Feb  9  2020 pthread_attr_destroy.3.gz -> pthread_attr_init.3.gz
lrwxrwxrwx 1 root root   32 Feb  9  2020 pthread_attr_getaffinity_np.3.gz -> pthread_attr_setaffinity_np.3.gz
lrwxrwxrwx 1 root root   32 Feb  9  2020 pthread_attr_getdetachstate.3.gz -> pthread_attr_setdetachstate.3.gz
lrwxrwxrwx 1 root root   30 Feb  9  2020 pthread_attr_getguardsize.3.gz -> pthread_attr_setguardsize.3.gz
lrwxrwxrwx 1 root root   33 Feb  9  2020 pthread_attr_getinheritsched.3.gz -> pthread_attr_setinheritsched.3.gz
lrwxrwxrwx 1 root root   31 Feb  9  2020 pthread_attr_getschedparam.3.gz -> pthread_attr_setschedparam.3.gz
lrwxrwxrwx 1 root root   32 Feb  9  2020 pthread_attr_getschedpolicy.3.gz -> pthread_attr_setschedpolicy.3.gz
lrwxrwxrwx 1 root root   26 Feb  9  2020 pthread_attr_getscope.3.gz -> pthread_attr_setscope.3.gz
lrwxrwxrwx 1 root root   26 Feb  9  2020 pthread_attr_getstack.3.gz -> pthread_attr_setstack.3.gz
lrwxrwxrwx 1 root root   30 Feb  9  2020 pthread_attr_getstackaddr.3.gz -> pthread_attr_setstackaddr.3.gz
lrwxrwxrwx 1 root root   30 Feb  9  2020 pthread_attr_getstacksize.3.gz -> pthread_attr_setstacksize.3.gz
-rw-r--r-- 1 root root 3.4K Feb  9  2020 pthread_attr_init.3.gz
-rw-r--r-- 1 root root 2.0K Feb  9  2020 pthread_attr_setaffinity_np.3.gz
-rw-r--r-- 1 root root 1.7K Feb  9  2020 pthread_attr_setdetachstate.3.gz
-rw-r--r-- 1 root root 2.5K Feb  9  2020 pthread_attr_setguardsize.3.gz
-rw-r--r-- 1 root root 2.0K Feb  9  2020 pthread_attr_setinheritsched.3.gz
-rw-r--r-- 1 root root 1.9K Feb  9  2020 pthread_attr_setschedparam.3.gz
-rw-r--r-- 1 root root 1.8K Feb  9  2020 pthread_attr_setschedpolicy.3.gz
-rw-r--r-- 1 root root 2.1K Feb  9  2020 pthread_attr_setscope.3.gz
-rw-r--r-- 1 root root 2.3K Feb  9  2020 pthread_attr_setstack.3.gz
-rw-r--r-- 1 root root 1.8K Feb  9  2020 pthread_attr_setstackaddr.3.gz
-rw-r--r-- 1 root root 1.8K Feb  9  2020 pthread_attr_setstacksize.3.gz
-rw-r--r-- 1 root root 2.8K Feb  9  2020 pthread_cancel.3.gz
lrwxrwxrwx 1 root root   25 Feb  9  2020 pthread_cleanup_pop.3.gz -> pthread_cleanup_push.3.gz
lrwxrwxrwx 1 root root   34 Feb  9  2020 pthread_cleanup_pop_restore_np.3.gz -> pthread_cleanup_push_defer_np.3.gz
-rw-r--r-- 1 root root 3.3K Feb  9  2020 pthread_cleanup_push.3.gz
-rw-r--r-- 1 root root 1.8K Feb  9  2020 pthread_cleanup_push_defer_np.3.gz
-rw-r--r-- 1 root root 4.5K Feb  9  2020 pthread_create.3.gz
-rw-r--r-- 1 root root 1.7K Feb  9  2020 pthread_detach.3.gz
-rw-r--r-- 1 root root 1.3K Feb  9  2020 pthread_equal.3.gz
-rw-r--r-- 1 root root 2.0K Feb  9  2020 pthread_exit.3.gz
lrwxrwxrwx 1 root root   27 Feb  9  2020 pthread_getaffinity_np.3.gz -> pthread_setaffinity_np.3.gz
-rw-r--r-- 1 root root 2.5K Feb  9  2020 pthread_getattr_default_np.3.gz
-rw-r--r-- 1 root root 3.8K Feb  9  2020 pthread_getattr_np.3.gz
lrwxrwxrwx 1 root root   27 Feb  9  2020 pthread_getconcurrency.3.gz -> pthread_setconcurrency.3.gz
-rw-r--r-- 1 root root 2.4K Feb  9  2020 pthread_getcpuclockid.3.gz
lrwxrwxrwx 1 root root   23 Feb  9  2020 pthread_getname_np.3.gz -> pthread_setname_np.3.gz
lrwxrwxrwx 1 root root   26 Feb  9  2020 pthread_getschedparam.3.gz -> pthread_setschedparam.3.gz
-rw-r--r-- 1 root root 2.1K Feb  9  2020 pthread_join.3.gz
-rw-r--r-- 1 root root 1.8K Feb  9  2020 pthread_kill.3.gz
-rw-r--r-- 1 root root 1.5K Feb  9  2020 pthread_kill_other_threads_np.3.gz
-rw-r--r-- 1 root root 1.7K Feb  9  2020 pthread_mutex_consistent.3.gz
lrwxrwxrwx 1 root root   29 Feb  9  2020 pthread_mutex_consistent_np.3.gz -> pthread_mutex_consistent.3.gz
-rw-r--r-- 1 root root 1.6K Feb  9  2020 pthread_mutexattr_getpshared.3.gz
lrwxrwxrwx 1 root root   32 Feb  9  2020 pthread_mutexattr_getrobust.3.gz -> pthread_mutexattr_setrobust.3.gz
lrwxrwxrwx 1 root root   32 Feb  9  2020 pthread_mutexattr_getrobust_np.3.gz -> pthread_mutexattr_setrobust.3.gz
lrwxrwxrwx 1 root root   33 Feb  9  2020 pthread_mutexattr_setpshared.3.gz -> pthread_mutexattr_getpshared.3.gz
-rw-r--r-- 1 root root 3.1K Feb  9  2020 pthread_mutexattr_setrobust.3.gz
lrwxrwxrwx 1 root root   32 Feb  9  2020 pthread_mutexattr_setrobust_np.3.gz -> pthread_mutexattr_setrobust.3.gz
lrwxrwxrwx 1 root root   34 Feb  9  2020 pthread_rwlockattr_getkind_np.3.gz -> pthread_rwlockattr_setkind_np.3.gz
-rw-r--r-- 1 root root 2.3K Feb  9  2020 pthread_rwlockattr_setkind_np.3.gz
-rw-r--r-- 1 root root 1.6K Feb  9  2020 pthread_self.3.gz
-rw-r--r-- 1 root root 2.7K Feb  9  2020 pthread_setaffinity_np.3.gz
lrwxrwxrwx 1 root root   31 Feb  9  2020 pthread_setattr_default_np.3.gz -> pthread_getattr_default_np.3.gz
-rw-r--r-- 1 root root 2.7K Feb  9  2020 pthread_setcancelstate.3.gz
lrwxrwxrwx 1 root root   27 Feb  9  2020 pthread_setcanceltype.3.gz -> pthread_setcancelstate.3.gz
-rw-r--r-- 1 root root 1.8K Feb  9  2020 pthread_setconcurrency.3.gz
-rw-r--r-- 1 root root 2.6K Feb  9  2020 pthread_setname_np.3.gz
-rw-r--r-- 1 root root 4.4K Feb  9  2020 pthread_setschedparam.3.gz
-rw-r--r-- 1 root root 1.8K Feb  9  2020 pthread_setschedprio.3.gz
-rw-r--r-- 1 root root 2.2K Feb  9  2020 pthread_sigmask.3.gz
-rw-r--r-- 1 root root 1.7K Feb  9  2020 pthread_sigqueue.3.gz
lrwxrwxrwx 1 root root   22 Feb  9  2020 pthread_spin_destroy.3.gz -> pthread_spin_init.3.gz
-rw-r--r-- 1 root root 2.4K Feb  9  2020 pthread_spin_init.3.gz
-rw-r--r-- 1 root root 1.7K Feb  9  2020 pthread_spin_lock.3.gz
lrwxrwxrwx 1 root root   22 Feb  9  2020 pthread_spin_trylock.3.gz -> pthread_spin_lock.3.gz
lrwxrwxrwx 1 root root   22 Feb  9  2020 pthread_spin_unlock.3.gz -> pthread_spin_lock.3.gz
-rw-r--r-- 1 root root 1.4K Feb  9  2020 pthread_testcancel.3.gz
lrwxrwxrwx 1 root root   23 Feb  9  2020 pthread_timedjoin_np.3.gz -> pthread_tryjoin_np.3.gz
-rw-r--r-- 1 root root 2.0K Feb  9  2020 pthread_tryjoin_np.3.gz
-rw-r--r-- 1 root root 1.6K Feb  9  2020 pthread_yield.3.gz
```

Why is this one manpage missing when all of the other pthread manpages are present?

---

### Post by Impavidus on 2022-04-05
It's supposed to be present: [https://packages.ubuntu.com/focal/all/glibc-doc/filelist](https://packages.ubuntu.com/focal/all/glibc-doc/filelist)
And on my 21.10 system it is. Was it lost somehow? Try reinstalling glibc-doc:```
sudo apt install --reinstall glibc-doc
```
If it happens often that files randomly disappear, consider that you may have a bad hard drive.

---

### Post by spjackson on 2022-04-05
It looks to me as though the pthread manpages that are present are those provided by the manpages-dev package. There are further pthread manpages in glibc-doc. I don't know why they are split like this but if you install the latter package, you should get what you are looking for.

---

### Post by pep37619 on 2022-04-05
Thanks!  Installing glibc-doc gave me the pthread_once manpage.

It would be nice if Ubuntu could suggest packages when a manpage is not found, just as it currently suggests packages when a command is not found.

---

### Post by Impavidus on 2022-04-06
I searched in synaptic for packages with pthread in the description. It wasn't too hard to find then.

---

### Post by pep37619 on 2022-06-01
> **Impavidus said:**
> I searched in synaptic for packages with pthread in the description. It wasn't too hard to find then.

Thanks!  I don't seem to have synaptic installed, but I found a different way that works for me.  I installed apt-file, and now I can use apt-file to search for missing manpages.

I ran into this problem again with the manpage for posix_spawn_file_actions_adddup2 being missing (even after installing glibc-doc), but I found it easily with apt-file:

```
$ apt-file search posix_spawn_file_actions_adddup2.3
manpages-posix-dev: /usr/share/man/man3/posix_spawn_file_actions_adddup2.3posix.gz
```

Although it's easy enough to fix now, I still think the organization of manpages is weird.  There seems to be at least three different packages (manpages-dev, glibc-doc, and manpages-posix-dev) that contain some of the manpages for C library functions, and often the same manpage is in two out of the three packages.

For example, the manpage for pthread_once is in both glibc-doc and manpages-posix-dev:

```
glibc-doc: /usr/share/man/man3/pthread_once.3.gz
manpages-posix-dev: /usr/share/man/man3/pthread_once.3posix.gz
```

but the manpage for pthread_create is in manpages-dev and manpages-posix-dev:

```
manpages-dev: /usr/share/man/man3/pthread_create.3.gz
manpages-posix-dev: /usr/share/man/man3/pthread_create.3posix.gz
```

There doesn't seem to be any rhyme or reason to the package organization that I can see.

---

