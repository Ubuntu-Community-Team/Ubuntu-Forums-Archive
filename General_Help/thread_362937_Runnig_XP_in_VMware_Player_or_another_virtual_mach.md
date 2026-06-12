---
title: "Runnig XP in VMware Player or another virtual machine"
date: 2007-02-16
forum: General Help
---

### Post by HippyVanMan on 2007-02-16
I run ubuntu linux, obviously, but I also run windows XP pro sp2 on another of my machines hard drive partitions (NTFS), I would like to run a windows xp pro sp2 virtual machine in ubuntu so as I can use certain windows programs (and no, don't offer wine to me as an alternative) but instead of using an image of xp i'd like to just be able to use the existing xp install, which is on an NTFS partition which ubuntu can read (but not write - which I assume will be necessary to set if this can work). I ask simply, is it possible to do this? And if so, how? 

Oh, I'm not out to necessarily do this with VMware, I'll do it with any  virtual machine I can.
Thank you for any help you can give me.

---

### Post by AusIV4 on 2007-02-16
Is it possible to boot a Windows partition in VMWare? Yes.
Is it possible to get past the login screen? No.

I attempted this a few weeks ago, and found that Windows recognizes the different hardware setup and wants you to authorize your computer again. If you do that, you won't be able to reboot to the partition anymore. There are some hacks that are supposed to circumvent that issue, but I wasn't able to get them working. Ultimately, I installed another copy of Windows, figuring I'd use the 30 day trial, then maybe transfer my license to the VM, but it turns out Windows doesn't count down the 30 days except when the VM is actually running.

Whatever that's worth.

---

### Post by HippyVanMan on 2007-02-16
Any chance of links to these hacks? Or at least more restricted search terms than general ones?

---

### Post by tansu on 2007-02-16
is it what you re lookin for:
[Convert Physical Machines to Virtual Machines]("http://www.vmware.com/products/converter/")

---

### Post by HippyVanMan on 2007-02-16
No, but thanks anyway. I don't want to convert my xp system to an OS image, I want to use it as is, inside my virtual machine.

---

### Post by irw on 2007-02-20
I don't know if this will work, but Blackmh says ["Running existing Windows installation on Ubuntu is piece of cake"]("http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html") on his site.


I'm just running through a full backup before trying it for myself ... ;)

---

### Post by jamesjtucker on 2007-02-20
I havent tried this yet, but others have reported this method to work:
[http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm](http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm)

Is that what you are looking for?

---

### Post by veloce on 2007-02-21
> **HippyVanMan said:**
> Any chance of links to these hacks? Or at least more restricted search terms than general ones?

Those hacks are ways of illegally using windows - it wouldn't be appropriate to broadcast that sort of thing here.  Remember that windows is not free (as in speech) software.  That's why we use Ubuntu!

That said, the windows authentication software is rather variable.  I've had windows vms move from one server to another without problem one time and no dice another.  (NB: each of these vms had a valid license from MS!)  Another time, altering the memory on a vm stopped it working.

I don't think that what you are trying to do conflicts with the license agreement. So what I would suggest is to try and create a vm with as close a virtual hardware configuration as your physical install.  It's rather involved, but what I would try is start by making a virtual copy of the physical system - this will have hardware settings as close as possible to the physical.  Then change the hard drive of that vm to the physical hard drive.

---

