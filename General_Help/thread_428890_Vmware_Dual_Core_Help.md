---
title: "Vmware Dual Core Help"
date: 2007-04-30
forum: General Help
---

### Post by Skerit on 2007-04-30
I'm currently running the beta of the vmware workstation (version 6).

In your virtual machine settings you can choose how many cores you want to use, but when I select 2 cores vmware says my host computer doesn't have 2 cores....

I haven't found any information on this problem anywhere, and I'm completely stuck. And, yés, I DO have a Dual Core processor...

---

### Post by veloce on 2007-04-30
> **Skerit said:**
> I'm currently running the beta of the vmware workstation (version 6).

In your virtual machine settings you can choose how many cores you want to use, but when I select 2 cores vmware says my host computer doesn't have 2 cores....

I haven't found any information on this problem anywhere, and I'm completely stuck. And, yés, I DO have a Dual Core processor...

What version of Ubuntu are you using?  Does it recognise your machine as dual core?

However, my recommendation is not to set up the vm as dual core.  I am using vmware server (so YMMV) but vms set up as dual core run like dogs.  It seems to be better to let ubuntu and vmware manage the dual core and run the vm as single core.  Both processors seem to get used for the vm more efficiently than the host (admitedly winxp) can.

---

### Post by zPacKRat on 2007-04-30
> **veloce said:**
> What version of Ubuntu are you using?  Does it recognise your machine as dual core?

However, my recommendation is not to set up the vm as dual core.  I am using vmware server (so YMMV) but vms set up as dual core run like dogs.  It seems to be better to let ubuntu and vmware manage the dual core and run the vm as single core.  Both processors seem to get used for the vm more efficiently than the host (admitedly winxp) can.

What Veloce stated is true, every single threaded request will make the "unused" core inaccessable by other threads. This is a shortcomming of VMware. so unless your running a multi threaded app you will see no advantage.

---

### Post by Skerit on 2007-05-01
Ohw, ok. That's kind of confusing, another thread stated that when you activated the virtual dual core option, everything would speed up significantly... Oh well.

It actually is a multi threaded application, I believe, Adobe Premiere Pro.
And Ubuntu (Feisty) does discover my Dual core processor, which makes it even more strange.

---

### Post by zPacKRat on 2007-05-01
There was an update released yesterday for VMware server that may address this issue. It could also be a  matter of the VMware not yet supporting your CPU, if its a new processor. Also I enabled dual cores on a Vista VM running my Opteron 165 box and it added the second core to the HAL. So it does work. And by enabling the second core you will do much to slow down Ubuntu while the VM is running, however you should see an increase in VM performance.

---

### Post by veloce on 2007-05-01
> **Skerit said:**
> Ohw, ok. That's kind of confusing, another thread stated that when you activated the virtual dual core option, everything would speed up significantly... Oh well.

It actually is a multi threaded application, I believe, Adobe Premiere Pro.
And Ubuntu (Feisty) does discover my Dual core processor, which makes it even more strange.

My point is that, in my limited experience, Ubuntu does SMP better than windows.  Watching system monitor while a vm is working hard shows both processors being used and load moving from one to the other.  When running a windows vm on a windows host under vmware, one processor gets allocated to the vm and that's it.

---

