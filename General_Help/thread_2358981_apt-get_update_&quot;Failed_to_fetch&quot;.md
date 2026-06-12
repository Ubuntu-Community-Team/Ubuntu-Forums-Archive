---
title: "apt-get update &quot;Failed to fetch&quot;"
date: 2017-04-19
forum: General Help
---

### Post by neanderslob on 2017-04-19
Hi All,

I'm having an issue in running a *sudo apt-get update*.  I'm getting the following error message

```

E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/xenial-security/main/dep11/icons-64x64.tar  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_xenial-security_main_dep11_icons-64x64.tar.gz - open (13: Permission denied) [IP: 91.189.88.162 80]

```

Any idea as to what might be causing this or how I might resolve it?

Thanks in advance.

---

### Post by RobGoss on 2017-04-19
Hello and welcome, go to **Software  & updates**, choose **other software, ** unchecked the failed URL you see when you run your updater then try updating your system again and see how it goes

---

### Post by neanderslob on 2017-04-19
Thanks for the reply.  There really isn't any "other software" checked, unless I'm misunderstanding you.  The URL that seems to be causing the problem is security.ubuntu.com.

---

### Post by RobGoss on 2017-04-19
Did you try changing your download source?

---

### Post by RobGoss on 2017-04-19
You can also try running the following commands

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by neanderslob on 2017-04-19
Changing the download source seems to have fixed it.

---

### Post by RobGoss on 2017-04-19
> **neanderslob said:**
> Changing the download source seems to have fixed it.

Thanks great so we learned something for next time sometimes it's a easy fix, I find after using Ubuntu for sometime anything can be fixed

This forum is a book of knowledge

If you have solved your issue you can mark this threat as solved, use the Threat tool tab at the top of this post

---

