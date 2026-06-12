---
title: "Dual data access with ubuntu/vista"
date: 2007-08-13
forum: General Help
---

### Post by gimpster123 on 2007-08-13
Hello,
I am a relatively new Ubuntu user.  I am wondering how i can access files I create in Ubuntu on Windows vista and vice versa.

thanks,
gimp

---

### Post by merlinus on 2007-08-13
```

sudo apt-get install ntfs-config

```then:

```

ntfs-config

```Tick appropriate boxes and restart.  Will give read-write access to ntfs windows partitions from ubuntu.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Install driver to read-write from windows to ubuntu.

-merlin

---

### Post by gimpster123 on 2007-08-13
excellent, thanks for the fast response

---

