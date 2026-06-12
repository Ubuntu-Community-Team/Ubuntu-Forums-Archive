---
title: "Partioning problem - &quot;resize operation failure&quot;"
date: 2008-05-08
forum: General Help
---

### Post by killahsam on 2008-05-08
Basically I have windows xp home already installed... and I accidently disabled my kaspersky antivirus and DL'd a virus by accident.. so in an attempt to save my data I'm trying to install linux onto my system to clean up the windows partion.

Here is the problem I get to the 4th step and I use the top choice and give windows about 80% and ubuntu about 20% and I try to partion it...

I get this error "resize operation failure"  

My drive is in NTFS format, and once again I want to save my windows data... I Downloaded the newest version of ubuntu today so that is the one I'm using.

Anyone got any suggestions to get this installed without losing my windows?

---

### Post by bodhi.zazen on 2008-05-08
First you can do data recovery from a live CD without installing Linux.

You might want to look at a distro with antivirus and data recovery tools already included.

[http://www.knoppix.net/wiki/Security_Live_CD](http://www.knoppix.net/wiki/Security_Live_CD)

There are others as well ...

Second, most likely you need to boot to windows and defragment your disk.

---

### Post by killahsam on 2008-05-08
> **bodhi.zazen said:**
> First you can do data recovery from a live CD without installing Linux.

You might want to look at a distro with antivirus and data recovery tools already included.

[http://www.knoppix.net/wiki/Security_Live_CD](http://www.knoppix.net/wiki/Security_Live_CD)

There are others as well ...

Second, most likely you need to boot to windows and defragment your disk.
the virus I have won't let windows boot at all... not even in safemode, or any other mode. 

I'll have to hop on another computer to DL that file. I'm On my ps3 right now.

---

### Post by killahsam on 2008-05-08
bump

any thing else I can do guys?  If I put another Harddrive in my computer... load windows on that.... and change my other hdd with the virus to like drive D:\  could I run a virus scan on that then take the other hd out and put mine back in and would it work to remove the virus?

Or can I do this with the linux with out removing my windows data on my current hdd.. I read somewhere there is a problem with it reading NTFS drives or something.

---

### Post by bodhi.zazen on 2008-05-08
You could do that (pull the hard drive an mount it in another box). There is a risk the virus will spread ...

The other option, and IMO better, is to boot with that Knoppix CD as that will keep the windows virus from spreading.

Next step, either way, is to scan the hard drive and identify the virus. If it is not possible to remove, back up any non-infected files, wipe the hard drive, and re-install windows.

You can access NTFS drives from linux, read write, with no foreseeable problems. The linux driver is now quite mature. The tools you need are on that Knoppix CD.

---

### Post by killahsam on 2008-05-08
> **bodhi.zazen said:**
> You could do that (pull the hard drive an mount it in another box). There is a risk the virus will spread ...

The other option, and IMO better, is to boot with that Knoppix CD as that will keep the windows virus from spreading.

Next step, either way, is to scan the hard drive and identify the virus. If it is not possible to remove, back up any non-infected files, wipe the hard drive, and re-install windows.

You can access NTFS drives from linux, read write, with no foreseeable problems. The linux driver is now quite mature. The tools you need are on that Knoppix CD.

Okay thanks for the help... I'm on the demo of the linux right now...  I'm about to check the knoppix out :)

Which one do I use there is more than one choice...    * 1 Echelonlinux
    * 2 Helix
    * 3 INSERT
    * 4 Knoppix STD
    * 5 Local Area Security Knoppix
    * 6 Penguin Sleuth Kit

---

