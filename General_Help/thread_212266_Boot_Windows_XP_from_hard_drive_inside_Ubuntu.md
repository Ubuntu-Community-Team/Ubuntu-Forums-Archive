---
title: "Boot Windows XP from hard drive inside Ubuntu"
date: 2006-07-09
forum: General Help
---

### Post by geetarista on 2006-07-09
I've been searching trying to figure this one out for a while, so now I've decided to post on it.  I am dual-booting Windows XP and Ubuntu Dapper on separate hard drives.  I love Ubuntu, but I still need Internet Explorer and Outlook Express for a couple of things and there's really no way around it.  I tried using Crossover Office and Wine, and tried to download IE and OE, but neither of them worked.  I seriously spent hours with each program trying to make them work but to no avail.  I was wondering if there is a way that I could boot Windows while I'm still inside Ubuntu.  I'm just trying to find the easiest solution so I don't have to reboot my computer each time I need IE/OE.  If possible, I'd just like to pop it up, use it, and get back out again.  I've been reading about vmware and how it can boot Windows inside a window, but I haven't seen anything 'bout using an existing installation.

If anyone could help me out here I'd really appreciate it!  I couldn't find any thread that discussed this, but the search in these forums doesn't really work that well either.

---

### Post by jimmygoon on 2006-07-09
> **geetarista said:**
> I've been searching trying to figure this one out for a while, so now I've decided to post on it.  I am dual-booting Windows XP and Ubuntu Dapper on separate hard drives.  I love Ubuntu, but I still need Internet Explorer and Outlook Express for a couple of things and there's really no way around it.  I tried using Crossover Office and Wine, and tried to download IE and OE, but neither of them worked.  I seriously spent hours with each program trying to make them work but to no avail.  I was wondering if there is a way that I could boot Windows while I'm still inside Ubuntu.  I'm just trying to find the easiest solution so I don't have to reboot my computer each time I need IE/OE.  If possible, I'd just like to pop it up, use it, and get back out again.  I've been reading about vmware and how it can boot Windows inside a window, but I haven't seen anything 'bout using an existing installation.

If anyone could help me out here I'd really appreciate it!  I couldn't find any thread that discussed this, but the search in these forums doesn't really work that well either.

I can't help much with virtualization (which would be a good search term fo ryou to use) but I can tell you that I've gotten wine to run IE fairly reliably using: [http://sidenet.ddo.jp/winetips/config.html](http://sidenet.ddo.jp/winetips/config.html)

---

### Post by mbeierl on 2006-07-10
VMWare Workstation can boot raw partitions (as in an existing Windows install) but there may be some issues:

[LIST=1]
[*]Boot loader - you need to make sure it doesn't automatically boot into the same Ubuntu image that you are currently running.  That would be BAD (tm)
[*]Windows activation - Windows might see the vmware bios, etc, as a significant change and want you to activate it.  Alternatively, It Just Might Crash, because the hal is not expecting new hardware.
[/LIST]

I used to do this years ago with VMWare 2.0 and it worked excellently, but I can't anymore due to my laptop using SATA, which appears as SCSI, and VMWare cannot use SCSI as a raw disk.

Hope this helps.

---

### Post by matrooswolf on 2006-07-10
I have not tried this myself, so I wash my hands in innocence, but:
[http://www.ubuntuforums.org/showpost.php?p=1117645&postcount=131](http://www.ubuntuforums.org/showpost.php?p=1117645&postcount=131)

---

