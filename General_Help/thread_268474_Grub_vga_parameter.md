---
title: "Grub vga parameter"
date: 2006-09-30
forum: General Help
---

### Post by Koybe on 2006-09-30
Hello,

I just buy a new wide screen. I was used to set vga parameter in grub to 791 to get a 1024x768 resolution. Does anyone know howt to set 1680x1050 if it is possible?

All I found is this : [http://www.8ung.at/spblinux/grub.htm](http://www.8ung.at/spblinux/grub.htm)

Tanx for the help ;-)

---

### Post by hugmenot on 2006-09-30
What does work is 1400x1050 in the framebuffer. You get some black margin left and right but I think that&#8217;s okay. My problem is that for the life of me I can&#8217;t remember what I used to have in /b/g/menu.lst to get this resolution.

I read something about vga=0x343 on the forums but vbetest reports only 1400x1050 @ 16-bit as supported and lists the number [328]. When I tried to use that as vga=0x328 booting didn&#8217;t continue.

EDIT: [http://gentoo-wiki.com/HOWTO_fbsplash](http://gentoo-wiki.com/HOWTO_fbsplash) says it&#8217;s decimal and I have to add 512 to the number in square brackets. A ha!

---

### Post by Herman on 2006-09-30
Here is a link to an excellent how-to on this subject, **[HOWTO: Change bootup resolution]("http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters"), by **[Indras]("http://www.ubuntuforums.org/member.php?u=126305").

You should be able to experiment with this using Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

When you find out what you want you will most likelyt want to edit your /boot/grub/menu.st Operating System Entries.....................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries")

And probably your automagic kernels list as well, if you want the changes to be retained at the next kernel update, defoptions.............................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#defoptions")


EDIT, Sorry for any inconvenience, but, I don't see the resolution you want listed there either, I hope I didn't waste your time.
Try vga=ask maybe, for a menu, when booting up from Grub's Command Line Interface, and see if that helps.

Regards, Herman :D

---

### Post by Koybe on 2006-10-01
Tank you for these and answers, i'll have a try as soon as spossible and i'll told you.

EDIT : I tried 833 and 834 for 1400x1050 resolution and 865, 866 for 1650x1080 but none of these worked. Anyway I'm not sure if i'm wrong or if the kernel is simply not compiled with these options. Maybe waiting fot Edgy will help as I saw they will show high def boot splash. ;)

---

