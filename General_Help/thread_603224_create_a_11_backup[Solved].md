---
title: "create a 1:1 backup[Solved]"
date: 2007-11-04
forum: General Help
---

### Post by etharis on 2007-11-04
I want to backup my 80 gig laptop drive. It runs Ubuntu 7.10 and XP pro. In a perfect world I would be able to boot up using a 3rd party piece of software create a 1:1 image of everything on my hd, that would maintain filesystems and partitions and if something were to go wrong i could just insert 3rd party software again and restore the 80 gig image. (i had planned to back it up on to an external). This is perfect world scenario.. And the world is not perfect..

I was just wondering if someone could point me in the proper direction about how to get started...
Thanks

---

### Post by HermanAB on 2007-11-04
Clonezilla.

Cheers,

Herman

---

### Post by wieman01 on 2007-11-04
Partimage.

See my signature.

---

### Post by ubuntology on 2007-11-04
Something else to try: [http://sourceforge.net/projects/freeghost/](http://sourceforge.net/projects/freeghost/)

---

### Post by etharis on 2007-11-05
Once again Ubuntu community you have served me well. Thanks :)

---

### Post by jromer on 2007-11-10
I triple boot xp, Ubuntu 6.06 and Ubuntu 7.10. I've used Acronis 10 to backup all partitions and MBR.

I've always been looking for a Linux alternative. I thought Clonzilla might be the answer...here's my experience:

Used Clonzilla 1.0.5-8 live CD.

Backed up all partitions and MBR. All looked OK.

When I restored however, all partitions were properly restored, but MBR only showed options for WinXP and Ubuntu 6.06. No option were available for 7.10. (Not sure what this would be.)

I had to go back to Acronis to properly restore MBR record. (I had used Acronis to backup my system prior to testing Clonezilla)

*** I've since learned that I had to turn off the default option that writes the MBR record when Clonezilla restores.
 So I have now tested both the backup and restore successfully!

---

