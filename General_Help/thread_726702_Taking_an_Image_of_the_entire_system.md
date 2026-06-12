---
title: "Taking an Image of the entire system"
date: 2008-03-17
forum: General Help
---

### Post by neojags on 2008-03-17
hi,

I have winxp and ubuntu both installed perfectly and running fine. Now i want to take the image of the entire hard disk containing ubuntu and winxp including the grub on to a dvd so that i can restore to this config when harddisk crashes . How do i do that?

jags

---

### Post by thinkdez on 2008-03-17
As you want to backup the MBR I can recommend using Acronis True Image.  I have used it in the past and it worked flawlessly.  It was easy to use and I was very happy with it as it saved my butt on more than one occasion.  The caveat to this is that its not open source and not free.  I found an alternative to this called Self Image however I have not used it nor can I say that it works well.  If you have a spare disk to test it out I am sure we would all like to hear how well it worked for you.

Both of these programs have the ability to image the disk from a live state but I would recommend that you use a live boot disk to image the system just to make sure.  I know windows can act finicky when an image is taken from a live state.  I know Acronis has this ability. 

I believe there are many other programs that do this but I believe Self Image and Acronis are the kind of software your looking for

Self Image - [http://selfimage.excelcia.org/]("http://selfimage.excelcia.org/") 

Acronis - [http://www.acronis.com/homecomputing/products/trueimage/]("http://www.acronis.com/homecomputing/products/trueimage/")

---

### Post by trippinnik on 2008-03-17
you could use partimage, it will take a full disk image of your partitions.  you'll need to run it off a live disk though since you can't mount the drives you want to take images of when you use it.  it can then save the compressed images onto another drive for later use.

---

### Post by jonabyte on 2008-03-17
Just saw this in an article:

[clonezilla]("http://clonezilla.sourceforge.net/")

---

