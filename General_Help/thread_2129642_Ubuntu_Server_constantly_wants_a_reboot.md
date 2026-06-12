---
title: "Ubuntu Server constantly wants a reboot"
date: 2013-03-26
forum: General Help
---

### Post by jeff7181 on 2013-03-26
I have Ubuntu Server 12.04.2 3.2.0-39-generic x86_64 running in a VM on ESXi 5.0.  I'm using it as a minecraft server and it runs well.  However, it seems like every time I SSH to the VM to check on things, I see this message:  *** System restart required ***
It's not automatically updating, and there's not always even updates available. 

I'm somewhat new to Linux, I can find my way around but for example, I don't know what causes that message to be displayed.  Obviously there's a flag somewhere that gets set to display that text... and I'm trying to find out what can/is setting that flag.  I always hear about how Linux doesn't need as many reboots as a Windows box but it seems like every week, even multiple times a week, it's prompting me to reboot so I'm looking for some help figuring out why.

---

### Post by dcstar on 2013-03-27
Not updating eh, then how come it has a kernel that was only released a month or two ago and has already been replaced by 3.2.0-40 in the last day or so?

It is updating, and the reboot prompts are because it wants to run the new kernel it just updated to. No point hiding the messages whatsoever.

---

