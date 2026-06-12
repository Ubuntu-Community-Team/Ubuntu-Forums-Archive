---
title: "Kernel update after I manually installed later mainline kernel?"
date: 2017-03-15
forum: General Help
---

### Post by davaweb on 2017-03-15
Ubuntu 16.04.2
Installed with kernel 4.8.0-41
Manually updated to and running kernel 4.10.1-*

As above and 16.04 is running fine on kernel 4.10.1.

System updates shows my 'installed' kernel as 4.8.0-41 and wants to update it to a later 4.8.* kernel. It doesn't see that I am running kernel 4.10.1-*.

If I let it do this 'kernel update' presumably I will no longer be running kernel 4.10.1.

1. How can I 'tell' the system it is running kernel 4.10.1 and
2. how can I stop system updates doing what it thinks is a kernel update?
3. Why doesn't system updates know I'm running a later kernel than it is offering?

If updates had to offer a new kernel I would have expected it to offer kernel 4.10.2, the latest mainline stable release.

Thanks for your help.

---

### Post by #&amp;thj^% on 2017-03-15
> **davaweb said:**
> Ubuntu 16.04.2
Installed with kernel 4.8.0-41
Manually updated to and running kernel 4.10.1-*

As above and 16.04 is running fine on kernel 4.10.1.

System updates shows my 'installed' kernel as 4.8.0-41 and wants to update it to a later 4.8.* kernel. It doesn't see that I am running kernel 4.10.1-*.

If I let it do this 'kernel update' presumably I will no longer be running kernel 4.10.1.

1. How can I 'tell' the system it is running kernel 4.10.1 and
2. how can I stop system updates doing what it thinks is a kernel update?
3. Why doesn't system updates know I'm running a later kernel than it is offering?

If updates had to offer a new kernel I would have expected it to offer kernel 4.10.2, the latest mainline stable release.

Thanks for your help.

Take the updates to kernel 4.8.0-41 as they are fix's and security patches.
> 1. How can I 'tell' the system it is running kernel 4.10.1 and
Enter this in the terminal to show the running kernel:
```
uname -r
```
> 2. how can I stop system updates doing what it thinks is a kernel update?
Not Advisable due to security and stability. 
> 3. Why doesn't system updates know I'm running a later kernel than it is offering?
It's not a supported kernel for 16.04.... at least yet.
Your responsible now for upgrading the kernel that was hand-installed.
Upgrading to a mainline kernel is usually not a good idea

    Most of the basic information in this answer is from the Mainline Builds wiki

1. They are provided only for testing and are unsupported

    The mainline kernels are built from the latest unmodified "mainline" Linux kernel sources.
    The Ubuntu kernel team provides these only for testing and debugging purposes, to see whether issues have been fixed "upstream", i.e. by the Linux kernel developers.
    They are therefore not supported and must be used at your own risk; you can report possible bugs to kernel.org via kernel-oops, or if you want a faster solution, try posting to the Linux Kernel Mailing List

2. They will often break drivers, especially Nvidia/AMD and wireless (Broadcom)

    The mainline kernels do not include any Ubuntu-provided drivers or patches
    This means no binary drivers for graphics, wireless, etc. are provided
    If you try installing binary drivers downloaded directly from the manufacturers, there is a very good chance they will not work because the mainline headers may be incompatible.
        This will be especially true for non-LTS versions after 12.04 (12.10, 13.04, ...), because the mainline kernels are built using the last LTS toolchain (compilers, etc.), which is generally older than the toolchain on the latest non-LTS release.

3. You should only install these if you believe they may fix a critical problem you are having with the current kernel

    Newer kernels sometimes contain fixes for a hardware or filesystem problem you may have. For example, the internal HD4000 graphics on the latest Intel Ivy Bridge CPUs occasionally froze, a bug which was fixed in kernels 3.3.6 and newer.
    You can try installing a mainline kernel in these circumstances, and see if it helps your problem.
    If it does, you should consider upgrading to the latest Ubuntu+1 kernel instead, which does have binary drivers available for it.

4. If you install a mainline or other newer kernel, you can still choose to use your old (stable) kernel by selecting it at boot-time:

---

### Post by Frogs Hair on 2017-03-15
> Why doesn't system updates know I'm running a later kernel than it is offering You have installed a kernel from outside of the Ubuntu repository designated for your release and there is no mechanism in the update system to detect that automatically. 

> how can I stop system updates doing what it thinks is a kernel update You can lock a package version using the synaptic package manager

This may help to understand updates.
 [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

### Post by davaweb on 2017-03-15
Many thanks all,

By '1. How can I 'tell' the system it is running kernel 4.10.1' I meant 'how can I tell the system **it** is running ...' . I know I am because, as you say, I do uname -r.
But it appears I can't tell the system - and I know the caveats of running mainline kernels. 

What I hadn't grasped was why the system wanted to update the kernel for security etc - of course, thanks to your replies, I do now. THANK YOU :-)

I locked the 4.10.1 and went ahead with the updates. Installed without a problem and on restart uname -r still showed 4.10.1 - great.

Why am I using 4.10.1? Ryzen ...

Please know I **_very much appreciate_** all your help - deepened my understanding.

---

