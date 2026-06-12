---
title: "sound drivers all over the root?"
date: 2018-04-04
forum: General Help
---

### Post by ulao3 on 2018-04-04
I noticed today I have driver fragments (I think) on the root of my drive. I do not have a need for sound nor have I ever. Thus, I'm not really sure how these file got here. I was thinking maybe it was for the plex server but removing that didnt clean this up. Any ideas?


my / dir
audio     console  etc             lib         loop6       midi02  mixer3      ptmx   ram13  ram6    rmidi3     smpte1   sys   tty5     vmlinuz
audio1    core     fd              libnss3.so  loop7       midi03  mnt         pts    ram14  ram7    root       smpte2   tmp   tty6     vmlinuz.old
audio2    dev      forcefsk        loop0       lost+found  midi1   mpu401data  ram    ram15  ram8    run        smpte3   tty   tty7     webmin-setup.out
audio3    drivers  full            loop1       media       midi2   mpu401stat  ram0   ram16  ram9    sbin       sndstat  tty0  tty8     zero
audioctl  dsp      home            loop2       mem         midi3   null        ram1   ram2   random  selinux    srv      tty1  tty9
bin       dsp1     initrd.img      loop3       midi0       mixer   opt         ram10  ram3   rmidi0  sequencer  stderr   tty2  urandom
boot      dsp2     initrd.img.old  loop4       midi00      mixer1  port        ram11  ram4   rmidi1  shm        stdin    tty3  usr
cdrom     dsp3     kmem            loop5       midi01      mixer2  proc        ram12  ram5   rmidi2  smpte0     stdout   tty4  var

---

### Post by spjackson on 2018-04-04
Many of the files in that list look like what belongs in /dev. Perhaps it's the result of a faulty cp command or similar.

---

### Post by ulao3 on 2018-04-04
Its nothing I did, and I don't think its footprints of a hack? I could just remove them but i'd like to know exactly what to remove. Says created by users audio ?

I guess I could

find / -user audio-exec rm -fr {} \;

?

I see what you mean, all dev files. I'll just remove dups. Thx.

---

