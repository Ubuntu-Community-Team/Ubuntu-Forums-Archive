---
title: "Windows SSH terminal that supports using GUI applications"
date: 2007-05-14
forum: General Help
---

### Post by rscott5 on 2007-05-14
Hi everyone,

I'm looking for a Windows application that will let me SSH into my Ubuntu machine and run applications that use a GUI, not just ones that run through the terminal. I'm pretty sure that I've seen one, I just can't remember the name and it's on the tip of my tongue so I figured I would ask everyone here. Thanks a lot for your help.

---

### Post by dfreer on 2007-05-14
you'll need a remote desktop program really. there are some that use SSH to encrypt the data, so maybe that is what you are thinking of. umm check out this link:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_connect_into_remote_Ubuntu_desktop_via_Windows_machine](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_connect_into_remote_Ubuntu_desktop_via_Windows_machine)
that might work, but i dunno about ssh encryption, you probably need to do ubuntu > ubuntu with XDMCP to do that

---

### Post by rscott5 on 2007-05-14
> **dfreer said:**
> you'll need a remote desktop program really. there are some that use SSH to encrypt the data, so maybe that is what you are thinking of. umm check out this link:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_connect_into_remote_Ubuntu_desktop_via_Windows_machine](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_connect_into_remote_Ubuntu_desktop_via_Windows_machine)
that might work, but i dunno about ssh encryption, you probably need to do ubuntu > ubuntu with XDMCP to do that

That'll work, thanks a bunch.

---

### Post by Hossie on 2007-05-15
There's also a Xserver for Windows, called [Xming](http://en.wikipedia.org/wiki/Xming). In combination with Putty you can use XDMCP from a windows client.

---

### Post by dfreer on 2007-05-15
> **Hossie said:**
> There's also a Xserver for Windows, called [Xming](http://en.wikipedia.org/wiki/Xming). In combination with Putty you can use XDMCP from a windows client.

nice! gonna hafta try this out, and it says it can run off a USB flash drive, awesome!

---

