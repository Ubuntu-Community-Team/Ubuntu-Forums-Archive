---
title: "First time upgrading"
date: 2012-10-20
forum: General Help
---

### Post by GJ1234 on 2012-10-20
Hello fellow Linux enthusiasts!

I'd like to ask some questions about upgrading from Ubuntu 12.04 to 12.10.
This is my first time ever to upgrade an operating system and I only have run Linux for a few months now.
I'm aware that the update manager is perfectly usable to update and it seems very simple indeed, but I also have Windows 7 on the same laptop and I used Grub Customizer to set Windows as the default boot option.
Will the update to 12.10 affect the bootorder?
Also I read about ppa's that won't work properly, will this completely crash the operating system or just some specfic programs?
Thanks for the help!

---

### Post by offgridguy on 2012-10-20
> **GJ1234 said:**
> Hello fellow Linux enthusiasts!

I'd like to ask some questions about upgrading from Ubuntu 12.04 to 12.10.
This is my first time ever to upgrade an operating system and I only have run Linux for a few months now.
I'm aware that the update manager is perfectly usable to update and it seems very simple indeed, but I also have Windows 7 on the same laptop and I used Grub Customizer to set Windows as the default boot option.
Will the update to 12.10 affect the bootorder?
Also I read about ppa's that won't work properly, will this completely crash the operating system or just some specfic programs?
Thanks for the help!
12.04 and 12.10 are different OS so it is not an update  but an install and yes it will affect the boot order.  Just to clarify are you meaning an upgrade from 12.04 to 12.10 or an update from 12.04 to 12.04.1 ??

---

### Post by GJ1234 on 2012-10-20
> **offgridguy said:**
> 12.04 and 12.10 are different OS so it is not an update  but an install and yes it will affect the boot order.  Just to clarify are you meaning an upgrade from 12.04 to 12.10 or an update from 12.04 to 12.04.1 ??

I did not even know there was a 12.04.1 is there any significant difference?
Mm okay, do you know if GRUB customizer already works for 12.10?

---

### Post by offgridguy on 2012-10-20
> **GJ1234 said:**
> I did not even know there was a 12.04.1 is there any significant difference?
Mm okay, do you know if GRUB customizer already works for 12.10?
12.04.1 is 12.04 with all the updates thats all.  There are a lot of negative issues in this forum regarding 12.10,  personally i would stick with 12.04,  But do a thread search and
check it out for yourself.  I  am not 100% sure but GRUB customizer probably works for
12.10 as well.
:):)

---

### Post by grahammechanical on 2012-10-20
> do you know if GRUB customizer already works for 12.10?

It works a little bit. It does not handle the Grub 2.0 submenus very well.

Grub 1.99 uses sda1, sda5, etc.  Grub 2.0 uses msdos1, msdos5, etc. And this is causing confusion with duplicate entries.

The last Linux OS to be installed will always put its version of Grub into the MBR and the grub.cfg file generated will become the controlling configuration.

You will get Grub 2.0 if you upgrade or fresh install 12.10. But Grub 2.0 is going to be put into 12.04 by the end of January anyway.

12.04.1 is what is called a point release. As you can see from this release schedule there will be another 3 by April 2014.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule]("https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule")

People modify the desktops very much and then experience issues with an upgrade to the next release.

Upgrades are tested but only from a default 12.04 to a default 12.10. We cannot test for every possible combination that people have.

Deactivate any ppas. Revert your desktop to a default configuration. Allow time for community developers to catchup with the new release and modify their utilities accordingly. In other words, do not be in such a rush.

Regards.

---

### Post by offgridguy on 2012-10-20
[Quote}
People modify the desktops very much and then experience issues with an upgrade to the next release.
.[/QUOTE]

Thank you for this info.

---

