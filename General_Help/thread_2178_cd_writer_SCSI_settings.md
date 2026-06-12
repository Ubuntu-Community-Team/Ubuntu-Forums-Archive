---
title: "cd writer SCSI settings"
date: 2004-10-26
forum: General Help
---

### Post by arrowhead on 2004-10-26
Hi, I am trying to set up some way to write audio cds and found gcombust in the repositories. I would like to try this because I've used k3b and cdroast before and would like to try something new :smile: .
The problem I am having is with the SCSI settings in the preferences, well I think that's what it is (newbi alert  8-[ ), when I click on the "check SCSI settings" button I get an error message "cdrecord failed to recongnise the selected drive (wrong SCSI settings or no permission to to device)!"
If anyone can help me set this up I would be greatful.

David

---

### Post by ulrich on 2004-10-26
hi,
first of all is your cd-writer scsi or not?
scsi-emulation is no more needed in the new kernels and if you have an ide-writer, forget about that scsi-thing. 
check your /etc/fstab file which should give you the info which dev is your burner.
then in k3b enter the appropriate device.
like '/dev/hdc' ... 

hth, i hadnt the time and need of using k3b since i switched to ubuntu.
but that was what i did in gentooo using k3b.

---

### Post by arrowhead on 2004-10-26
Thanks for the help ulrich.
My drive is ide and I have got it working with k3b as you suggested. I will try again with  gcombust when I've a little more spare time ;-).

David

---

