---
title: "Partition Size vs RAM...do both affect speed, or just RAM?"
date: 2015-12-17
forum: General Help
---

### Post by Keiva on 2015-12-17
Hallo,
I am running Ubuntu 14.04 & Win10 in dual boot.  I didn't use Wubi.

K, that part's done.  So, I'm having speediness issues in Ubuntu, in that it's sssssslllllloooooowwwwwww.  If I allocate more space to its partition, will that in turn allow more RAM, or are RAM and partition disc size unrelated?  If they aren't related in that way, do I have to allow more RAM to each individual application that lags?  I didn't have speed problems before installing Ubuntu, and am considering moving Win into VirtualBox--could that help my speed?

tyvm!
K

---

### Post by QIII on 2015-12-17
It woud be helpful if you would provide the specification of your machine.

RAM and disk storage are two entirely different things.  RAM is a container for what you are working on right now.  It is handled by a completely different hardware component from your disk.

An analogy (remember that analogies are seldom perfect) is this:

RAM is your kitchen sink.  It holds the water you are working with right now.

Disk storage is like a reservoir.  It holds water you may or may not work with later.

When you are done with the water in your sink and drain it, some water is pumped back to the reservoir and some is flushed, never to be seen again.

Your sink is now empty (unless there is something else in the sink you are working on right now.)

In general, you do not assign the amount of RAM dedicated to any task.  The operating system does.  Programmers can reserve some memory in their design, but you don't usually have access to the source code to change and compile it unless you are yourself a software developer or otherwise knowledgeable.

---

### Post by grahammechanical on 2015-12-17
Changing partition size will have no effect at all.

Getting a hard drive with a faster data transfer rate will speed up application loading times.

All applications and data used by an application will load into computer memory (RAM) and run from it. So, having fast RAM chips will have an effect. As will having enough RAM to do away with the need for the OS to swap data into & out of the swap partition on the hard disk as we open and use more and more applications.

There is one item of hardware that can have a good or bad effect on the user experience and that is the graphic adapter or video card. Is it capable of running modern Linux desktop environments that require 3D rendering to be done by the graphic adapter? Does the graphic adapter have a sufficient amount of its own memory to do fast 3D rendering?

If we install Ubuntu and the graphic adapter is not capable of running Ubuntu's Unity 3D user interface than a video driver is used called llvmpipe that tries to give an approximation of Unity 3D. 
This allows the installation to complete and the user to get a working desktop. But even on graphic adapters that can run Unity 3D llvmpipe often seems slow.

This command will tell you if you have a video adapter capable of running Ubuntu with the Unity user interface.

```
/usr/lib/nux/unity_support_test -p
```

You should see something like this
> 
graham@sdb7-Dev:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GT 220/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 340.96

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

Regards.

---

### Post by oldos2er on 2015-12-17
Moved to General Help.

---

### Post by Keiva on 2015-12-21
> **grahammechanical said:**
> 
Getting a hard drive with a faster data transfer rate will speed up application loading times.


That's what I was looking for.  Thank you!

---

