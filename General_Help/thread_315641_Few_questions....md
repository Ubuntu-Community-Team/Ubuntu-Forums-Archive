---
title: "Few questions..."
date: 2006-12-09
forum: General Help
---

### Post by gatorbowls on 2006-12-09
Hey, I have a few questions about  ubuntu..first of all I have Microsoft Windows Xp home edition I burned Unbuntu and now running it live through the cd... I would love to install it so than i dont need the Cd... But my question is... if i install it, but than decide to go back to Microsoft windows xp home edition can I do that? Or is it a 1 time deal where i cant.

Second question..
Would I need a anti virus scanner...And are linux's even dispose to viruses on the Internet including Trojans,spy ware,key loggers ect..

---

### Post by PriceChild on 2006-12-09
Welcome to Ubuntu :)

I'm glad to see you're enjoying the live cd and want to increase your usage.

To install, I advise you defragment your windows install, then follow the following instructions to install ubuntu in a "dual boot" [http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

You will be able to choose which OS to boot up.

And secondly, > Ubuntu is quite secure. Average users don't need to install a firewall or a virusscanner. But remember security is a process instead of a product so you still have to be careful with what you do. For example don't give root privileges to programs which don't need them and don't install server stuff (which might open ports) if you don't need it.

---

### Post by steve.horsley on 2006-12-09
Yes you can un-install Ubuntu again. First use the Windows install CD to put the windows bootloader back, then delete and re-use the Ubuntu partitions.

You don't really need a virus scanner unless you tend to forward lots of emails from windows users to other windows users, in which case a the scanner could prevent you from passing windiws viruses on.

---

### Post by PriceChild on 2006-12-09
> **steve.horsley said:**
> Yes you can un-install Ubuntu again. First use the Windows install CD to put the windows bootloader back, then delete and re-use the Ubuntu partitions.Forgot this bit.

Yeah, you can put in the windows xp disc. Choose to go into a recovery console (not automated system recovery) Log in, then type ```
fixmbr
```Restart your computer and then you should be back to windows. You can then use something like partition magic, or a gparted live cd to remove the ubuntu partition and make the windows one bigger again.

---

### Post by gatorbowls on 2006-12-09
alrite but do you guys support gameing such as America's army and medal of honor and battlefield 1942...???

---

### Post by PriceChild on 2006-12-09
> **gatorbowls said:**
> alrite but do you guys support gameing such as America's army and medal of honor and battlefield 1942...???1942 runs perfectly under the proprietory software "Cedega", Don't think MoH will work. AA "should" work under cedega... but you may have problems with punkbuster.

There's nothing wrong with dualbooting :)

Personally, I find amazing native linux games such as NWN.

---

