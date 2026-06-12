---
title: "Graphics Dead-Need to Manually Replace Drivers"
date: 2008-06-26
forum: General Help
---

### Post by Dylnuge on 2008-06-26
Hello,

Using Ubuntu 8.04, the graphics card seemed to have died on me. Dell is insisting it is a software problem and wants me to reinstall the drivers, despite graphics oddities appearing on the startup splash screen (The Dell one, not the Ubuntu one) and text not rendering right on the GRUB screen.

I have an old 7.04 LiveCD and I can boot in Graphics "Safe" Mode only. Can I update my drivers from the LiveCD to test if it is a software issue, and if so, how?

Thanks!

---

### Post by Dylnuge on 2008-06-26
Anyone?

I don't want to go through the pains of reinstalling my OS if it can be fixed easy or is a hardware problem.

---

### Post by Elfy on 2008-06-26
> Can I update my drivers from the LiveCD to test if it is a software issue, and if so, how?

I'm not sure that you can, I know that nvidia makes you reboot at which point you would lose it again.

But if grub isn't right it wouldn't make much sense to me for it to be the driver, because it's not started afaik.

Can you get to recovery mode - Hardy has a little menu - one option being to fix x server

I'm not sure that the dpkg-reconfigure command lets you do anything with the video anymore either - but could be wrong.

Or maybe see if you can edit xorg.conf at a root prompt to use vesa and then try reinstalling.

---

