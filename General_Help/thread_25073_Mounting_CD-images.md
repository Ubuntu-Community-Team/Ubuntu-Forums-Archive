---
title: "Mounting CD-images"
date: 2005-04-09
forum: General Help
---

### Post by xodeus on 2005-04-09
Hi I would like to know how to mount CD-images in this formats:
iso, nrg, bin/cue, mds/mdf.
Please help.

---

### Post by nemin on 2005-04-09
[QUOTE=xodeus]Hi I would like to know how to mount CD-images in this formats:
iso, nrg, bin/cue, mds/mdf.
Please help.[/QUOTE]
Maybe this link is usefull?
[http://freshmeat.net/projects/mount-iso-image/](http://freshmeat.net/projects/mount-iso-image/)
You could also google for "mount iso file", "mount nrg file" etc.

---

### Post by Dracontopes on 2005-04-09
```
 mount -o loop myimage.iso /path/directory 
```

? Works for my .img images...

---

### Post by xodeus on 2005-04-09
[QUOTE=nemin]Maybe this link is usefull?
[http://freshmeat.net/projects/mount-iso-image/](http://freshmeat.net/projects/mount-iso-image/)
You could also google for "mount iso file", "mount nrg file" etc.[/QUOTE]

But this is an extension for KDE... :(

---

### Post by xodeus on 2005-04-09
[QUOTE=Dracontopes]```
 mount -o loop myimage.iso /path/directory 
```

? Works for my .img images...[/QUOTE]

Works for nrg too.
Cheers mate.

Now I only need to know how to mount mds/mdf and cue/bin images.

---

### Post by doclivingston on 2005-04-09
ISOs should be able to me mounted as above (with the mount command). I've found the easiest way to mount the others is to convert them to the .iso format and then mount them.

I'm not sure if there are .deb packages for the following, they should be able to convert other formats:

BChunk(bin/cue) - [http://he.fi/bchunk/](http://he.fi/bchunk/)
mdf2iso (mdf): [http://mdf2iso.berlios.de/](http://mdf2iso.berlios.de/)

and from the Nero Linux FAQ, you should be able to convert .ngr files to a .iso with the following command, or see [http://wiki.linuxquestions.org/wiki/Nero_CD_image](http://wiki.linuxquestions.org/wiki/Nero_CD_image)
`dd if=myNeroImage.ngr of=myIsoImage.iso bs=1024 skip=300`

---

### Post by ubuntu_demon on 2005-04-09
[QUOTE=doclivingston]ISOs should be able to me mounted as above (with the mount command). I've found the easiest way to mount the others is to convert them to the .iso format and then mount them.

I'm not sure if there are .deb packages for the following, they should be able to convert other formats:

BChunk(bin/cue) - [http://he.fi/bchunk/](http://he.fi/bchunk/)
mdf2iso (mdf): [http://mdf2iso.berlios.de/](http://mdf2iso.berlios.de/)

and from the Nero Linux FAQ, you should be able to convert .ngr files to a .iso with the following command, or see [http://wiki.linuxquestions.org/wiki/Nero_CD_image](http://wiki.linuxquestions.org/wiki/Nero_CD_image)
`dd if=myNeroImage.ngr of=myIsoImage.iso bs=1024 skip=300`[/QUOTE]
 bchunk is available in universe

---

### Post by yellow beard on 2006-05-06
when i try to use mdf2iso i get a file too large error. apparntly theres a patch out to fix this but i dont know where to get it?

---

### Post by PriceChild on 2006-05-28
I'm having the same problem...
Found this: [http://www.linuxquestions.org/questions/showthread.php?t=377258]("http://www.linuxquestions.org/questions/showthread.php?t=377258")
Which shows the patch at [http://developer.berlios.de/patch/index.php?func=detailpatch&patch_id=665&group_id=2545]("http://developer.berlios.de/patch/index.php?func=detailpatch&patch_id=665&group_id=2545")

However, does this need to be applied to the source code and then built myself?

No chance of using the deb package i've got and patching that?

Please help with this, or a way to mount mdf.

Pricey

EDIT

just tried```
mount -o loop myimage.iso /path/directory
``` and it worked perfectly :)

---

### Post by vistovistor on 2007-11-04
I know its an old post but...
Hello my first post here =) sorta newish to Ubuntu, but&#12288;I have been having similar problems with mounting files, ISO everything is OK but when it comes to mounting mdf/mds files its a problem, theres a program called mdf2iso in the reps that can help out here of course it doesn't help when you have MDF and MDS separately,(eg raw data and a catologue file) at least I don't know the extended function to get it to work. However this is the workaround I have used.

**For this you will need: **
A windows boot OS (not wine or an emulator as they don't support SDTP)
Alcohol 120% (about 10mb)

Install alcohol 120% then mount your mdf\mds file as a Virtual drive by dragging it into the program, then clicking "Mount to volume" then proceed to the left hand side and click -> Image making wizard, target the wizard to your fake mounted virtual drive then rip it as an ISO, burn onto your disk or in my case 4 gig mem stick and put back on Ubuntu then enjoy.
If anyone has thought of a better way please let me go it took me a day to work this out (my windows laptop doesn't have a burner ><)

---

