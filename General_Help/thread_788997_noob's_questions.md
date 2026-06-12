---
title: "noob's questions"
date: 2008-05-10
forum: General Help
---

### Post by Dimitris.Salonika on 2008-05-10
since this is my first post,i would like to say "hi"to everyone and that i am glad to be here and a linux user.

   Recently (before 3 months) i started using linux (open.SUSE 10.3) from microsoft XP and now i am excited with linux.Furthermore i would like
to start using ubuntu (8.04) because as i said i am new to these and i have read in internet it's more user-friendly and with bigger community.

    I've ordered my new PC and i was wondering:
1.CPU is intel's Dual Core E2200 @ 2,2-should i choose x86 architecture or   
  64bit ubuntu?
2.Can i have 4 GB RAM with ubuntu?(I assume you are familiar with the 
  windows XPx86 problems)
3.Is ubuntu 8.04 compatible with nvidia series 8 graphic cards?
4.Disk Partitioning should be done with installation or later with a 
  specific program(like windows XP)? 
5.With windows XP ,choosing the file system was easy(NTFS),Now with 
  open.SUSE i was lost (i think ext3 is better).witch file system should
  i choose with ubuntu?
6.Is it possible with the above hardware(graphic card's GPU is 8500) to 
  watch high definition video in my PC smoothly (with ubuntu of course)?

  thanks in advance.


P.S.:Sorry for my bad english  and if these questions have already been 
     answered in an other thread witch i didn't found.

---

### Post by Fixel on 2008-05-10
Answering the questions I know the answer to:
1. I'm running the 64bit version with no troubles what so ever...
2. 4 gig shows up in the 64bit version for me.
3. Yes
4. You can do it when installing (the livecd has a partitioner and if you choose "manual" (partitioning when installing you can make all the partitions, even ntfs ones.
5. ext3 definetely for your core system... Here's my set-up: One 40 gig ext3 partition and one 20 gig hfs+ (mac) and one 110 gig NTFS for media.
6. Yes. (1080p runs smoothly for me... althou I usually watch 720p because of the resolution on my monitor)

---

### Post by Fixel on 2008-05-10
Forgot to say.. when I installed with a 8600m gfx card I had to use an alternate install cd (still easy to do)..

and then I had to edit the /etc/X11/xorg.conf to say "vesa" (gfx standard) instead of "nvidia"

all this was really simple

---

### Post by Dimitris.Salonika on 2008-05-10
thanks but what do you mean "an alternate cd"?I've just get used to open.SUSE's RPM
and i am not familiar with ubuntu's instalation programs.

---

