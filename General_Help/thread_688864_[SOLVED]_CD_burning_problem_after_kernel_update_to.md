---
title: "[SOLVED] CD burning problem after kernel update to 2.6.22-14.51"
date: 2008-02-05
forum: General Help
---

### Post by tramir on 2008-02-05
I'm using Gutsy and have a TSSC CDRW/DVD unit. It used to be that I could burn CDR's just fine. I had some problems reading overburnt CDs -- most of the times Ubuntu just refuses to read the extra sectors, but sometimes it mounts ok.

After yesterday's kernel update to 2.6.22-14.51, I started having trouble. I'm still able to burn CDs at full speed (24x in the case of this old unit), but Ubuntu just refuses to read them. It mounts the drive, reads the allocation table and displays the list of files, but can't access any of them. dmesg reports "Buffer I/O error on device sr0" on a lot of logical blocks. The CDs work fine on a Windows machine, so I'm guessing it has to be a kernel problem... I tried to downgrade, but the problem is still there. The only workaround was to burn the CDs at 4x, in which case things work, but I don't think that that's supposed to be like this. Anybody care to have a suggestion? If you need any more information, I'd be happy to oblige.

Don't think this makes a difference -- the burning was done with K3b.

TIA

---

### Post by tramir on 2008-02-07
Update: now I have problems even when burning at 4x. Some of the files (at the end of the CD) are unreadable. Again, the CDs work just fine in Windows. I checked Launchpad for bugs related to this, but nothing really fits my case. Should I file a bug? Anybody has any idea?

---

### Post by tramir on 2008-02-07
OK, I finally managed to figure it out and wanted to let other people know, if they have the same problem. It seems that it all goes back to an old error in the kernels (?) with reading the last sectors of CDs. The solution, which I found at [http://www.troubleshooters.com/linux/coasterless.htm](http://www.troubleshooters.com/linux/coasterless.htm), is to add some padding to the last track (yes, the problem and the solution were identified since 2005!!). The relevant command line options for cdrecord/wodim are "**padsize=63s -pad**". Apparently this never hurts, even if you don't have the bug I have...

In K3b (which is what I use), this is done by going to Settings - Configure K3b... - Programs - User Parameters and add "padsize=63s -pad" to "**cdrecord**". I guess Brasero, GnomeBaker and the other should have a similar option to specify additional command line arguments? 

Now everything works fine, even burning at full speed. I didn't check overburned CDs yet, but my guess is that the same principle would apply to them too. And yes, it is a Linux bug :( Hope they solve it soon...

*Edit, July 8, 2008*: It works with overburned CDs too...

---

