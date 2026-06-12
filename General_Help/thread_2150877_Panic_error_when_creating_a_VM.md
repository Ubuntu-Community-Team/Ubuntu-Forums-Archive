---
title: "Panic error when creating a VM?"
date: 2013-06-02
forum: General Help
---

### Post by rayj00 on 2013-06-02
I am trying to create a VM in VMware Server 2.0.2. I downloaded the Ubuntu Deskop 12.04 twice
and get this same error:

panic early exception 0d rip 10:ffffffff8103fed4 error 0 cr2 0

Any ideas?

Thanks,

Ray

---

### Post by Cheesemill on 2013-06-02
VMware server stopped being supported several years ago, way before Ubuntu 12.04 was released.
[http://www.vmware.com/products/server/overview.html](http://www.vmware.com/products/server/overview.html)

Also the last supported OS for installing VMware server on was Ubuntu 9.04, I don't think it's going to be possible to get it working on any of the current versions of Ubuntu.

Is there any good reason for using VMware Server instead of one of the more recent virtualization solutions such as VirtualBox, KVM or VMware Workstation/Player ?

---

### Post by rayj00 on 2013-06-02
You misunderstand me.  I have VMware Server already installed on my Windows 7 host.
I am trying to create an Ubuntu VM.

---

### Post by Cheesemill on 2013-06-02
It doesn't matter whether you are running it on a Windows or Linux host, VMware Server doesn't support running 12.04 as a guest OS.

There aren't any current versions of Ubuntu that are supported by VMware Server, the last version that was supported was 9.04.

[http://www.vmware.com/resources/compatibility/search.php?deviceCategory=software&partner=271&productNames=7&testConfigurations=16&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc&testConfig=16](http://www.vmware.com/resources/compatibility/search.php?deviceCategory=software&partner=271&productNames=7&testConfigurations=16&page=1&display_interval=10&sortColumn=Partner&sortOrder=Asc&testConfig=16)

---

### Post by rayj00 on 2013-06-02
So I take it VMware vSphere Hypervisor 5 is the way to go?

---

### Post by Cheesemill on 2013-06-02
> **rayj00 said:**
> So I take it VMware vSphere Hypervisor 5 is the way to go?

It's definitely one of the options.

If the host machine is only going to be running VM's then you've got a few different solutions...
You can get free hypervisors from VMware, Microsoft and by using Linux (usually with KVM or XEN) although you pay for extra features with the first two.

If you want to use the machine as a desktop at the same time as hosting VM's then KVM, VirtualBox and VMware Player are free or you can pay for VMware Workstation, all of these except KVM will run on a Windows host machine.

You have to decide for yourself which one of these is the best depending on what it is you're trying to do. Do some research and test some out :)

---

