---
title: "EDIT Grub safely"
date: 2014-07-05
forum: General Help
---

### Post by nick126 on 2014-07-05
Hi, i have dual-booted my laptop with windows 7 and ubuntu, and have grub 2 at startup  to select between them, with ubuntu the top and default, and windows at the bottom. 
I want to change that, i.e reorder them. I recently tried one of the online guides (to reorder it)  about editing some file somewhere and despite correctly following it, messed up my whole partition and had to spend hours fixing it. I would like to know if there is a way to do it safely that anyone could recommend, again I know there are guides online already , but I dont want to stuff my setup again. So if there is a safe way that wont stuff up my system... please let me know
Your help would be greatly appreciated, thanks.

---

### Post by yancek on 2014-07-05
> I want to change that, i.e reorder them. I recently tried one of the  online guides (to reorder it)  about editing some file somewhere

"Some file", "some where"??  That's a little vague.  I hope you learn to keep better notes in the future or you will continue to have problems.  To se windows as the default to boot from Grub, you go to the /boot/grub/grub.cfg file or it might be in /boot/grub/i386-pc/ and count the menuentry entries.  If you windows entry is the fifth menuentry you would go to the /etc/default/grub file and change this line:

> GRUB_DEFAULT=0

so that it looks like this:

> GRUB_DEFAULT=4

4 rather than five as in this case, Grub counts from zero.  If you want to move the actual menentry up so that it is at the top of the grub menu, that's another story.  I've only done this on a temporary basis to test flash drives but moving the entry up works.  I expect that if you were to run update-grub, it would change it back?

---

### Post by grahammechanical on 2014-07-05
> [COLOR=#000000] I expect that if you were to run update-grub, it would change it back?[/COLOR]

I do not think so.
 
grub.cfg is composed from information in several other grub configuration files and that includes the /etc/default/grub. We do not edit grub.cfg but we can edit the other grub configuration files. Then running update-grub will create grub.cfg.

There is also a utility with a GUI that can do it for us. It is called Grub Customizer. We install it through a PPA.

[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

[https://answers.launchpad.net/grub-customizer/+faq/1355](https://answers.launchpad.net/grub-customizer/+faq/1355)

Regards.

---

### Post by yancek on 2014-07-05
So you are saying that if the OP physically moves the menuentry in grub.cfg from its present location to be the first entry in the file, he could run update-grub and it would still be the first entry?  I doubt that but haven't tried it.  Obviously, if the OP makes the change in /etc/default/grub by entering a new number for GRUB_DEFAULT that will stay.  As I understand it, the primary reason for not editing grub.cfg directly is that updating grub will overwrite or change anything that is not in the /etc/defaul/grub file or the /etc/grub.d/ files.  I make changes there to test things all the time with no problems.

---

