---
title: "Dual Boot"
date: 2008-04-30
forum: General Help
---

### Post by mitchell486 on 2008-04-30
I have my computer set up to boot from Vista on my primary SATA hard drive and I would like to be able to dual boot with Ubuntu on my second hard drive. My first is a SATA. My second is an IDE. Is it in the BIOS that I need to do this switch or is it a program that I need to get to be able to dual boot. I want to be able to switch even maybe while running one. I have Virtual Machine but I didn't know if that's what I wanted to use. Any help would be wonderful. Because right now all my system does is boot to my Vista SATA instead of giving me an option when booting up.

Thanks guys in advance. :)

EDIT:I would like the main selection at the boot screen. Preferably with about a 30 second delay to decide which I want.

---

### Post by mitchell486 on 2008-04-30
Bump. I need help please.

---

### Post by SendDerek on 2008-04-30
Not to be rude or anything, but this is a topic that has been discussed about a thousand times before.  And each time somebody asks, it's generally because they didn't do a search first.  So, the support you get might not be the greatest...

Anyways, here's what I can offer.

My google search for you:
[http://www.google.com/search?q=vista+ubuntu+dual+boot+how+to+sata+ide&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=vista+ubuntu+dual+boot+how+to+sata+ide&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

A promising tutorial:
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

More tutorials:
[http://nighthacker.net/how-to-dual-boot-vista-and-ubuntu-gutsy710/](http://nighthacker.net/how-to-dual-boot-vista-and-ubuntu-gutsy710/)
[http://howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)
[http://ubuntuforums.org/showthread.php?t=207870](http://ubuntuforums.org/showthread.php?t=207870)

Take your pick. The principles apply to SATA, IDE, and both SATA and IDE hard drive setups.

---

### Post by mitchell486 on 2008-04-30
Thank you. I DID however do a quick search. I just was unable to find anything helpful. I will sift through your suggestions and report back. Thank you. I saw on these forums that it has been discussed a billion times. But none of them were the answers that I wanted. I would like it to be an option at the boot screen. Not have linux boot first and then be able to switch to windows. Thank you though. I will look through those. Thank you again.

---

### Post by mitchell486 on 2008-04-30
> **SendDerek said:**
> Not to be rude or anything, but this is a topic that has been discussed about a thousand times before.  And each time somebody asks, it's generally because they didn't do a search first.  So, the support you get might not be the greatest...



I am sad to report back to you, not to be rude, but you did not read what I asked. My question seems to be different than others in the respect that I want to have it a the boot screen have an option. Not just boot to one or the other. And so now I have a handful of useless links because those did nothing. 90% of those links were for just ONE hard drive. Not even a SATA and an IDE. But a couple were for multiple hard drives but had no options of what I asked. I ask for the option to select which HDD to boot from at the boot screen with about a 30 second pause or so while I decide. But thank you for at least trying. If anyone can help with my specific problem please let me know. Thank you.

---

### Post by oygle on 2008-04-30
mitchell486 - See [this post]("http://ubuntuforums.org/showthread.php?t=577185")

You just want to do the opposite, default boot Vista, and the second grub boot option to be Ubuntu. So the very last part of your menu.1st should be (I think ?)

```

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Ubuntu 8.04
map             (hd0) (hd1)
map             (hd1) (hd0)
root            (hd1,0)
savedefault
makeactive
chainloader   +1

```

I _think_ you would also have to be modifying the lines befre that set (above), the ones above the line marked "DEBIAN AUTOMAGIC KERNELS LIST".

---

