---
title: "Kubuntu Live CD can't mount partitions"
date: 2007-10-21
forum: General Help
---

### Post by joao82 on 2007-10-21
Hi.
I decided to move on to the newest release of Kubuntu because i was extremely satisfied with Feisty Fawn and thought that everything could only improve with Gutsy.

But there are many problems with Gutsy, and the one I would like to point out is that when I run the Live CD it fails to open my other partitions, so I can't access my data. Using Feisty I can mount all the partitions and see all the files, which is good in case I can't boot to an operating system on the hard drive, for backing up data.

I took some screen shots to show how Gutsy acts strangely.

[IMG]http://img140.imageshack.us/img140/7427/snapshot1pf2.png[/IMG]
here you can see that Gutsy is aware there are other partitions, and offers a double option on the right to mount the selected partition.


[IMG]http://img139.imageshack.us/img139/838/snapshot2ve1.png[/IMG]
this is the result of double-clicking a partition, or selecting "mount", only an error message on the bottom of the screen.
again, the menu on the right has all the options twice.


[IMG]http://img525.imageshack.us/img525/7152/snapshot3hw2.png[/IMG]
here, on another computer, exploring a usb pen drive. all the menu options show up twice.

This is all under Dolphin, but using Konqueror it's also impossible to mount the partitions.

Here's the output from the terminal, while browsing partitions:

```
ubuntu@ubuntu:~$ sudo dolphin
Error: "/var/tmp/kdecache-ubuntu" is owned by uid 999 instead of uid 0.
Error: "/tmp/ksocket-ubuntu" is owned by uid 999 instead of uid 0.
kio (KMimeType): WARNING: KServiceType::offers : servicetype trash not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype trash not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype system not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype system not found
ASSERT: "m_pendingMimetypeInfos.count() == 1" in /build/buildd/kdelibs-3.5.8/./kio/kio/kfilemetainfo.cpp (975)
Error: "/var/tmp/kdecache-ubuntu" is owned by uid 999 instead of uid 0.
Error: "/tmp/ksocket-ubuntu" is owned by uid 999 instead of uid 0.
Error: "/var/tmp/kdecache-ubuntu" is owned by uid 999 instead of uid 0.
ASSERT: "!name.isEmpty()" in /build/buildd/kdelibs-3.5.8/./kio/kio/kdirlister.cpp (969)
Error: "/var/tmp/kdecache-ubuntu" is owned by uid 999 instead of uid 0.




ubuntu@ubuntu:~$ sudo konqueror
Error: "/var/tmp/kdecache-ubuntu" is owned by uid 999 instead of uid 0.
Error: "/tmp/kde-ubuntu" is owned by uid 999 instead of uid 0.
Error: "/tmp/ksocket-ubuntu" is owned by uid 999 instead of uid 0.
Error: "/var/tmp/kdecache-ubuntu" is owned by uid 999 instead of uid 0.
Error: "/var/tmp/kdecache-ubuntu" is owned by uid 999 instead of uid 0.
Error: "/var/tmp/kdecache-ubuntu" is owned by uid 999 instead of uid 0.
Error: "/var/tmp/kdecache-ubuntu" is owned by uid 999 instead of uid 0.
Error: "/var/tmp/kdecache-ubuntu" is owned by uid 999 instead of uid 0.
Error: "/tmp/ksocket-ubuntu" is owned by uid 999 instead of uid 0.
ASSERT: "!name.isEmpty()" in /build/buildd/kdelibs-3.5.8/./kio/kio/kdirlister.cpp (969)

```

Aside from these problems, the Live CD doesn't run as good on my laptop. In the middle of the boot it exits the loading screen, turns black and then it's in text mode until the desktop shows up.
And it can't shut down properly.

None of this happens using the Feisty CD. And now I'm not so sure if I should install Gutsy on my pc.

---

### Post by joao82 on 2007-10-21
Could someone just tell me if Kubuntu Gutsy will automount partitions after I install it?
I don't know if the same is happening to others.

---

### Post by maxdevis on 2007-10-23
i have the same problem with the live cd with my external hdd.

---

### Post by noisemonkey on 2008-01-31
i experienced the same error on the kubuntu gutsy live-cd.
found this hint [http://jabasite.ej.am/blog/2008/01/21/kubuntu-gutsy-mount-error/]("http://jabasite.ej.am/blog/2008/01/21/kubuntu-gutsy-mount-error/")
worked for me.

---

