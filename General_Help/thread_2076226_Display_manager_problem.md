---
title: "Display manager problem?"
date: 2012-10-25
forum: General Help
---

### Post by 25tom on 2012-10-25
Recently experimentally installed gdm instead of lxdm... Later, I decided to return to lxdm. I uninstalled gdm and, as advised by a line of text that appeared in the terminal during the uninstallation process, ran the command ```
dpkg-reconfigure lxdm
```

Now when I try to boot Lubuntu, I either get just a black screen or an endlessly looping loading screen (Lubuntu logo with row of blue/white dots underneath).

How can I get the greeter/display to come back?

I can get lxdm to run if I go in recovery mode and type ```
sudo lxdm
```

but the screen looks all stretched when I do this.

Thanks in advance for any help :)

---

### Post by ajgreeny on 2012-10-25
If this is Lubuntu 12.04 or 12.10 you need to be aware that lightdm has taken over from lxdm, though for some reason lxdm is still installed (in 12.04 it is anyway).

[COLOR=Red]EDIT:[/COLOR]  Scrub that; lxdm is not installed as well, it seems that some files for lxdm still appear in the filesystem for some reason.

Perhaps use lightdm instead of lxdm in the command you used?

---

### Post by 25tom on 2012-10-26
> **ajgreeny said:**
> If this is Lubuntu 12.04 or 12.10 you need to be aware that lightdm has taken over from lxdm, though for some reason lxdm is still installed (in 12.04 it is anyway).

[COLOR=Red]EDIT:[/COLOR]  Scrub that; lxdm is not installed as well, it seems that some files for lxdm still appear in the filesystem for some reason.

Perhaps use lightdm instead of lxdm in the command you used?


I think it's Lubuntu 11.10... It's Oneiric Ocelot, anyway...
Does this make a difference?

---

### Post by 25tom on 2012-10-26
Hmmm, I have tried lightdm, and the problem persists. None of my data is lost, so I'm gonna go for a standard Ubuntu install.

Thanks for the help :)

---

### Post by ajgreeny on 2012-10-26
If I'm not too late try ```
sudo dpkg-reconfigure lxdm
```
It looks as if you tried that without root permissions which would not work.

Sorry I missed that need before.

I also think that **lightdm** did not arrive in Lubuntu till 12.04, hence I have left **lxdm** in the command as it was.

---

### Post by 25tom on 2012-10-27
> **ajgreeny said:**
> If I'm not too late try ```
sudo dpkg-reconfigure lxdm
```
It looks as if you tried that without root permissions which would not work.

Sorry I missed that need before.

I also think that **lightdm** did not arrive in Lubuntu till 12.04, hence I have left **lxdm** in the command as it was.

Yes, I did try that, thanks anyway :) Since I haven't been able to get anything to work, I've uninstalled Lubuntu and I'm now just using standard Ubuntu... Thanks to everyone for the help :)

---

