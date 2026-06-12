---
title: "Help setting up an XP dual boot"
date: 2007-05-31
forum: General Help
---

### Post by helloyo on 2007-05-31
I've been Windows free for a couple of years now but want a more consistent gaming experience. I have a few questions on the best way to setup that I'm sure some of you guys could help with.

1. What version of Windows would be best? I assume XP, what version will do? 
2. How much space will I need to set aside? How will installing Windows effect my MBR?
3. I'm happy to have no internet connection setup, but what measures will I need to have in place not to get infected?
4. Anything else I should know?

Thanks a lot guys!

---

### Post by Tyke91 on 2007-05-31
1. Xp will do fine
2.i dont know how much space you have on your disk, but if you're not going to game on ubuntu (i dont anyway) then 40-50 gigs should be plenty
3. HURRAY LINUX! nobody makes viruses for ubuntu
4. I also do a dual boot for xp... you will need 2 partitions for ubuntu (total 3 partitions, XP/Root/Swap).  My computer came with 3 partitons already on it, so i had to delete one on startup (maximum 4 partitions)

you should be good :D


EDIT: just saw that you want to game on ubuntu... you probably dont. not many games are supported. Use XP for games and Ubuntu for everything else.

2 quality games that ARE native on linux:

Neverwinter Nights (all expansions) - $18

Vendetta Online  - $10 a month

---

### Post by kyphi on 2007-05-31
If you install Windows after Ubuntu it will overwrite GRUB.

My preference is to run two hard drives, one for Ubuntu and another for Windows.  If you nobble Windows so that it does not have internet access, there is no chance of a virus infection unless you introduce it via floppy or other removable media.

If you want to partition your existing hard drive, 10 - 12 Gb will be quite sufficient.

To run Windows via a virtual machine does not work for gaming.  Wine or Crossover are not sufficiently developed for gaming.  Cedega has limited success.

---

### Post by Tyke91 on 2007-05-31
I dunno if 10-16 will be quite enough... there is a good chance that he will just try to run games via wine anyway (alot [such as WoW] will work) and since the original install will take up 2 or so gigs to start up with, 8-14 is not much for what he wants to do..


40-50 was probably too high for me, but i intend to do a full crossover eventually and i wanted to ensure i had enough space for everything ;)

---

### Post by shijirou on 2007-05-31
Remember that if you are going to do gaming, you need some space for window's virtual swap file as it uses this a lot in gaming so try to partition at least 20 gig for windows. Plus in all my years and experience in using Windows, it tends to slow down when you overcrowd your hard drive even after a defrag.

On my windows machine I have allocated 4 gig of space for the swap file and everything else is space for games.

---

### Post by freefromXP on 2007-06-01
I still Dual boot for Gaming.  My XP partion is 60G and has 40g of gameing it's just games, T/s and almost all services turned off.  I even removed Eplorer so I have no browser I don't need to access the web and get crap on my sys I don't want.

   I am building a new machin and I have a KVM switch so I can have both gaming and Offcie sys up  at same time :p:D

---

### Post by helloyo on 2007-06-01
thanks guys! if i do want to connect to the internet in windoze, what firewall/antivirus/etc would you guys recommend.

starting to remember why i haven't run XP in years...

---

### Post by Haulnbones on 2008-06-24
> **helloyo said:**
> thanks guys! if i do want to connect to the internet in windoze, what firewall/antivirus/etc would you guys recommend.

starting to remember why i haven't run XP in years...

If you're not going to connect to the internet, don't waste your time/money on an antivirus. They only slow your system down more. Use SP3 and Windows Firewall, and some form of hardware Firewall and you'll be fine. I've been running that configuration with SP2 for years and haven't had any virus problems.

---

### Post by heartburnkid on 2008-06-24
> **helloyo said:**
> thanks guys! if i do want to connect to the internet in windoze, what firewall/antivirus/etc would you guys recommend.

starting to remember why i haven't run XP in years...

Yeah, after 4 blissfully Windows-free months, I just set up a dual-boot to run Spore Creature Creator... I feel your pain.

Anyway, for firewall, I still stick with ZoneAlarm Free.  It's not quite the shining star it was, but it still delivers basic protection on the cheap.

Antivirus/Antimalware, I go with Avast and Spybot in combination.  Avast is a bit sluggish, but doesn't seem to affect performance too badly in tray mode.  For a lower-end system, substitute Avira for Avast; it's much snappier, and has good detection rates.  Only problem with Avira is that it pops up a giant ad for the Pro version when you update; however, this can be done away with with a little permissions hacking (take away the execute permission from avnotify.exe).  Well, that, and it doesn't have an integrated anti-malware scanner like Avast.  Still, you've got Spybot for that, so you're at least somewhat covered.

All the products I mention above are free-as-in-beer.

---

### Post by djsephiroth on 2009-02-12
> **Haulnbones said:**
> If you're not going to connect to the internet, don't waste your time/money on an antivirus. They only slow your system down more. Use SP3 and Windows Firewall, and some form of hardware Firewall and you'll be fine. I've been running that configuration with SP2 for years and haven't had any virus problems.
Antivirus != firewall. You will want an anti-malware app. I recommend AVG Free and Spybot running concurrently. They're both very lightweight, and free to boot.

Soft firewalls are dubious countermeasures. A hardware firewall is kind of overkill, though, so using Windows Firewall may be useful. PeerGuardian2, often seen simply as a way of not getting caught when torrenting warez, is rather useful as a port-blocker, and I daresay it does a great job.

---

