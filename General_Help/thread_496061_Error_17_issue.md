---
title: "Error 17 issue"
date: 2007-07-08
forum: General Help
---

### Post by lgardner on 2007-07-08
I recently tried to set up a dual-boot system on my laptop. I had vista already installed beforehand, set up a partition for Ubuntu and installed Ubuntu to that partition. Unfortunetely, I was unable to get Ubuntu to work properly. I kept getting the "Ubuntu black screen of death." I got frustrated and decided to try again at a later time.

And so i continued using my vista partition, but i wanted to reclaim the space used for the Ubuntu partition, and so i deleted that partition. Unfortunetely, GRUB is still installed, and now every time I try to boot my computer I get this.



Grub 1.5

Loading Grub.....

Error 17


I'm using the family PC for now but i'm really worried about my laptop. I did some googling and found some solutions using the fixmbr function but it doesn't seem to work with Vista. Can anyone help? I'm desperate.

---

### Post by confused57 on 2007-07-08
> **lgardner said:**
> I recently tried to set up a dual-boot system on my laptop. I had vista already installed beforehand, set up a partition for Ubuntu and installed Ubuntu to that partition. Unfortunetely, I was unable to get Ubuntu to work properly. I kept getting the "Ubuntu black screen of death." I got frustrated and decided to try again at a later time.

And so i continued using my vista partition, but i wanted to reclaim the space used for the Ubuntu partition, and so i deleted that partition. Unfortunetely, GRUB is still installed, and now every time I try to boot my computer I get this.



Grub 1.5

Loading Grub.....

Error 17


I'm using the family PC for now but i'm really worried about my laptop. I did some googling and found some solutions using the fixmbr function but it doesn't seem to work with Vista. Can anyone help? I'm desperate.

If you have a Vista install DVD(not a recovery disk), I think there is an option to repair the mbr...however, if you don't have an install DVD, I would recommend you try reinstalling Ubuntu, then download the MbrFix.exe utility to repair Vista's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://www.users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)
there are instructions on the MbrFix.exe download site to repair Vista's mbr

What kind of video card does your laptop have?  That may be why you're getting the black screen, may just be a matter of selecting the correct video driver in Ubuntu.

---

