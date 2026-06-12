---
title: "CD/DVD Writer not available to select when attempting to burn discs"
date: 2007-04-03
forum: General Help
---

### Post by KrisWillis on 2007-04-03
Since upgrading to 7.04 I appear to have lost the use of my CD/DVD writer.

Originaly I lost all functionality from the point at which the Ubuntu loading splash screen appeared, and when I mean all functionality, I mean **all** functionality! It was like the drive lost power - I couldn't eject or anything using the button on the front!

I've got to the stage where I can operate my drive using its button, and when inserting blank media, I get an icon on the desktop indicating the media type and confirming that it is infact blank. Although, when I insert either a previously burnt disc, or factory stamped disc I get the CD or DVD Disc icon and double clicking that gives me an empty window where I can drag files and burn a disc. It doesn't however display the discs content.

(To get this far I made a slight ammendment to my fstab file, changing a "noauto" to an "auto")

When trying to write to a CD or DVD in either CD/DVD Creator, GnomeBaker or anything similar, getting to the stage where I click to burn the files it asks me to select a drive to use, where the only option is to create an image file.

I'm fairly new to desktop Linux, and have enjoyed the last couple of weeks installing, upgrading and fixing problems, but this is one I am having troubles solving! Any help or pointing in the right direction would be much appreciated.

Many thanks :)

---

### Post by KrisWillis on 2007-04-04
Since rebooting, I have noticed that when it was mounting my drives it mentioned that hdc, which I believe is my DVD/CD Writer, was set to read only because it is write-protected - Could this by the source of my troubles?

---

### Post by KrisWillis on 2007-04-06
Todays 7.04 updates appear to have fixed my problem :)

---

