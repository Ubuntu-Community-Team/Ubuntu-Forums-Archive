---
title: "Networking, suspend and shutdown/restart all partly broken since Saucy upgrade"
date: 2013-10-27
forum: General Help
---

### Post by halfbeing on 2013-10-27
I wonder if someone can help me. I have been experiencing a number of problems since upgrading to Saucy and I suspect they may be related, but I've no idea against which package(s) I should file bug reports.

Firstly, shutdown/restart doesn't work from the Unity menu. Nothing happens. I have to do a "sudo reboot" from the terminal.

Secondly, I often find when waking from suspend that I have no network. Both my network cards are inactive. I often find in these cases that doing another suspend cycle will fix this, but this only seems to work (when it works) if I suspend using the keyboard shortcut (I haven't tried from the Unity pull-down menu). Suspending by doing "sudo pm-suspend" from the terminal doesn't fix the networking. But that puts up against my third problem…

Very often, after the second problem has occurred, suspend by keyboard shortcut and Unity pull-down menu stop working. Since suspend from the terminal doesn't help me either, I have no "sudo reboot" from the terminal to get networking and suspend functioning again.

---

### Post by vanadium on 2013-10-27
How did you upgrade? Although officially supported, upgrading over an existing Ubuntu version is not always without its issues. It is usually preferred to do a fresh installation, i.e., one where the system partition has been wiped. This eliminates the chance that old settings conflict with the newly installed OS. There is significant chance that the symptoms you decribe will be gone when you clean reinstall the new Ubuntu version. Anyway, you may try first in a live session wether the proble is there. If it is there as well, then it indeed denotes an incompatibility between the new Ubuntu and your hardware, and reinstalling won't help.

---

### Post by halfbeing on 2013-10-27
Yes, I upgraded an existing installation. My guess is that, since the problems are intermittent, this isn't due to hardware incompatibility. So maybe you are right about settings conflicts being the cause. But wiping the system partition and reinstalling everything is a huge job, particularly when you have to do it every six months to keep up with the Ubuntu release cycle.

---

### Post by vanadium on 2013-10-27
> **halfbeing said:**
> But wiping the system partition and reinstalling everything is a huge job, particularly when you have to do it every six months to keep up with the Ubuntu release cycle.
Reinstalling is what I now do from within a sofa in less than 30 minutes. However, if you need to transfer your data back, then it will take a lot longer indeed.

I want a clean install every 6 months, but do not feel to recopy my data each time. This is why I have a separate home partition. From within the installation CD, I rename my home directory away, e.g. /home/vanadium -> /home/vanadium_old. Then, I do a fresh installation with manual configuration ("Something else" in the Installation options). I assign my root partition for /, with indication that it can be wiped and reformatted, I assign my home partition for /home, indicating it should not be formatted. This creates a brand new installation for me, with a new clean /home/vanadium home directory. Then it is a matter of moving the contents of the old home to Documents, Videos, ... in the new home. I also move the configuration directories of Firefox and Thunderbird along.

As many testimonies reveal: you *can* conveniently upgrade every six months, but there is no guarantee that it doesn't create any issues.

One other reason I do clean upgrades is in fact to see the new system with the new defaults as the developpers designed it.

---

### Post by marcinkowski on 2013-10-27
This solved the network on wake from suspend issue for me:

[http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153](http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153)

though I am still suffering from this other suspend issue:

[http://askubuntu.com/questions/366511/update-to-13-10-blank-screen-and-repeated-suspend-on-wake-from-suspend](http://askubuntu.com/questions/366511/update-to-13-10-blank-screen-and-repeated-suspend-on-wake-from-suspend)

---

### Post by halfbeing on 2013-10-28
Thanks for finding that. It does look like the issue I'm having. I haven't tried the workaround yet but there's enough people saying that it works. Apparently just doing a "restart network-manager" at the command line should work too.

By the looks of things it probably wouldn't have helped to have done a clean install of 13.10 in this case.

---

### Post by marcinkowski on 2013-10-28
No problem. I didn't do a clean install either.

Just for the sake of completeness, issuing either: [FONT=Ubuntu Mono]

sudo nmcli nm sleep false

[/FONT]or 
[FONT=Ubuntu Mono]
[/FONT][FONT=Ubuntu Mono]sudo service network-manager restart
[/FONT]
also solved the problem on a one-off basis for me.
[FONT=Ubuntu Mono][/FONT]
source: [http://askubuntu.com/questions/365441/13-10-suspend-kills-wifi](http://askubuntu.com/questions/365441/13-10-suspend-kills-wifi) and [http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153](http://ubuntuforums.org/showthread.php?t=2182128&p=12830153#post12830153)

---

