---
title: "can i run an existing windows xp on hardy heron?"
date: 2008-04-26
forum: General Help
---

### Post by pengko.eo on 2008-04-26
Hi guys. I am a newbie to Ubuntu Hardy Heron. 

Is there any software that can run an existing windows xp on hardy heron? 

Meaning that I have a windows xp installed on my computer and i would like to run it from my hardy heron. I heard a software called virtual box and i have tried it, but it seems like instead of running the existing windows xp on hardy heron, we should install a new windows xp on hardy heron.

is there any software that can run my windows xp on a hardy heron? 

thank you very much for the help.

---

### Post by evymetal on 2008-04-26
You can run a dual boot installation (so you can boot either into windows or Hardy when you start your computer) - that's what I have (although I only have windows for testing purposes, I never use it).

Is it the applications that you want or your documents? If you just want the documents then you should be able to access them from Hardy already.

---

### Post by Monicker on 2008-04-26
The commercial version of VMWare Workstation gives you the option of running an existing XP install from a virtual machine.  It would read the data directly from the XP partition, so you would see everything as if you had booted into it.

---

### Post by pengko.eo on 2008-04-29
hi monicker. thanks for the information about vmware. i have installed it on my hardy heron. the thing is, how do i create a virtual machine for my existing windows xp? i somehow always ended in the menu that it wants me to install a new windows xp. could you please help me with a tutorial? thanks a lot

---

### Post by the8thstar on 2008-04-29
Your best bet at this point is to use the search tool on these forums (or even Google for that matter) and look for "running an existing installation of Windows XP in VMWare" or "running an existing partition of Windows XP", etc. There are MANY tutorials for doing that on VMWare or VirtualBox (same kind of software).

Be aware that games that require directX and/or heavy 3D effects will not run in a virtual machine, simply because 3D support is still an experimental feature at best and at worse, most computers don't have the power to harness that load of work (Ubuntu + XP + 3D).

Also, you will need to reactivate XP because Windows will think it's been reinstalled on a new machine (i.e. hardware change). Unfortunately, if you want to boot into your Windows partition (not inside VMWare this time), you will have to reactivate again. Eventually Windows will lock itself up and you will have to call the hotline in India to get a new COA (certificate of activation). This is a Microsoft issue, nothing to do with Linux.

Finally, running an existing install of Windows in VMWare can be tricky because you can launch the Ubuntu partition by accident instead of Windows, which means that Ubuntu is going to try to run itself in VMWare. This is the WORSE scenario and usually it causes the system to hang and you will need to reinstall it afterwards.

I hope my 'warnings' will help you in making a sound decision.

---

### Post by pengko.eo on 2008-04-29
thank you for the warning 8th star. but i am willing to take the risk since i just reformatted my pc and i practically have nothing to lose. I have tried googling for a bit much, but i cant find the perfect tutorial about running my existing windows xp on hardy heron. does anyone have any good tutorial about this?

thanks a lot

---

### Post by the8thstar on 2008-04-30
Someone may have answered your prayers, **pengko.eo**! Check this forum:
[http://ubuntuforums.org/showthread.php?p=4840018#post4840018]("http://ubuntuforums.org/showthread.php?p=4840018#post4840018")

Hope this helps. :)

---

