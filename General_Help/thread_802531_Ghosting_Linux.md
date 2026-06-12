---
title: "Ghosting Linux"
date: 2008-05-21
forum: General Help
---

### Post by boyce1 on 2008-05-21
Ok, so i have messed up my linux a few times. I've finally realised it would be a good idea to backup my linux, just incase i mess it up to the point where i can't fix it :)


I tried using Clonezilla to make an image, but it seems i can't copy a mounted harddrive. I only have one harddrive, with one OS. How can i copy it? 

any help will be appreciated. thanks.

---

### Post by SPr on 2008-05-21
You'll have to make a live CD and boot from it. Take a look at the Clonezilla home page for a link to the live CD page. Sorry, but I don't seem able to give a direct link.

[Clonzilla home page](www.clonezilla.org/)

---

### Post by boyce1 on 2008-05-21
i have a clonezilla livecd, and its fine until at one point it says " cannot make an image of a disk thats mounted", and it stops.

---

### Post by SPr on 2008-05-21
Sorry, because the HDD was mounted I assumed you were running it from the same HDD.

Hmmm, do you have access to the command line in the live CD? Have you tried unmounting the HDD?

If Clonezilla is automatically mounting the HDD it could be because it needs somewhere to write the image and chooses the HDD or perhaps it might be a bug.

I've never used Clonezila so I can't help any more.

---

### Post by boyce1 on 2008-05-21
ok, do you advise any other software to do this?

---

### Post by SPr on 2008-05-21
I use Partimage on [SystemRescueCD](www.sysresccd.org/). I've used it successfully many times (when I started using Ubuntu I decided to image my HDD rather keep reinstalling. The need to reinstall will gradually fade away.)

One thing to point out though is that if you repartition the HDD at any time Partimage wont be able to write the old images to the new sized partitions correctly.

There are many useful tools on SystemRescueCD and it could save much trouble sometime :)

---

### Post by boyce1 on 2008-05-21
so is it a case of booting from that CD, and writing an image? and would that image have to be written to something such as an external hardrive?

---

### Post by SPr on 2008-05-21
Boot from the CD. The image will have to be written to another partition on the same HDD or another HDD, flashdrive etc.

---

