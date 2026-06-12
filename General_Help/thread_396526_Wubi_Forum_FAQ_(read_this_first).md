---
title: "Wubi Forum FAQ (read this first)"
date: 2007-03-29
forum: General Help
---

### Post by ago on 2007-03-29
**About**
[Wubi](http://wubi-installer.org) is an officially supported Ubuntu installer for Windows users that allows you to install and uninstall Ubuntu as any other Windows application, in a simple and safe way.

[color=red]**NOTE: Wubi 8.04.1 is now available: [http://wubi-installer.org](http://wubi-installer.org)**[/color]

This addresses most of the issues that emerged after the 8.04 release. Note that Wubi 8.04.1 requires the new 8.04.1 desktop ISO, you will not be able to reuse the 8.04 CD/ISO with 8.04.1. Alternate and DVD ISOs will not work with 8.04.1. It is recommended to let Wubi grab the ISO for you, if you prefer to download manually, here is the address: [http://releases.ubuntu.com/8.04.1/](http://releases.ubuntu.com/8.04.1/) (the desktop ISO is the one you want).

**Unsupported set-ups:**
[list]
[*] Software raid arrays 0 and 1 are not supported. They will be supported in the 8.10 release. Note that some "hardware" raids, are in fact software ones.
[*] Encrypted disks are not supported.
[*] Windows ME is not supported.
[*] DVD ISO/CDs and Alternate ISO/CDs are not supported. The ISO must be an 8.04 CD Desktop ISO (let Wubi get one for you). For Wubi 8.04.1 the 8.04.1 Desktop ISO is required.
[/list]
**Knonw issues of Wubi 8.04.1**
[list]
[*] If Wubi fails creating the image from a CD, please use the ISO directly by placing wubi.exe and the ISO in the same folder. For download problems please download the CD Desktop ISO manually and place it in the same folder as wubi.exe (you can get that from wubi-installer.org).
[*] If you used Wubi rev 505, the uninstaller may fail if you installed on a drive different from C. In such case use [https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe](https://wiki.ubuntu.com/WubiGuide?action=AttachFile&do=get&target=Uninstall-Ubuntu.exe). Wubi rev 506+ does not have this issue.
[*] If the installation fails while formatting the swap virtual disk it means that your drive is excessively fragmented. Uninstall, reinstall and run jkdefrag on c:\ubuntu\disks\swap.disk before rebooting.
[*] Some hardware is not fully compatible and Wubi will freeze upon booting (ACPI) and/or you may experience video problems. Those are not Wubi specific issues. There are generally special parameters that are required to enable workarounds for such hardware. If you press ESC at boot after selecting "Ubuntu" you will se a menu with more boot options. If the workarounds do the trick, we encourage you to notify the developers, so that a long-term solution can be investigated.
[*] Ubuntu cannot be booted if Windows has not been shut down cleanly, you have to clear the Windows filesystem from Windows (there is no chkdsk equivalent for Linux yet). If Wubi fails to start, boot into windows, run chkdsk /r from windows on the same drive where you have installed Ubuntu, shutdown cleanly and then try to boot into Ubuntu again.
[/list]

For a more exhaustive list please read the [WubiGuide](https://wiki.ubuntu.com/WubiGuide).

**Useful Links**
[list][*] [Wubi Latest Release](http://sourceforge.net/project/showfiles.php?group_id=198355)
[*] [Wubi Website](http://wubi-installer.org)
[*] [Lubi and LVPM Website](http://lubi.sourceforge.net)
[*] [Wubi General FAQ](http://wubi-installer.org/faq.php)
[*] [Wubi Advanced Guide](http://wiki.ubuntu.com/WubiGuide)
[*] [Search the Wubi Forum](http://www.ubuntuforums.org/search.php?f=234)
[*] [Wubi Project Page](https://launchpad.net/wubi)
[*] [Lubi Project Page](https://launchpad.net/lubi)
[*] [Lupin Project Page](https://launchpad.net/lupin)
[*] [LVPM Project Page](https://launchpad.net/lvpm)
[*] [Credits and History](http://www.wubi-installer.org/faq.php#development)
[*] [Translations](http://ubuntuforums.org/showthread.php?t=716056)
[/list]

**Asking Questions on this Forum**

Remember that Wubi is only an installer, once Ubuntu is up and running our work is mostly over, if you have general questions regarding Ubuntu please consider using dedicated resources like [Ubuntu support forums](http://www.ubuntuforums.org/forumdisplay.php?f=13), [Ubuntu documentation](http://help.ubuntu.com/) or the [Ubuntu guide](http://www.ubuntuguide.org/). This forum should be used for issues directly relating to Wubi. Before asking, see if you can find an answer using the  [Wubi general FAQ](http://wubi-installer.org/faq.php) and the more advanced [WubiGuide](http://wiki.ubuntu.com/WubiGuide). You can look for answers within the Wubi forum by using the excellent [search tool](http://www.ubuntuforums.org/search.php?f=234). If you want to report a bug, mention that in the forum before posting to the project websites, if the bug is confirmed we will add an entry in the project bug tracking system.

It helps a lot if you are descriptive and precise when reporting problems. It helps even more if you can provide relevant logs when asking for support. Logs speed up the process considerably and you will get answers/solutions more speedely. For more information on how to access the relevant logs, see: [https://wiki.ubuntu.com/WubiGuide#head-8823bb81b6e0ecd10006d3d226c1f7e8f6f705b1](https://wiki.ubuntu.com/WubiGuide#head-8823bb81b6e0ecd10006d3d226c1f7e8f6f705b1) 

If you think you found a bug, feel free to report it on this forum . If you are not sure or simply want to ask support for some issue, feel free to start a new topic. Please see the [Wubi Guide](http://wiki.ubuntu.com/WubiGuide) first. 

**What are the minefield builds?**

Minefields are experimental builds to test new pre-release features, if you want something that is supposed to work then forget about minefield builds and use the latest [official wubi version](http://sourceforge.net/project/showfiles.php?group_id=198355). If you do not mind a bumpy ride and want to help us debugging have a go in the: [minefield](http://www.wubi-installer.org/devel/minefield)

---

### Post by LibraDragon on 2009-04-11
I just written an article 
**Creating a 2nd Swap disk**

[http://ubuntuforums.org/showthread.php?t=1122928]("http://ubuntuforums.org/showthread.php?t=1122928")

I wasn't sure where to post it but hope it helps.

---

### Post by callie510 on 2009-04-11
Can you add something very obvious (maybe bold or colored) about how Wubi is not meant to install Ubuntu on a second partition, another hard drive, or anywhere except within windows?

I know this seems obvious to anyone who knows anything about ubuntu and wubi - but this forum gets a lot of non-tech-savvy traffic, and I feel like half the wubi questions I see are from people who tried to use wubi to install ubuntu to another disk - ie, not within windows.

---

### Post by alanwall on 2009-05-10
> **callie510 said:**
> Can you add something very obvious (maybe bold or colored) about how Wubi is not meant to install Ubuntu on a second partition, another hard drive, or anywhere except within windows?

I know this seems obvious to anyone who knows anything about ubuntu and wubi - but this forum gets a lot of non-tech-savvy traffic, and I feel like half the wubi questions I see are from people who tried to use wubi to install ubuntu to another disk - ie, not within windows.

OK, then I guess the wubi 8.10 install script is wrong ?
It asked where so I picked my r:\ partition.
Are you telling me it HAS to be c:\ ?
Thanks !

---

### Post by server69 on 2009-06-23
Hi!
Can anyone tell me in two words (and as simple as possible, I'm not very good in English), what are pros and cons of Wubi and differences between Wubi and fresh installation on another partition? I've read that Wubi-Ubuntu could be slower because of too much defragmented partition, but is there anything else? And for example if I were installing fresh Ubuntu I would've chosen ReiserFS or ext4, and so is there any differences between these fs and NTFS ?
And one more question, I have an ArchLinux installed, so I can't run Wubi from Windows's bootloader: what entry have I got to add to grub menu.lst ?

Thanks

---

### Post by TriadHonor on 2010-02-07
I'm adding a guide on how to resolve the grub issue with a simple method.

---

### Post by megaflyman on 2010-02-09
I have installed ubuntu using Wubi but at the boot menu the key board is none responsive. After the clock runs out the highlighted operating systems boots which is windows xp since I am unable to select ubuntu. After windows xp boots I can use the key board just fine. Does any one have any suggestion?

---

### Post by booboomc21 on 2010-06-07
I had installed Ubuntu 9.10 on my laptop through Wubi. Then removed it because i put it on my desktop. But now when ever I start my laptop it askes me if i want to start Windows or Ubuntu. I dont have ubuntu on there anymore. How can i get it back to just loading windows? 

Thanks.

---

### Post by ozmotion on 2010-07-14
i was having trouble finishing the ubuntu 10.04 install via wubi on my T42 with the "installer encountered an unrecoverable error" msg, but everything seemed to work fine when i used the ACPI workaround option at the grub menu. 

i found this thread with an external search and thought it was quite helpful though it's somewhat old, thanks for the info.

---

### Post by mörgæs on 2011-02-20
As of now, the best troubleshooting thread for Wubi is this one:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

