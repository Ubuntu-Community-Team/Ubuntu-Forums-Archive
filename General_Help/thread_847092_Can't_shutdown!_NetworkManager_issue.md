---
title: "Can't shutdown! NetworkManager issue"
date: 2008-07-02
forum: General Help
---

### Post by JustGus on 2008-07-02
I'm a completely noob and installed Hardy a couple nights ago, but have run into problems. After upgrading some software I'm now unable to shutdown my machine. After exiting the GNOME GUI, the black screen shows the following and stays there, failing to complete the shutdown of the machine:

------------------------
NetworkManager: <WARN> nm_signal_handler(): Caught signal 15, shutting down normally.

NetworkManager: <info> Caught termination signal

NetworkManager: <debug> [1214920380.164088] nm_print_open_socks(): Open Sockets List:

NetworkManager: <debug> [1214920380.164191] nm_print_open_socks(): Open Sockets List Done.

NetworkManager: <WARN> nm_hal_deinit():libhal shutdown failed - Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
------------------------
Any suggestions on how to fix this would be great.

Also, in case like this, I'm unable to find any solution other than pulling the plug to shut down. Any other suggestions of what to do to better power down would be welcome!

Cheers,

Gus

---

### Post by Gunman1982 on 2008-07-02
Somewhere I have already seen this, even in this forum. For a workaround: If you reboot your computer that should work fine or? Do you use the realtime kernel? To find out you can open a console and type 'uname -a'.

---

### Post by kdcoetzee on 2008-07-02
i get the same error.
Some peoples computers react differently than others.
mine slows my shutdown down with a few second.
I didn't get it fixed. 

I think the message handler stops before network manager. then network manager still tries to access it but with no success.

Is this on a notebook with wireless ?

---

### Post by JustGus on 2008-07-02
Hi - 
In answer to your questions...
- I can reboot the machine, but can't get it to simply shutdown.
- when I type in 'uname -a', I get...
Linux server-desktop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
- The machine is a miniITX box running Hardy
Any ideas on how to fix?  And is yanking the plug detrimental? (I know on Windows it's supposed to be very bad, whereas on Mac's it's not quite such a grave offence)

Cheers,
Gus

---

### Post by chrisccoulson on 2008-07-02
Network Manager might be a red herring. If I turn off usplash, I'm fairly sure I see those errors from Network Manager as well. It doesn't halt the shutdown of the machine and I have no issues with shutting down.

---

### Post by JustGus on 2008-07-03
I hear you...but if it isn't a red herring?  For the moment it's all I've got to go on!

---

### Post by jimv on 2008-07-03
Time to troubleshoot then!  Install WICD instead of NetworkManager and see if the issue persists.  If it's not a problem with NM, then the stalling should still occur.

---

### Post by lil_elvis2000 on 2008-07-03
I get similar. I think it is because the dbus message manager shutsdown as one of the first services and networkmanager still tries to access it. Wouldn't worry.

Networkmanager spews all sorts of messages. When I switch my KVM, when I add a disk to my RAID..very clumsy piece of software. I'm not impressed with it at all.

---

### Post by kdcoetzee on 2008-07-04
The problem is not with Network Manager. One of my work colleague have the same problem(actually bit worse) we installed wicd, and it worsen it.

In the end we saw that [network manager 0.7.0]("http://ubuntuforums.org/showthread.php?t=848135") is the most stable but the error still persists.

The problem is something to do with what lil_elvis2000 and I said.

---

### Post by brujoand on 2008-07-31
adding "noapm" at the end of boot options in grub menu.lst should fix this

---

