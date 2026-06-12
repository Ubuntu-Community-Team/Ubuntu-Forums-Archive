---
title: "How much trouble will I get myself in, if..."
date: 2014-04-08
forum: General Help
---

### Post by Tom Collier on 2014-04-08
1. I do a complete backup of my current 12.04.4 installation (even the trash folder), then
2. I scrub my current dual-boot Win7/12.04 installation because GRUB and boot-repair did a weird thing that gives me 7 (!) partitions; or
3. I did it in my ignorance, however....I finally got the Ubuntu side back up and running after several hours of futzing around with boot-repair; then
4. I do a clean re-install of 12.04 and of 12.04 only; no more Windows 'cause I only used it to run some PortableApps off a thumb drive;
5. Then I do a complete restore of the backup from Ubuntu 1, (before they cut and run);

Will I get my applications and files back, and restored to where they belong?

I'm one of those guys who just uses my computer to churn out deliverables to clients; I stick with LTS installations because tinkering and fiddling steals time from making money, so...

Yes? No! Don't do it! Maybe?

Thanks in advance to those of you wiser than I in the ways of the cyber-innards...

---

### Post by Mark Phelps on 2014-04-08
>  I only used it to run some PortableApps off a thumb drive;

OK ... but Windows portable apps are NOT going to run in Ubuntu.  Just so you know.

---

### Post by Tom Collier on 2014-04-08
Yep, PortableApps never have run in Ubuntu. That was the only reason I kept Windows in the dual boot setup.

---

### Post by CaptainMark on 2014-04-09
We can't really tell you how much you're likely to need Windows in the future obviously but other than that I see no reason not to do this. Just make sure you backup to portable media. You could install Windows to Virtualbox just in case.

---

### Post by monkeybrain20122 on 2014-04-09
Your applications will not be back if you do a clean install and only restore your /home from backup. Your settings will be kept though when you reinstall the applications.

---

### Post by Bucky Ball on 2014-04-09
Go for Clonezilla. It will make a direct copy of the partition(s) (or entire disk) and then put it back as is, or was ...

[http://clonezilla.org/](http://clonezilla.org/)

Used it recently on my desktop when I replaced the OS hard drive with an SSD. Did the lot, including my XP partition, not that you want/need that anymore. Good luck. ;)

PS: Now you're backed up, you can also just boot from a Live CD (or Gparted CD) and kill the Win partition, then use boot repair to reinstall grub. That option is in 'Advanced Options'.

---

### Post by monkeybrain20122 on 2014-04-09
> **Bucky Ball said:**
> Go for Clonezilla. It will make a direct copy of the partition(s) (or entire disk) and then put it back as is, or was ...

[http://clonezilla.org/](http://clonezilla.org/)

Used it recently on my desktop when I replaced the OS hard drive with an SSD. Did the lot, including my XP partition, not that you want/need that anymore. Good luck. ;)

PS: Now you're backed up, you can also just boot from a Live CD (or Gparted CD) and kill the Win partition, then use boot repair to reinstall grub. That option is in 'Advanced Options'.

Yeah but OP doesn't want to clone the whole disk, if I understand correctly the point is to restructure the disk and keep only Ubuntu. I am not even sure if he wants to keep the system part of Ubuntu because something is messed up from what I gathered (though it is not very clear) 

Operations that involve restructuring disk and restoring selective partitions are ideal for fsarchiver (provided you don't get into some inflexible setup like gpt or uefi etc), Clonezilla is only good for straight forward backup/restore and if you have big enough drive to restore to.

---

### Post by Tom Collier on 2014-04-09
Thanks! This has all been helpful and why I so admire this community and forum.

I'm going to experiment with Clonezilla before I do this.  I just wish I had a can of WindowsBeGone that I could spray on my computer.

Every time I attempt partition editing or try to work with GRUB or to use boot-repair, even when I follow the step-by-step tutorials dredged up with Google,  I get cryptic exceptions that I'm simply unequipped to deal with because I don't have the knowledge, nor the time to spend acquiring it.

I learned about UEFI the hard way, as I bricked a laptop that came with Win8 preinstalled. I special-ordered the one I have now with Win7, (HP i7, 16GB RAM, 1TB hard drive) but the dual boot process even on this one, created an oddball partition situation that I don't really understand. But it worked and I could get into both sides when needed, so I just trudged along until a refusal to boot into Windows yesterday.

Thanks again to everyone. Ima mark this one "Solved."

---

