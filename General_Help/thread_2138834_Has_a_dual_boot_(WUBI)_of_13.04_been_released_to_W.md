---
title: "Has a dual boot (WUBI) of 13.04 been released to Windows yet?"
date: 2013-04-25
forum: General Help
---

### Post by DivingHawk on 2013-04-25
Pretty much just what the topic says. Can i download a dual boot for Windows 7 now? If not when can I?

---

### Post by grahammechanical on 2013-04-25
Wubi is not a dual boot method of installing Ubuntu on a machine with Windows OS installed. And Wubi is not available from 13.04. **W**indows-based **Ub**untu **I**nstaller

[https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html)

---

### Post by DivingHawk on 2013-04-25
Alright. So is dual booting currently an option on 13.04?

---

### Post by deadflowr on 2013-04-25
> **DivingHawk said:**
> Alright. So is dual booting currently an option on 13.04?

Yes, just not with wubi.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by oldfred on 2013-04-25
If you do not want to repartition which is required for a full partitioned dual boot, you can install to another drive. You can use an external hard drive or even a flash drive. Flash drive may not be as fast as a full install to your hard drive but if functional and good way to do an extended test if you are not sure you will like Ubuntu. A persistence install is using the live installer with the capability to save some data. A full install has all the same functions as any install.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Now older but the logic is the same.

 HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

### Post by DivingHawk on 2013-04-25
Are there any plans to release WUBI for 13.04? It's pretty much the way I've grown accustomed to. Ya know, just in case I need Windows for something.

---

### Post by Gizfreak on 2013-04-25
I had a dualbooting PC with windows8 / Ubuntu 13.04 nightly build and that was made possible with [this wubi.exe]("https://mega.co.nz/#!OBBkAQ6b!VFWunV7FDHZpGOats5SMhBogUeRGw9LdVF7apfAbEmc").

---

### Post by oldfred on 2013-04-25
I have no idea who mega is, but it is not an Ubuntu supported version.

       Wubi not available with 13.04
[https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-April/036993.html)

---

### Post by bcbc on 2013-04-25
> **Gizfreak said:**
> I had a dualbooting PC with windows8 / Ubuntu 13.04 nightly build and that was made possible with [this wubi.exe]("https://mega.co.nz/#!OBBkAQ6b!VFWunV7FDHZpGOats5SMhBogUeRGw9LdVF7apfAbEmc").I don't advise using unofficial wubi.exe versions. There's a wubi.exe for 13.04 signed by Canonical if you must use it. But it's officially unsupported so I don't know why it's here: [http://releases.ubuntu.com/13.04](http://releases.ubuntu.com/13.04)

---

### Post by Impavidus on 2013-04-25
> **DivingHawk said:**
> Are there any plans to release WUBI for 13.04? It's pretty much the way I've grown accustomed to. Ya know, **[COLOR=#ff0000]just in case I need Windows for something[/COLOR]**.

Sounds like Ubuntu is your primary system. In that is case it's better to do a full dual boot on a separate partition.

---

### Post by deadflowr on 2013-04-25
> **Gizfreak said:**
> I had a dualbooting PC with windows8 / Ubuntu 13.04 nightly build and that was made possible with [this wubi.exe]("https://mega.co.nz/#!OBBkAQ6b!VFWunV7FDHZpGOats5SMhBogUeRGw9LdVF7apfAbEmc").


I'm guessing that with the past tense, you've since removed Ubuntu.

As oldfred said, that technique is unsupported and will likely be fraught with problems going forward.

Don't count on a lot of help if using that crashes your system, eventually.

---

