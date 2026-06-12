---
title: "Vmtools can't run on Ubuntu Edgy 6.10"
date: 2007-02-16
forum: General Help
---

### Post by helai on 2007-02-16
I installed  the VMware Workstation 5.5.3 on winxp ,and installed ubuntu6.1 2.6.17-10-generic on vmware
and instlled the vmware tools following the instruction

[http://www.howtogeek.com/howto/ubuntu/install-vmware-tools-on-ubuntu-edgy-with-vmware-553/](http://www.howtogeek.com/howto/ubuntu/install-vmware-tools-on-ubuntu-edgy-with-vmware-553/)
[http://mtnbike.org/blog/?p=26]("http://mtnbike.org/blog/?p=26")

but when run the command on the console,it shows the error message as below

```

```root@ridge:/tmp/vmware-tools-distrib# sudo chmod u+w /usr/bin/vmware-config-tools.pl 
root@ridge:/tmp/vmware-tools-distrib# sudo patch /usr/bin/vmware-config-tools.pl vmware-tools-config-5.5.2-patch-diff.txt 
patch: **** Can't open patch file vmware-tools-config-5.5.2-patch-diff.txt : No such file or directory 
root@ridge:/tmp/vmware-tools-distrib#```

```

,any advices

---

### Post by helai on 2007-02-16
yes,these information seems only refer the vmware5.5.2,but when I have installed the vmware5.5.3 tools ,I also can't get what I want 
Seemless mouse movement (between host and guest) 
Cut & Paste - Guest to Host 
even I have added vmware-toolbox on the System->Preferences->Sessions->Startup Programs,so it seems that vmware tools still can't fully suppor the ubuntu 6.1 

who has the best solution or who is succeed in installed vmware tools in ubuntu6.1 and runs well 

[https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29](https://help.ubuntu.com/community/VMware/Tools?highlight=%28vmware%29)

Thanks

---

### Post by Robin T Cox on 2007-02-16
I installed VMware Tools in Kubuntu Edgy 6.10 by following these instructions:

[http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html](http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html)

They run well in Windows 2000 Pro on VMware.

---

### Post by AaronD on 2007-03-19
Hello - I had the seamless mouse issue with 5.5.3 on an XP host with 6.10 as a guest.  I also had some video problems as well.

I solved them by loading the VMWare Tools from the latest Workstation 6 beta over top of the 5.5.3 VMWare Tools in the 6.10 VM.

If you need help getting it going, let me know.

Thanks!

---

