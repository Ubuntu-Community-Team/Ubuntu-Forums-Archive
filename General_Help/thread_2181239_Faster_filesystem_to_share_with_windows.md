---
title: "Faster filesystem to share with windows"
date: 2013-10-17
forum: General Help
---

### Post by JaySeeJC on 2013-10-17
I'm dualbooting ubuntu 13.10 and windows 8.1. I have vmware 10 installed in windows, keeping the actual vms on a shared, majority of hard drive ntfs partition. I recently moved them to said partition, having decided to dualboot again to get some windows apps working. I've noticed though that since moving the vms to the large shared partition that they're crashing, and it seems ntfs-3g is just not fast enough to keep up. So I'm wondering, is there any filesystem I can use to share data between windows and ubuntu that's faster than ntfs and has native/driver support in windows? Preferably has journaling support and such, as it's my main data partition and i'd hate to lose anything on it.

---

### Post by nerdtron on 2013-10-17
Why would you put your VM hard drives in an ntfs partition? why not store them on you home folder by default?

---

### Post by Morbius1 on 2013-10-17
You lost me on the description of the problem.

You dual boot with Win8.
VMWare is installed on Win8
Your actual VM's are on a shared NTFS partition.

I'm not seeing where ntfs-3g is even coming into play here.

But to your final question:
> So I'm wondering, is there any filesystem I can use to share data  between windows and ubuntu that's faster than ntfs and has native/driver  support in windows? Preferably has journaling support and such, as it's  my main data partition and i'd hate to lose anything on it.         
I don't know of one.

---

### Post by Lars Noodén on 2013-10-17
Windows doesn't support any real file systems natively.  There might be some third party add-ons that allow at least some support of EXT.  Here is one, but I have no idea how much it does.
[http://www.paragon-software.com/home/extfs-windows/](http://www.paragon-software.com/home/extfs-windows/)

But with NTFS, the more you use it, the slower it gets, unless you frequently de-fragment it.

---

### Post by JaySeeJC on 2013-10-17
> **nerdtron said:**
> Why would you put your VM hard drives in an ntfs partition? why not store them on you home folder by default?
Because I'm trying to keep as much as possible on the partition, which takes up most of my disk and has the most room to store the hard drives as they grow.

> **Morbius1 said:**
> You lost me on the description of the problem.

You dual boot with Win8.
VMWare is installed on Win8
Your actual VM's are on a shared NTFS partition.

I'm not seeing where ntfs-3g is even coming into play here.

But to your final question:

I don't know of one.
Sorry. That was a tired post just before I went to bed last night. I have vmware installed on ubuntu. I'm storing the VMs currently on the ntfs partition, but something about ntfs-3g is causing it's cpu usage to max out and cause vmware's VM to crash. 

> **Lars Noodén said:**
> Windows doesn't support any real file systems natively. There might be some third party add-ons that allow at least some support of EXT. Here is one, but I have no idea how much it does.
[http://www.paragon-software.com/home/extfs-windows/](http://www.paragon-software.com/home/extfs-windows/)

But with NTFS, the more you use it, the slower it gets, unless you frequently de-fragment it.
Via a reddit post I've found the udf filesystem. It sounds promising, as it has native support under both windows and linux and POSIX permissions support. I'm currently looking into that.

---

### Post by Lars Noodén on 2013-10-17
If you meant UFS, it's not quite there yet:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268665](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268665)

at least not as of 2008 or so.  

I haven't tried XFS but Ubuntu does seem to support it.

---

### Post by JaySeeJC on 2013-10-17
Actually I do mean UDF.
Reddit post: [http://www.reddit.com/r/linux/comments/1omh0t/faster_filesystem_to_share_with_windows/](http://www.reddit.com/r/linux/comments/1omh0t/faster_filesystem_to_share_with_windows/)
Relevant AskUbuntu: [http://askubuntu.com/questions/27936/can-and-should-udf-be-used-as-a-hard-drive-format](http://askubuntu.com/questions/27936/can-and-should-udf-be-used-as-a-hard-drive-format)

---

