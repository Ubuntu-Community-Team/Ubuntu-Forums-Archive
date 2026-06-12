---
title: "Getting a script to execute on startup."
date: 2013-08-26
forum: General Help
---

### Post by blackout2 on 2013-08-26
Hello, I know this is Ubuntu forums, and I'm not sure whether or not I should put this in General Help, or other Distro. I am using Backtrack 5. I know, when I downloaded it I didn't realize how stupid and "script kiddie" it was, and it's already on my partition, but it has a terminal, so it works for me. I REALLY do not like the programs on the computer, they are only for people who either don't know anything, or someone who knows everything, and just wants to save time. I am neither(I even have it so none of the programs will open, in case I get tempted). Anyway, Backtrack 5 is based heavily on Ubuntu, meaning even GRUB recognizes it as Ubuntu.

So, now that that is out of the way, here is my issue, I have written a simple script, that I plan to add to in the future, and I want it to run at startup. I really have no idea how to do this, and the closest thing to it is when I put a VBScript in the startup folder on my Windows(It greets me every time I boot up).
So, I would like some help in finding the startup folder, and anything else I should know.

Thanks in advance.

---

### Post by Quackers on 2013-08-26
Try calling the script by entering it in Startup Applications. Click the + sign and enter the details there.

---

### Post by blackout2 on 2013-08-26
Yea, I could do that, I didn't think of that....I was hoping to do it without using the GUI, but until then, it will work. Thanks.

---

### Post by Yellow Pasque on 2013-08-27
It used to be that you put the command in /etc/rc.local or /etc/init.d/rc.local
I'm not sure if that still works in the upstart era.

---

### Post by blackout2 on 2013-08-27
Yea, I was going to do this more with startup, but I ran into a little problem, that makes me embarrassed, I was having some problems with se-toolkit, so I couldn't download anything from apt, or synaptics, so, I removed it from the computer, and tried to reinstall, I followed some instructions on the internet, and they didn't work. I will post the code in a sec(I have to boot into the Linux)

---

### Post by SeijiSensei on 2013-08-27
> **Temüjin said:**
> It used to be that you put the command in /etc/rc.local or /etc/init.d/rc.local
I'm not sure if that still works in the upstart era.

Putting commands into /etc/rc.local will work even with Upstart.  Upstart still uses the /etc/init.d/ structures and starts all linked programs found in /etc/rc2.d/ at boot.  The last of these executes /etc/rc.local.

However if the script requires network access, it won't work on desktop Ubuntu systems where the network is usually started by the user.  rc.local will have executed long before then.  You can resolve this problem by creating a static network definition in /etc/network/interfaces.  I think there may also be a way to have a script run immediately after the network is started by the user.

---

### Post by blackout2 on 2013-08-27
Yea, well that didn't work, I put my program in Startup Applications, and I accidentally put it on a higher priority then the important programs, and I couldn't move the mouse, no display, etc, etc, so I just did a re-install, and now I'm good, with apt and all that.
EDIT: When I say "It didn't work", I was referring to putting it in Startup....

---

