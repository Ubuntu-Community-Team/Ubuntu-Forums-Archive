---
title: "Howto refresh environment variables?"
date: 2007-02-24
forum: General Help
---

### Post by vharun on 2007-02-24
Hi,

I want to refresh/reload environment variables. Is there any way to load them without restarting the system?

Thanks in advance.

---

### Post by NewOldTimer on 2007-02-24
this what your looking for??


To use rehash command, simply called rehash at command line:

# rehash

rehash will update and refresh the OS’s path environmental variables to include the newly added and installed directories, thus enables users to call the functions and commands from any directory immediately without restarting the server.

---

### Post by vharun on 2007-02-24
Hi NewOldTimer,

Thanks for your reply. But rehash command does not work on my system. Do you know in which package is it? So i can install and use it. By the way i am using Kubuntu Feisty 7.04.

Thanks in advance.

---

### Post by NewOldTimer on 2007-02-24
not much help here, way outa my league I'll offer this and leave you to the more informed... sorry I couldn't  offer more

[http://groups.google.com/group/comp.os.linux/browse_thread/thread/a11eada31b9b9411/5ab2873fba59313b%235ab2873fba59313b](http://groups.google.com/group/comp.os.linux/browse_thread/thread/a11eada31b9b9411/5ab2873fba59313b%235ab2873fba59313b)..

---

### Post by vharun on 2007-02-25
:) Thanks anyway. Now I am reading about dpkg-reconfigure. I think so it does what i want.

---

### Post by Ramses de Norre on 2007-02-25
That's for reconfiguring installed packages, which env variables would you like to refresh?
If they are set in ~/.bashrc you can run ```
source ~/.bashrc
```
You can do so for every other file they may be set in (like /etc/bash.bashrc).

---

### Post by alzamabar on 2008-05-26
> **Ramses de Norre said:**
> That's for reconfiguring installed packages, which env variables would you like to refresh?
If they are set in ~/.bashrc you can run ```
source ~/.bashrc
```
You can do so for every other file they may be set in (like /etc/bash.bashrc).

I'd like to refresh the variables in /etc/environment. How could I do it?

Thanks.

M.

---

