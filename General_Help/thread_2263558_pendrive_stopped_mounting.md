---
title: "pendrive stopped mounting"
date: 2015-02-01
forum: General Help
---

### Post by Rixter69 on 2015-02-01
Evening:

   I have a rather strange problem. I was using a Dane-Elec 4Gb pendrive that just quit mounting. I tried several " fixes" including rebuilding the partition table and re-formatting. However, not sure if these procedures took effect since laptop won't mount the pendrive. So, I ran: badblocks -wsv /dev/sdx(x=drive designation) and after more than an hour, got readout:  1013233 done, (1012288/556896/3072 errors).
#1. Please explain readout #2. Is said drive salvageable? Now, here come the ***WEIRD***; when searching around for a 'fix" to this problem, I went to vendors website ([www.newdane.com/?page_id=673]("http://www.newdane.com/?page_id=673")) and read D-E pendrives are _*NOT*_ compatible w/ Linux/Ubuntu!!(?) Huh...? I'd used this pendrive before it's 'problem", so....? Have you ever heard of an O.S. exclusive pendrive???? I have several other makes and brands of pendrives and none (that I know of) make this claim! They all work w/Ubuntu...even the no-name "cheapies"!!! Well, there it is and I'd appreciate your feedback. And, if your willing, I have another question relating to pendrive/partitioning.
Stay Sharp:
:confused:[FONT=times new roman]***Rick***[/FONT]

---

### Post by Bucky Ball on 2015-02-01
*Thread moved to **General Help**.*

Never heard of an OS specific pen-drive. Strange they should make that claim, but not totally unusual. I've used lots of stuff that doesn't work with Ubuntu according to the manufacturer. It is more that they don't support it, I think, as in, if you ring or email, they know nothing about Linux so can't help (or do know something, but won't). A reason for this is that there are so many spins and flavours that it is hard to cover them all from a support perspective. This is probably also the reason some manufacturers just don't mention Linux at all. The hardware apparently supports Win and Mac, but no mention of Linux. Plug it into my Ubuntu box, works perfectly. *shrug*

As for the pen-drive that was working fine before and has now stopped: how old is it? What exactly happened? It was working fine, then one day you plugged it in and it no longer mounted? If you have just reformatted it and it is showing those few thousand errors, that is not a good sign. 

(PS: Please use default font size. Thanks. I have changed the font size in your first post. ;))

---

### Post by Rixter69 on 2015-02-01
Evening Bucky:

   Sorry 'bout the font size, won't happen again. Let me 'update" you. I did get the laptop/O.S. to finally recognize the pd. Immediately opened Gparted and crated partition table and formatted to FAT32. Then it still wouldn't "mount", so I ran sudo mkdir /media/iso and now it "seems" to mount it OK. However, with all my other pd's, when they are mounted, at first, the comp/O.S. makes a "space-age" noise to let you know it's mounted. With this one, it doesn't do that. I'm going to try it a few more times before I actually use it...sorta test it out, before I write anything to it, just to make sure it keeps mounting and reading.
\\:D/***[FONT=georgia][SIZE=5]Rick[/SIZE][/FONT]***

---

### Post by Bucky Ball on 2015-02-01
> **Rixter69 said:**
> 
   Sorry 'bout the font size, won't happen again.

All good. Large font can be perceived as shouting is all (as can all capitals and/or all bold). ;)

Seems you are making progress of a sort. I was wondering if it is just a very old USB dongle which might be slowly dying, but seems to be recognised now at least. Let us know how it survives. 

Just wondering why you are using FAT32. Is there a specific reason? It has limitations. NTFS is better if you are wanting to use with a Win machine, or EXT4 if not. Good luck.

---

### Post by Rixter69 on 2015-02-01
Hey Bucky:

   You know, your about the 3rd or fourth person that's mentioned using NTFS. I'll tell you why I used FAT32. I was under the impression it was more universally compatible...in other words it worked well across the board (i.e. MSWin/Mac/Linux). Then I keep hearing it has it's limitations. So, no problem, I can just re-format it to NTFS. Not that this is such a deal, but all my other pendrives makes a spaced-aged noise when mounted/unmounted. This caused question with other respondents and this pendrive, now, doesn't make those noises, as it did before? Any comments on that? One more thing, the pendrive is a 4Gb, but is showing only 3Gb available and I can't "find" anything on the drive. There shouldn't be anyhting on it for when I ran the badblocks test, it should have deleted all data. Be interested in your thoughts.
THANKS:
:-k[SIZE=5][FONT=franklin gothic medium]***Rick***[/FONT][/SIZE]

---

