---
title: "Files/directory of root user in personal /home directory"
date: 2014-12-15
forum: General Help
---

### Post by tigerjack89 on 2014-12-15
While looking at the /home folder, I found the followings


```
    drwx------  2 root        root         4096 mag 29  2013 .gvfs
    -rw-r--r--  1 root        root           58 ott 22  2013 .install4j
    drwxr-xr-x  2 root        root         4096 ott  1  2013 .rpmdb
    -rw-rw-r--  1 tigerjack89 tigerjack89    58 ott 22  2013 .install4j_jre

```

What they are? Can I switch them to my_user:my_group? 
Actually, I don't know if I can safely delete this folder and the previous .install4j file.

---

### Post by schragge on 2014-12-15
Usually, they are result of calling some programs with root privileges through *sudo*.

You can switch them to your user:group with
```

sudo chown -R $USER: .

```

As to the *.rpmdb* directory, see discussion on this bug: [lpbug]1069350[/lpbug]. It gets  created as a side-effect when calling old versions of dkms (before trusty, I believe) while installing any dkms-based kernel modules like NVIDIA/AMD proprietary video drivers or VirtualBox. It can be safely removed.

---

### Post by tigerjack89 on 2014-12-15
> **schragge said:**
> Usually, they are result of calling some programs with root privileges through *sudo*.

You can switch them to your user:group with
```

sudo chown -R $USER: .

```

As to the *.rpmdb* directory, see discussion on this bug: [lpbug]1069350[/lpbug]. It gets  created as a side-effect when calling old versions of dkms (before trusty, I believe) while installing any dkms-based kernel modules like NVIDIA/AMD proprietary video drivers or VirtualBox. It can be safely removed.
Thanks for your time.
Very precious info on .rpmdb, I was actually asking which program can use it. There are some __db files inside .rpmdb folder; do you think is it safe anyway?

Also, regarding other folders, quoting [http://askubuntu.com/a/561560/239377](http://askubuntu.com/a/561560/239377)

[LIST]
[*].[gvfs]("http://en.wikipedia.org/wiki/GVFS") is a virtual file system for gnome. Leave this as it is; mess with it and your system probably (most likely) will fail to work as intended.
[*].install4j is a java installer builder. Can be removed but it will depend on why you installed it and if you still need it.
[/LIST]

---

### Post by schragge on 2014-12-15
Even if you installed some rpm packages with [alien]("http://manpages.ubuntu.com/manpages/utopic/en/man1/alien.1p.html") they were converted to debs in the process anyway. So, yes it can be completely removed. It gets created anytime rpm is called either directly by you (e.g. when inspecting contents of an rpm package) or indirectly by some tool like alien or dkms.

And I was wrong assuming that the unnecessary creating of .rpmdb was fixed in trusty. Even the latest dkms version in vivid still queries rpm after each kernel upgrade and thus creates this directory if it doesn't already exist. What was actually fixed in raring (not in trusty) is creating /~/.rpmdb when running rpm as root. You can get rid of it if you uninstall rpm. With rpm not available dkms resorts to [uname]("http://manpages.ubuntu.com/manpages/utopic/en/man1/uname.1.html") when querying kernel version and architecture.

---

