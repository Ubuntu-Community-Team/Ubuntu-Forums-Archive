---
title: "Lirc in Feisty"
date: 2007-04-12
forum: General Help
---

### Post by manro on 2007-04-12
Hello,

I made lirc work in Edgy following this tutorial: [[COLOR="Sienna"]http://ubuntuforums.org/showthread.php?t=288229&highlight=lirc[/COLOR]]("http://ubuntuforums.org/showthread.php?t=288229&highlight=lirc")

Now, it only works for kernel 2.6.17-10-generic (or at least I cannot make it work with other one) ... because of this I never update my kernel (not that I don't want to). Now with Feisty almost out I really want to upgrade, I test the beta and the remote seems to work, but just like it used to work in Edgy, is like "pre-configured" without lirc and I don't have any idea how to make lirc to work in Feisty as it do in Edgy with 2.6.17-10 kernel.

Any help I'll really apreciate!

Regards,
Manro

---

### Post by superm1 on 2007-04-12
Hi, 
per the lirc howtos, you just need to rebuild your kernel module after upgrading.

See the bottom of this link:
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

"Rebuild Modules"

---

### Post by manro on 2007-04-12
Thanks a lot! ... I'll try it as soon as I get home and let you know how it goes!

Thanks again,
Manro

> **superm1 said:**
> Hi, 
per the lirc howtos, you just need to rebuild your kernel module after upgrading.

See the bottom of this link:
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

"Rebuild Modules"

---

### Post by manro on 2007-04-14
> **superm1 said:**
> Hi, 
per the lirc howtos, you just need to rebuild your kernel module after upgrading.

See the bottom of this link:
[https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty)

"Rebuild Modules"

Hi again,

superm1, thanks, I follow the howto you point me to but I think that my problem is the "managed I2C device", my tv card is an avermedia and I just don't know/understad how to change the ir_common module in Feisty's kernel :( ... I'll really apreciate all the help you guys can give me! :D 

Thanks agian!
Best Regards,
MaNRo

---

### Post by superm1 on 2007-04-14
I wish I could help more there - but I don't have one of these myself and haven't experienced the issue first hand.  Following hexion's howto in the thread should hopefully be fairly straightforward afaik.
Sorry!

---

### Post by manro on 2007-04-14
> **superm1 said:**
> I wish I could help more there - but I don't have one of these myself and haven't experienced the issue first hand.  Following hexion's howto in the thread should hopefully be fairly straightforward afaik.
Sorry!

Hey Superm1, thanks a lot for worry about my issue, I'll keep reading and asking here and there :D ... as soon as I figure out how to make it work I'll let you know!

Thanks!
MaNRo

---

