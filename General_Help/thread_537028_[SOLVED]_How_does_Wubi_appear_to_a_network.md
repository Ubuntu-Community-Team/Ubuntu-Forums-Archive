---
title: "[SOLVED] How does Wubi appear to a network?"
date: 2007-08-28
forum: General Help
---

### Post by burgerearl on 2007-08-28
I work on a Department of Defense network, and more specifically, I'm only allowed to use specific hardware/software configurations. 

It's not really an issue if I don't connect to the network, but that's not really any fun....

I'm able to run Ubuntu using VMWare, because (I think) I'm still connecting to the network using Windows' ethernet adapter.

I'm guessing that Wubi won't work similarly, but wanted to post to make sure since I'm a little confused about it being a "windows program"

Thanks!

---

### Post by tuxcantfly on 2007-08-28
> I work on a Department of Defense network, and more specifically, I'm only allowed to use specific hardware/software configurations.

It's not really an issue if I don't connect to the network, but that's not really any fun....

I'm able to run Ubuntu using VMWare, because (I think) I'm still connecting to the network using Windows' ethernet adapter.

I'm guessing that Wubi won't work similarly, but wanted to post to make sure since I'm a little confused about it being a "windows program"

Thanks!

It should work identically to standard ubuntu. However, since you're using Ubuntu in a virtual machine, yes, it's connecting through Windows, while the Wubi-generated Ubuntu install will connect directly, like standard Ubuntu would. You might need to use Samba for some Windows networks; however, you might have less luck if the network has some kind of blocking for non-Windows systems; you could try just booting with a livecd and trying to connect to see if it's being blocked or allowed. Also, you might want to repost this question in the general Ubuntu forums (it affects all standard Ubuntu installs, not just Wubi-generated installs).

---

### Post by burgerearl on 2007-08-28
Thanks. This is what I suspected, but I wanted to make sure. The issue isn't that non-standard systems are blocked from the network, but rather not allowed, so I'd get in trouble for connecting Ubuntu directly.

Oh well. I'll be off this network in a year and then I can use whatever OS I want!

---

### Post by mike827 on 2008-04-27
Wubi installs the filesystem in a windows file which acts as a partition. ubuntu itself runs natively on the hardware (no virtual machine) the only difference is it uses the file as a partition. so it will connect to the DoD network as an UBUNTU MACHINE!!!! if you just download an ISO u can install it in a VMMACHINE using the same principal of a file as a partition, except it runs in the virtual machine rather than natively on the hardware.

---

