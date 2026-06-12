---
title: "puzzled by references to click-ubuntu-sdk-14.10-i386 in /var/lib/schroot/"
date: 2015-03-31
forum: General Help
---

### Post by dragonfly41 on 2015-03-31
Recently I thought I might *experiment* with Ubuntu SDK for app development on Ubuntu 14.04 .. 
[https://developer.ubuntu.com/en/start/ubuntu-sdk/installing-the-sdk/](https://developer.ubuntu.com/en/start/ubuntu-sdk/installing-the-sdk/)
but quickly uninstalled after realising that SDK requires Ubuntu 14.10

......

My Ubuntu 14.04 desktop continues to work for development but is running out of head room in a **50  GB** partition .. 2.5 GB left .. which is why I started looking inside /var and other folders to jettison files.

I've just now noticed references to **click-ubuntu-sdk-14.10** filesystems in /var/lib/schroot/

I'm surprised that total occupied space in this directory /var/lib/schroot/ is ...  **37.5 GB**.

**/var/lib/schroot/chroots**
click-ubuntu-sdk-14.10-i386       ** 1.1 GB** in size

**/var/lib/schroot/mount**
click-ubuntu-sdk-14.10-i386-5ad9603a-95bc-4ac9-bc6b-b8c8542b02b2        **16.9 GB** in size (looks like / filesystem copy)
click-ubuntu-sdk-14.10-i386-ucca-1000-{6286474c-ee91-4673-8a37-72731f90b276}        **16.9 GB** in size (looks like / filesystem copy)

**/var/lib/schroot/session**
click-ubuntu-sdk-14.10-i386-5ad9603a-95bc-4ac9-bc6b-b8c8542b02b2                         **1.2 KB**
click-ubuntu-sdk-14.10-i386-ucca-1000-{6286474c-ee91-4673-8a37-72731f90b276}       **1.3 KB**
[B]
/var/lib/schroot/union/overlay/[/B]   two more references to click-ubuntu-sdk-14.10    **148 MB**
**/var/lib/schroot/union/underlay/**    two more references click-ubuntu-sdk-14.10     **1.1 GB**
**/var/lib/schroot/union/unpack/**      empty

...

My questions:  How can I safely recover this space .. or rather .. how to safely purge click-ubuntu-sdk-14.10-i386 and any sessions?

I have read this ...

[http://manpages.ubuntu.com/manpages/maverick/man7/schroot-faq.7.html](http://manpages.ubuntu.com/manpages/maverick/man7/schroot-faq.7.html)

But why such large filesystems left following a brief installation of Ubuntu SDK then immediately uninstalling?
The schroot content appears to replicate my Ubuntu 14.04 / filesystem.
i.e. bin, boot, dev, etc, home, lib. media .. through to .. usr, var.

---

### Post by grahammechanical on 2015-03-31
> [COLOR=#333333][FONT=Ubuntu]The Ubuntu SDK is available for Ubuntu 14.04 (Trusty) onwards.[/FONT][/COLOR]

Keep in mind the fact that the main purpose of the Ubuntu SDK is to get people writing apps for the Ubuntu phone store. And the Ubuntu phone OS is built on the Ubuntu 14.10 code. That is where the references to 14.10 come from. We need a lot of 14.10 code to write those apps.

Applications and libraries in Ubuntu are packaged in the debian package format. The Ubuntu developers have evolved the debian package format into the Click package format. It is called "Click" because the SDK will allow a developers to submit their app for acceptance into the phone app store by a one click method. Apparently this is so much easier than doing debian packaging. So, the SDK comes with all the necessary libraries for the Click packaging system.

How did you install the SDK? Through the PPA? How did you uninstall the SDK? Did you use the ppa purge command? That command should remove all the packages that came from the PPA.

Regards.

---

### Post by dragonfly41 on 2015-04-01
Thanks for the information.

I remember going to this site to install Ubuntu SDK  ...

[https://developer.ubuntu.com/en/start/ubuntu-sdk/installing-the-sdk/](https://developer.ubuntu.com/en/start/ubuntu-sdk/installing-the-sdk/)

but when I started to install there was extensive activity seen in the terminal and I decided to abandon the installation
before completion.

I may have then uninstalled ubuntu-sdk through Synaptic Package Manager.
I have used Synaptic Package Manager to hunt for references to ubuntu-sdk and they are not installed.
Purging ubuntu-sdk at this stage has no effect since no package is found.

...

I've now read more about chroot.

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

> 
Basic Concepts
A  chroot is basically a special directory on your computer which prevents  applications, if run from inside that directory, from accessing files  outside the directory. [COLOR=#ff0000]In many ways, a chroot is like installing another  operating system inside your existing operating system. [/COLOR]
Technically-speaking, chroot temporarily changes the root directory (which is normally /) to the chroot directory (for example, /var/chroot). As the root directory is the top of the filesystem hierarchy, applications are unable to access directories higher up  than the root directory, and so are isolated from the rest of the  system. This prevents applications inside the chroot from interfering  with files elsewhere on your computer. 
Note that it is possible for software from outside the chroot to access files inside the chroot. 


So presumably Ubuntu-SDK set up these chroots?

This is what worries me .. i.e. what are the implications of deleting /var/lib/schroot contents?

> 
In addition, by using schroot then all binds are engaged and removed automatically at chroot enter and exit. This is important to minimize accidental erasures of data.[COLOR=#ff0000] Thus, I think in a basic help page like this to warn users not to erase/delete/trash_can an entire chroot or entire chroot directories until chroot is exited (and all binds removed).[/COLOR] For schroot, all automatically created binds will be removed on exit and accidental erasure of entire /home (often heard about) can be minimized. (It seems either people forget or don't comprehend bi-directional nature of mount --bind.) 


I then found this post in AskUbuntu.

[http://askubuntu.com/questions/594686/removing-chroot-done-by-ubuntu-touch-sdk](http://askubuntu.com/questions/594686/removing-chroot-done-by-ubuntu-touch-sdk)

> 
i sussed it i removed 
/etc/schroot/chroot.d/-ubuntu-sdk* /var/lib/schroot/chroots/-ubuntu-sdk*
rebooted and problem sorted :)
thanks wayne :)


And sure enough in my /etc/schroot/chroot.d I find ...

click-ubuntu-sdk-14.10-i386

So .. can I safely just delete 
/etc/schroot/chroot.d/-ubuntu-sdk* /var/lib/schroot/chroots/-ubuntu-sdk*
without impacting on my main filesystem?

---

### Post by dragonfly41 on 2015-04-17
*boomp ...*

I have to resubmit my question.

The short story is that I tried to install Ubuntu SDK .. freaked out at the long activity on terminal .. ended the installation prematurely .. and now I have unwanted mounts which are in effect a "jail" operating system within my main operating system.  This has gobbled up disk space and I now need to safely unmount these unwanted chroots.

I did an experiment and if I delete a test file in /var/lib/schroot/mount/click-ubuntu-sdk-14.10-i386-5ad9603a-95bc-4ac9-bc6b-b8c8542b02b2 .. it deletes the file in my parent os.  

So the "jail" os is binding to my host os and I can't just purge /var/lib/schroot.

Here is the output of running **df**

```

:~$ df

Filesystem                  1K-blocks     Used Available Use% Mounted on
/dev/sda8                    50264772 47211720    476668 100% /
none                                4        0         4   0% /sys/fs/cgroup
/dev                          1475340       12   1475328   1% /var/lib/schroot/mount/click-ubuntu-sdk-14.10-i386-5ad9603a-95bc-4ac9-bc6b-b8c8542b02b2/dev
tmpfs                          296992     1216    295776   1% /run
none                             5120        4      5116   1% /run/lock
/run/shm                      1484952      164   1484788   1% /var/lib/schroot/mount/click-ubuntu-sdk-14.10-i386-5ad9603a-95bc-4ac9-bc6b-b8c8542b02b2/run/shm
none                           102400       68    102332   1% /run/user
click-ubuntu-sdk-14.10-i386  50264772 47211720    476668 100% /var/lib/schroot/mount/click-ubuntu-sdk-14.10-i386-5ad9603a-95bc-4ac9-bc6b-b8c8542b02b2
click-ubuntu-sdk-14.10-i386  50264772 47211720    476668 100% /var/lib/schroot/mount/click-ubuntu-sdk-14.10-i386-ucca-1000-{6286474c-ee91-4673-8a37-72731f90b276}


```

So how do I _safely_ purge the schroot references .. leaving just /dev/sda8.

I only need the mount on /dev/sda8 (my Ubuntu 14.04).
I do have some other /dev/sda* partitions but I have unmounted those (1, 2, 5, 10).

---

### Post by dragonfly41 on 2015-04-18
Finally succeeded in researching and tidying up spurious schroot mounts.

schroot -a -e

I've seen other threads with similar questions.

My note.  Beware installing ubuntu sdk unless you really know what you're doing. I dived in without researching first.

Here is one (untried) script I found for tidying up schroot sessions.

[http://web.mit.edu/andersk/Public/clean-schroots](http://web.mit.edu/andersk/Public/clean-schroots)

---

