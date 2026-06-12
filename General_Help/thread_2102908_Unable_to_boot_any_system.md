---
title: "Unable to boot any system"
date: 2013-01-08
forum: General Help
---

### Post by lucas006 on 2013-01-08
Hello. Yesterday I have installed 64 bit Ubuntu 12.10. I had problems with booting Windows 7 (here is thread - [http://ubuntuforums.org/showthread.php?t=2102460](http://ubuntuforums.org/showthread.php?t=2102460)). Anyway, with support  problem has been solved, but new occurred...
Today I started Ubuntu. After some hours I decided to run Windows, so I clicked "Restart...". After restart there wasn't grub, just blinking **[COLOR=SeaGreen]_[/COLOR]**. I decided to use boot-repair from Ubuntu 12.10 live usb, but problem still occurs, so I can't boot any operating system. 
(boot-repair log files are in attachment).

Regards, lucas006.

---

### Post by oldfred on 2013-01-08
It looks like Boot-Repair had some sort of error. Do you not have an Internet connection? Boot-Repair usually needs that to download a correct grub or other app to complete fix.

Try re-running it, but post link it gives you not all the files.

---

### Post by lucas006 on 2013-01-08
I have internet connection. I used boot-repair again (with internet connection)  and nothing, still blinking _.
Here is log: [http://paste.ubuntu.com/1511173](http://paste.ubuntu.com/1511173)

As always two messages prompted:
First:
"LDM-blocker detected. Please backup your data before this operation. Do you want to continue?"
Second:
"LDM-blocker detected. This will delete the 6th sector of sda. Do you want to continue?"
I choosed "No" two times. Should I choose "Yes"?

---

### Post by oldfred on 2013-01-08
Did you have dynamic partitions?

I had not heard of LDM until this bug was posted.
       ldm bug grub2 2.00
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)


Just went back and looked at your other thread. If you have good backups I would say yes. But I do not think bug report had a specific way to remove the old ldm info, just work arounds on booting.

---

### Post by lucas006 on 2013-01-09
Okay I successfully restored grub menu and booted Windows ;)
I used Boot-Repair but this time I decided to go Advanced Options and check "purge GRUB before reinstalling it". As always it prompted LDM blocker message, for tests (due to using purge GRUB option) again I choosed "no".
After reboot grub menu appeared. But when I tried to boot Windows it prompted "disk read error" Ubuntu could be booted normally. So I added new menuentry to GRUB (by editing 40_custom) with Windows 7. Right now I can boot Ubuntu and Windows.

If you need here is logfile with "purge GRUB" option enabled (but it is before adding new menuentry): [http://paste.ubuntu.com/1513149](http://paste.ubuntu.com/1513149)

I hope grub won't broke suddenly (like last time after using Ubuntu few hours).

Thanks for help.

---

### Post by oleink on 2013-01-09
> **lucas006 said:**
> Okay I successfully restored grub menu and booted Windows ;)
I used Boot-Repair but this time I decided to go Advanced Options and check "purge GRUB before reinstalling it". As always it prompted LDM blocker message, for tests (due to using purge GRUB option) again I choosed "no".
After reboot grub menu appeared. But when I tried to boot Windows it prompted "disk read error" Ubuntu could be booted normally. So I added new menuentry to GRUB (by editing 40_custom) with Windows 7. Right now I can boot Ubuntu and Windows.

If you need here is logfile with "purge GRUB" option enabled (but it is before adding new menuentry): [http://paste.ubuntu.com/1513149](http://paste.ubuntu.com/1513149)

I hope grub won't broke suddenly (like last time after using Ubuntu few hours).

Thanks for help.


Never EVER attempt to repair grub without doing exactly what you did this last time.  GRUB can be a pain in the neck sometimes especially when packages break themselves.  Also thanks for the config file.  Not too many people have luck finding them as guidelines for their own config files when they are new to GRUB

---

### Post by serpantman on 2013-01-09
If grub gives you trouble i'd suggest trying lilo, i prefer it to grub.

---

