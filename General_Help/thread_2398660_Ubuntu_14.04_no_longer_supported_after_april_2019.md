---
title: "Ubuntu 14.04 no longer supported after april 2019"
date: 2018-08-15
forum: General Help
---

### Post by jbamford92 on 2018-08-15
Hi,

So i have a HTPC Server running MythTv along with Kodi which is running 14.04. However i cannot upgrade because the firmware for the Satellite Tuners i use will not compile with 16.04 and higher. So what does this mean? Can i no longer use my HTPC Server? I have tried 16.04+ with the Firmware but its completely broken. Im not buying new cards just to upgrade neither because these cards are not cheap. Any ideas?

Thanks.

---

### Post by DuckHook on 2018-08-15
Nothing stops one from running a version past EOL. You just won't be getting further updates and are therefore at risk of getting pwned or worse. However, this danger is not an absolute. It must be placed into its proper context and that may mitigate the danger sufficiently to allow continued use.

Example: I still run Windows XP, an OS so full of security holes that it is little short of a joke among security experts. But it is tightly sandboxed in a VM with the virtual NIC disabled and no access at all to any other part of my file system. It is not used for any new apps—just old proven ones—so my risks are small and manageable. This use case allows me to run a known security pit with few worries.

In your case, you can judge for yourself whether your real-world risks are really that high. If you delete your browsers, e-mail clients, CUPS and any other problematic apps from this box after the EOL date, keep only the bare essential GUI apps and run it strictly as an HTPC, I don't see what trouble could arise. Indeed, as a server, you may not even have to run a desktop environment and you can get rid of the GUI altogether (I don't run or understand MythTV at all, so I could just be talking out of my hat here).

Another option is to try compiling your drivers with old libraries under newer versions. I have seen threads where gurus do this, but it is way above my pay grade and I wouldn't know how to advise you. Hopefully, others can chime in.

Yet another option is to run your old OS within a VM or container. This gives you some sandboxing protection, although the need to service clients means that you will have to leave networking enabled. The main advantage would be the ability to roll back to a good snapshot should you get compromised.

Last but not least, you can contact the OEM who makes your peripherals and ask them for driver solutions you may not be aware of.

---

### Post by jbamford92 on 2018-08-15
Thanks for your reply. 

I cant really take the machine off the network or internet as i play the recordings from this HTPC in Kodi when im not at home. Its annoying i hate updating ill have to message the manufacturer on this problem. But kernel higher than 4.4.0 doesnt work.

---

