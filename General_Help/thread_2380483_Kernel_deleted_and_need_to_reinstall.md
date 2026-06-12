---
title: "Kernel deleted and need to reinstall"
date: 2017-12-18
forum: General Help
---

### Post by shalinmishra on 2017-12-18
Hello,

New to Ubuntu. 

I was using Ubuntu 10.04.2 and i deleted lsb-base. Now, the ubuntu will not load and says the kernel is not available. I then installed Ubuntu 10.04.4 on another partition. Can I retrieve my earlier environment and fix its kernel? I don't want to lose the programs and applications in my 10.04.2 environment.


Regards,
Shalin

---

### Post by howefield on 2017-12-18
Best thing that could have happened, 10.04 is long passed its support life cycle.

Use a supported release.

---

### Post by shalinmishra on 2017-12-18
I just want my old applications and data back from the partition. How do I get it?

---

### Post by coffeecat on 2017-12-18
Mount the partition that has your data from your parallel 10.04.4, or from a live session, and copy your data to an external drive. That's assuming you haven't already been making backups of your data. You do do regular backups of your data, don't you?

As far as applications are concerned, you'll have to re-install them when you have installed a supported version of Ubuntu. Application configurations: ditto. It's theoretically possible to rescue your application configurations from your old 10.04, but that path leads to frustration, misery, teeth-gnashing and general annoyance. Things have changed so much since 10.04, that you are likely to cause yourself problems by doing this. It'll be quicker and less stressful to simply install applications and configure them to your liking in your new Ubuntu install.

Friendly piece of advice. Make a note of the end-of-life date of the version of Ubuntu that you install and make sure you upgrade or re-install before then. 16.04 is the current latest LTS with support until 2021, and 17.10 the current intermediate release with support only until July next year. The server version of 10.04 has been obsolete for over two years, and the desktop version for over 4 years. We cannot provide support for such a dead version of Ubuntu.

---

### Post by ajgreeny on 2017-12-18
Start with a supported version running as a live system, mount the partition that should show in your live system file manager, and search for your files there.

Once found you can copy them to an external USB disk or other device.

There is little that we can do with 10.04 as the repos for that have been moved and it would be pointless trying to revive that when you can retrieve those files more easily with the live system.

---

### Post by vasa1 on 2017-12-18
> **coffeecat said:**
> ...
Friendly piece of advice. Make a note of the end-of-life date of the version of Ubuntu that you install and make sure you upgrade or re-install before then. ...
@ shalinmishra, You can visit [https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29](https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29) for the dates.

---

### Post by shalinmishra on 2017-12-18
Thank you all for the response. However, it still doesn't help me. I understand the constraints. Unsupported version, etc etc. But I wish there was a way i could use the software from the 10.04.2 environment some way. I need to get keys again to re-install it and that will mean paying again for the same software (that was the TnC). Thanks all anyway. Good day.

---

