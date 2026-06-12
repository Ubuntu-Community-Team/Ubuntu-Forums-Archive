---
title: "hibernation in gutsy"
date: 2008-01-26
forum: General Help
---

### Post by stubblepoo on 2008-01-26
i know this has been explained elsewhere but i dont understand what they're are trying to say. basically when i hibernate it goes through the motions but it blacks out then immediately the log-on screen comes back so it's not really hibernated, help please!

---

### Post by diaa on 2008-01-26
Sometimes hibernation in Ubuntu doesn't work with certain hardware, I suggest that you try s2disk which is known to have much less problems.
You need only to follow the part titled *How to try uswsusp*, the 2nd part is optional, if you face problems with the guide, tell me and I'll try to help.

[How to use s2disk]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/")

---

### Post by stubblepoo on 2008-01-28
i tried this a while back and it dind't work, i think the problem is something to do with the swap drive or my lack of it as i never made one. is that any help.

---

### Post by 47_MasoN_47 on 2008-01-28
I feel your pain, I don't really understand what people are talking about in the fix thread for the suspend/hibernate problem.  I have a Compaq Presario 2170 and a IBM Thinkpad G41 both running Gutsy and neither will suspend or hibernate.  The Compaq did with Fiesty but now it doesn't anymore.  The Thinkpad never worked with either one.  It will suspend fine but the only way to get it to come on is to remove the battery, put it back in, and turn it on, and then it has to do a full reboot.

I read about the TuxOnIce thing, but am somewhat afraid of messing with the Kernel.  If you are comfortable messing with the kernel you might wanna try that out stubblepoo.

---

### Post by diaa on 2008-01-28
> **47_MasoN_47 said:**
> I feel your pain, I don't really understand what people are talking about in the fix thread for the suspend/hibernate problem. I have a Compaq Presario 2170 and a IBM Thinkpad G41 both running Gutsy and neither will suspend or hibernate. The Compaq did with Fiesty but now it doesn't anymore. The Thinkpad never worked with either one. It will suspend fine but the only way to get it to come on is to remove the battery, put it back in, and turn it on, and then it has to do a full reboot.

I read about the TuxOnIce thing, but am somewhat afraid of messing with the Kernel. If you are comfortable messing with the kernel you might wanna try that out stubblepoo.

Using s2disk doesn't involve compiling the kernel, so there's no messing with anything, you can just remove it if you get suspicious.

> **stubblepoo said:**
> i tried this a while back and it dind't work, i think the problem is something to do with the swap drive or my lack of it as i never made one. is that any help.

Yes, [turn on your swap drive permanently]("http://ubuntuforums.org/showthread.php?t=589586") then try again, it should work

---

