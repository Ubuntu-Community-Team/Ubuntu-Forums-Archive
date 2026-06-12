---
title: "Restore GRUB after Vista"
date: 2007-02-05
forum: General Help
---

### Post by xjas05 on 2007-02-05
Today i installed the largest virus available: Vista. the god damned piece of CRAP raped my MBR without ANY sort of god damn prompt at all, and after doing some googling, nothing is working for me to restore GRUB, I want to know, how can i make GRUB work again? I'm going to get rid of that god damned virus as soon as i get GRUB to work.. how pathetic it is indeed..

---

### Post by r4ik on 2007-02-05
Try,

[http://www.ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub](http://www.ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub)

Good luck !

---

### Post by xjas05 on 2007-02-05
I tried that... i sat here for 15 minutes trying to hit "Forward" and it won't let me continue, i HAVE to check the "Reformat" checkboxes to go any further...

---

### Post by MiCovran on 2007-02-05
Try: [http://www.arsgeek.com/?p=655](http://www.arsgeek.com/?p=655)

---

### Post by ashmew2 on 2007-02-05
Why dont you try this method :
1)Load up Live Session from Live CD
2)Open a terminal
3)Type these commands :

```
sudo grub
 find /boot/grub/stage1
 root (hd0,x)
 setup (hd0)
 quit

```
4)Reboot.

Replace the (0,x) with what it returned to u when u did find /boot/grub/stage1

---

### Post by xjas05 on 2007-02-05
that's what i am doing, but i'm still not seeing GRUB, it just goes straight into windoze... tried about 3 times now, nothing..

---

### Post by xjas05 on 2007-02-06
this is what i'm getting in terminal:

```

 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,0) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

```

where to go from here?

---

### Post by jonnymccullagh on 2007-02-06
Just a suggestion but I recently had trouble with my MBR and Windows (not Vista).
I found that Super Grub Disk did the trick for me:
[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")
Just an idea,
j

---

### Post by xjas05 on 2007-02-06
just tried that, twice, attempted to restore GRUB to mbr, and then also tried to boot into Ubuntu, both times, fail, i **HATE WINDOWS SO BAD**. why is this so hard? all i'm trying to do is fix a MBR.. and nothing is working.... shouldn't ubuntu have an option on the CD to restore boot loader?...i was surprised to not find such an option..

---

### Post by xjas05 on 2007-02-06
okay.. so i messed with it some more, and got it to boot into ubuntu... thanks a LOT for getting me out of that HORRIBLE windows environment... half of the problem still remains though.. need to get GRUB functioning properly...

---

### Post by jonnymccullagh on 2007-02-06
Can you tell us what you did? It might help others who come after you.

---

### Post by siucdude on 2007-02-07
> **ashmew2 said:**
> Why dont you try this method :
1)Load up Live Session from Live CD
2)Open a terminal
3)Type these commands :

```
sudo grub
 find /boot/grub/stage1
 root (hd0,x)
 setup (hd0)
 quit

```
4)Reboot.

Replace the (0,x) with what it returned to u when u did find /boot/grub/stage1

I just wanted to say thank you this worked great, and Let everyone know I love Ubuntu.

Thanks

---

### Post by mobilehavoc on 2007-02-07
> **siucdude said:**
> I just wanted to say thank you this worked great, and Let everyone know I love Ubuntu.

Thanks
Just so I understand it correctly...I currently have XP and Edgy dual-booting...

If I install Vista over XP it'll obviously rewrite the MBR...THEN if I follow the steps in this thread, it'll reinstall grub which will let me get back into Ubuntu BUT...

When I do this setup will it setup grub to allow dual-booting with Vista or is that a separate step. I definitely want to keep using Ubuntu but I don't want to mess up the dual-booting with Windows either...

---

### Post by siucdude on 2007-02-13
> **mobilehavoc said:**
> Just so I understand it correctly...I currently have XP and Edgy dual-booting...

If I install Vista over XP it'll obviously rewrite the MBR...THEN if I follow the steps in this thread, it'll reinstall grub which will let me get back into Ubuntu BUT...

When I do this setup will it setup grub to allow dual-booting with Vista or is that a separate step. I definitely want to keep using Ubuntu but I don't want to mess up the dual-booting with Windows either...

I was dual booting XP and Ubuntu, I have it on two different hard disks, I then Installed Vista over XP and did the steps here, and I was back to dual boot grub menu with Vista and Ubuntu.

Hope it works for you.

TJ

---

