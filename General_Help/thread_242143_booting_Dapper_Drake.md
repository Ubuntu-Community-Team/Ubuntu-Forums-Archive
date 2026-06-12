---
title: "booting Dapper Drake"
date: 2006-08-23
forum: General Help
---

### Post by bobanshirl on 2006-08-23
I have Dapper installed together with Windows XP.I was able to select either on bootup. The other day something happened and Windows would not boot but selecting Dapper went okay.I thought I would be clever and I reinstalled Windows XP.Trouble is when I switch on now it goes straight into windows with no option to select Dapper.Can someone tell me if it is possible to correct this or have I got to reinstall Dapper again.I hope I dont have to as I have got it going very well at the moment or I did have.Any help would be appreciated.

---

### Post by Irony on 2006-08-23
You need to reinstall the grub bootloader, you can use the install disc for this.

For example use the Dapper live CD then find grub in synaptic and install it.

---

### Post by bobanshirl on 2006-08-23
I have tried what you said but it came up and said it couldnt find it or words to that effect.DONT YOU HAVE TO BE ON LINE TO DO THIS.

---

### Post by Irony on 2006-08-23
See this (it depends what CDs you have);

[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

or

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Personally I do from an old Hoary CD this;

Boot from the install ubuntu CD and at the boot prompt type;

[PHP]
rescue[/PHP]

Go to a  mount points e.g. ubuntu is on hda5;

[PHP]dev/disc/disc0/part5[/PHP]

At the sh-3.00# prompt type;

[PHP]grub-install /dev/hda[/PHP]

After being returned to the prompt, do;

[PHP]#umount /dev/hda5
#reboot[/PHP]

You don't need to be online.

---

