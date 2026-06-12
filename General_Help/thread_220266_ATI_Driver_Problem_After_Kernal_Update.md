---
title: "ATI Driver Problem After Kernal Update"
date: 2006-07-21
forum: General Help
---

### Post by rowanparker on 2006-07-21
Hello,
I had an error with the ATI Driver (see [here]("http://ubuntuforums.org/showthread.php?p=1269540")). And it was working fine until I updated the kernal. Now I get the error message I got in the first place (in the other thread). It's rather annoying because I can't even run Office :(.

Is there anyway way I can get it working?

Thanks, Rowan.

---

### Post by slimdog360 on 2006-07-21
When the grub loader starts perhaps you can just load an older kernal. I know its not a permanent solution but rather a quick fix. But at least its something.

---

### Post by rowanparker on 2006-07-21
Good idea, thanks.

That'll do for now but does anyone have any better fixes? Has this happened to anyone else?

Rowan.

---

### Post by arkangel on 2006-07-21
Hi  
 well  I have a  ati driver   for my X700 mobility radeon

any time i upgrade the kernel or  restricted modules    then  i have  to reinstall the drivers  

[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

I  was following the wiki for that part but never worked for me, but when i run the driver as it comes  it is like a charm  
have you tried to  reinstall the driver again ?

---

### Post by vem0m on 2006-07-21
[http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910) try that topic for newer cards 9500 up for less then that try [http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26](http://www.ubuntuforums.org/showpost.php?p=1108696&postcount=26)

hope this helps

---

### Post by geco on 2006-07-21
> **rowanparker said:**
> Hello,
I had an error with the ATI Driver (see [here]("http://ubuntuforums.org/showthread.php?p=1269540")). And it was working fine until I updated the kernal. Now I get the error message I got in the first place (in the other thread). It's rather annoying because I can't even run Office :(.

Is there anyway way I can get it working?

Thanks, Rowan.

maybe [this thread](http://ubuntuforums.org/showthread.php?t=213420) will help you.

---

### Post by geco on 2006-07-21
here is the quoting:
> **givré said:**
> A new kernel update (2.6.15-26) is available. Before upgrading and to not have the same problem as for the last update, it is recommanded to read this first

You can find the entire security notice there : [http://www.ubuntu.com/usn/usn-311-1](http://www.ubuntu.com/usn/usn-311-1)

In other words,

- To upgrade automaticly the linux-restricted-module, it's important to check that the metapackage linux-arch (where arch is the architecture of your current kernel) is install before upgrading (ie linux-386 for 2.6.15-25-386, linux-k7 for 2.6.15-25-k7 etc...check your currant kernel with 'uname -r')

- You will have to recompile all module/driver that you compiled for the previous kernel (ex: vmware, nvidia from their site...)

- If you need to recompile module or driver, and if you need the kernel headers for that, check also that you have the linux-headers-arch (where arch is the architecture of your current kernel) install.


If it's too late and you have problems at start-up, boot in recovery mode and install the kernel metapackage via apt-get:

- Check first your architecture
```
uname -r
```
- Install the metapackage
```
sudo apt-get install linux-arch #replace arch with your architecture
```

Have also a look at this: [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#WHAT_HAPPENS_IF_YOU_CHANGE_YOUR_KERNEL_OR_IF_YOUR_KERNEL_IS_UPDATED)

---

### Post by rowanparker on 2006-07-21
Thanks, I'll look into it and get back to you.

Rowan.

---

### Post by rowanparker on 2006-07-28
OK, it works fine now.

But now I get the little orange star in the system tray showing updates for the driver and control panel. Now I take it I don't want to update, if that's the case then how do I stop it being shown in the update manager?

Thanks, Rowan.

---

