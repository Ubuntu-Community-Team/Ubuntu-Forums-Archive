---
title: "Grub menu.lst problem"
date: 2007-04-28
forum: General Help
---

### Post by Gregy1727 on 2007-04-28
Hi I've recently installed Feisty Fawn and I have the following problem:

I have this dual booted with Windows Vista, the problem is grub did not detect it during install. I have tried to add it to menu.lst myself, but it just keeps saying "starting up"

my menu.lst entry

```
title           Windows Vista
root            (hd0,6)
chainloader     +1

```

my fdisk output:

```
/dev/sda1   *           1         390     3132643+  83  Linux
/dev/sda2            1217       24321   185590912+   f  W95 Ext'd (LBA)
/dev/sda5            1217        1340      995967   82  Linux swap / Solaris
/dev/sda6           11196       16294    40957655    7  HPFS/NTFS
/dev/sda7           16295       24321    64476846    7  HPFS/NTFS

```


sda7 is the vista partition, can you help me on this?

---

### Post by m.musashi on 2007-04-29
For what it's worth, mine looks like this
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
I also know that Windoes never liked being on a partition other than the first one. Maybe vista is better about this but I don't know.

---

### Post by Herman on 2007-04-29
Hello Gregy1727,
 I hate to give anyone bad news, but it's better than letting you remain frustrated and waste a lot of time on this.  I don't think it's possible to boot Windows when it's in a logical partition. ..unless I'm wrong and I hope I am wrong here. 
It isn't Ubuntu's or Grub's fault Windows can't boot, it's Windows own fault.

Here is a link you should read about multibooting Windows, [MultiBooting Principles.]("http://www.goodells.net/multiboot/principles.htm")

Here is the home page of that site, [[COLOR=#0000bb]Understanding MultiBooting and Booting Windows from an Extended Partition by Dan Goodell[/COLOR]]("http://www.goodells.net/multiboot/index.htm")

I'm only guessing, but I think you probably had a Windows multi or dual boot set up by the Windows default method and maybe you deleted the Windows 'boot' partition and installed Ubuntu there in the primary partition instead.
Windows is still carrying on the same stupidity even with Vista, from what I read. It's really disgusting that they treat their customers like that, not informing you of the hazards of their silly method of dual booting.

Grub is a far superior boot loader and manager than anything Windows can come up with. If you need to rescue your files and re-install Windows, next time install one Windows, then install Ubuntu and use Grub for a 'third party boot manager', (as described in the links I provided earlier). That way you can use Grub's 'hide' and 'unhide' commands to allow you to install multiple Windows in a much more intelligent way than microsoft's default method. 
Regards, Herman

---

### Post by elijahclarity on 2007-05-06
Thanks.....that info helped. I think I'll have to use a 3rd party boot manager, or install XP on primary partition. Can u recommend a good boot manager??

---

### Post by Herman on 2007-05-06
Yes, [GAG Boot Manager]("http://gag.sourceforge.net/") or Grub , either are really good. GAG doesn't need an operating system to work from, it installs in the MBR and in first track of the hard disk.

[Super Grub Disk]("http://supergrub.forjamari.linex.org/") can hide and unhide Windows partitions too, but it isn't made to be installed and used on a permanent basis.

If you have at least one Linux installation already,(Ubuntu), you can use Grub to hide and unhide Windows partitions. That's what Grub's hide and unhide commands are for.
For example if you had two Windows installations in two primary partitions in the first hard disk and Linux (Ubuntu) was somewhere else, you would add hide and unhide commands to the Linux system's grub menu like this,
```
title     Microsoft Windows 95
hide      (hd0,1)
unhide    (hd0,0)
root      (hd0,0)
savedefault
makeactive
chainloader +1

title      Microsoft Windows 98SE
unhide     (hd0,1)
hide       (hd0,0)
root       (hd0,1)
savedefault
makeactive
chainloader +1
```Regards, Herman :)

---

