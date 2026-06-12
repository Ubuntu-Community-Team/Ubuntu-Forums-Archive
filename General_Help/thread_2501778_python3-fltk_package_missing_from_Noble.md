---
title: "python3-fltk package missing from Noble"
date: 2024-10-20
forum: General Help
---

### Post by robark on 2024-10-20
Hi, I am one of the developers of pyfltk (Python wrapper for FLTK GUI toolkit library). The library is in Debian Bookworm

[https://packages.debian.org/bookworm/python3-fltk](https://packages.debian.org/bookworm/python3-fltk)

It's also in Jammy and Oracular and Plucky but it's missing from Noble.

[https://launchpad.net/ubuntu/+source/pyfltk](https://launchpad.net/ubuntu/+source/pyfltk)

Is there a reason why it's not in Noble?
Is it still possible to add it to Noble?

Thanks

---

### Post by grahammechanical on 2024-10-20
> s there a reason why it's not in Noble?

This is just a user forum. You have given us a little information about this package but what you have given is much, much more than the Ubuntu maintainers pass on.

You might get a better response if you ask a question/post a bug on the Launchpad project web site.

Regards

---

### Post by 1fallen on 2024-10-20
> **robark said:**
> Hi, I am one of the developers of pyfltk (Python wrapper for FLTK GUI toolkit library). The library is in Debian Bookworm

[https://packages.debian.org/bookworm/python3-fltk](https://packages.debian.org/bookworm/python3-fltk)

It's also in Jammy and Oracular and Plucky but it's missing from Noble.

[https://launchpad.net/ubuntu/+source/pyfltk](https://launchpad.net/ubuntu/+source/pyfltk)

Is there a reason why it's not in Noble?
Is it still possible to add it to Noble?

Thanks

EDIT: Mine may have came along with my upgrade then:
```
apt policy  python3-fltk
python3-fltk:
  Installed: 1.3.9+repack-3
  Candidate: 1.3.9+repack-3
  Version table:
 *** 1.3.9+repack-3 500
        500 http://us.archive.ubuntu.com/ubuntu plucky/universe amd64 Packages
        100 /var/lib/dpkg/status

```

Are you sure about noble? [URL="https://linux-packages.com/ubuntu-24-04/package/python3-fltk"]https://linux-packages.com/ubuntu-24-04/package/python3-fltk



[/URL]

---

### Post by deadflowr on 2024-10-20
Looks like it suffered a build problem with Ubuntu:
[https://bugs.launchpad.net/ubuntu/+source/pyfltk/+bug/2058932](https://bugs.launchpad.net/ubuntu/+source/pyfltk/+bug/2058932)

---

