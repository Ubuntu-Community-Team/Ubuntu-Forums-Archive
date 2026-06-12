---
title: "How to use samba to share between Ubuntu and VM?"
date: 2007-11-15
forum: General Help
---

### Post by chunchengch on 2007-11-15
I have read some documents to try to use samba to connect Ubuntu and virtual machine, but it does not work, I wonder if it is possible to do this?

I can not find more informations about it, any help is highly appreciated.

Thanks!

---

### Post by mindwarp on 2007-11-17
You can definitely use samba between the VM and your host.  Sounds more like a networking issue to me.  You generally have two options, bridged and nat.  I have seen issues, depending on switches, where bridged might not work as expected.  But I have always been able to contact my nat VMs.   You can find out more about samba: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

As a personal preference, I just use SSH / SCP between vms.  If your VM isn't Ubuntu, you can download a program called 'WinSCP' that will allow you to scp files.

Good luck!

---

