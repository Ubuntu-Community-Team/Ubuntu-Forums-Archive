---
title: "Open office word processor disappeared...Help!"
date: 2007-09-11
forum: General Help
---

### Post by Don_S on 2007-09-11
I installed Ubuntu 7.04 a couple of days ago and all the updates too. Everything seems to be running fine except for one problem...I can't find Open Office word processor! It is not in the "applications" drop-down menu under "office" and when I try to open a document file, I get the "searching for application to use" message (or something similar) and it tells me that I need to install Open Office Writer. I click on OK and it seems to go through the installation successfully, but still no Open Office Word processor :confused: 
Here's what I've tried to fix the problem: (in addition to the above)
1. Tried to uninstall the Open Office suite (so I could try to re-install it), but it wouldn't let me.
2. I marked Open Office Writer for re-installation in Synaptic Manager. Again it goes through the re-install successfully but still no Office Word Processor.

Any suggestions? (other than "re-install Ubuntu")

---

### Post by eggdeng on 2007-09-11
Try ```
sudo updatedb
``` followed by ```
locate oowriter
``` You should get /usr/bin/oowriter. If you get anything else, it is not installed to the default location.

---

### Post by Don_S on 2007-09-11
Thanks for the suggestion.. will try it when I get home from work.

---

### Post by Don_S on 2007-09-11
Well I tried the above suggestion... when I type in "locate oowriter" nothing shows up...I'm returned to the command prompt:confused: Now what?

---

### Post by Sef on 2007-09-25
> I installed Ubuntu 7.04 a couple of days ago and all the updates too.

1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

3) Did you check the cd for defects?

Any one of those things could cause a bad install.

---

