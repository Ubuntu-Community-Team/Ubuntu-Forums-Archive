---
title: "Cannot access all IDE drives?"
date: 2005-05-08
forum: General Help
---

### Post by adkmom on 2005-05-08
Hi all-

New to Ubuntu.  The CD loads & all seems well except- I cannot access my hard drives.  They show in device manager but not anywhere else?

I have a Soyo board which has the ability to do RAID (4 IDE ports)- however, I am not set up for RAID- but have enabled all 4 ports for my 2 HD's & 2- optical drives.  Each is set as master for each line.

I think the trouble is that my BIOS sees IDE 3 & 4 as "scsi"- even though they are IDE drives attached.

Is there a command or way to get access to these drives?

Remember- n00b here- lol,

Tracy

---

### Post by clb137 on 2005-05-08
hi,

Are your other drives windows? Need to know the operating system.

Also for your info please have a look at the following link,  

[http://www.frankandjacq.com/ubuntuguide/5.04/index.html](http://www.frankandjacq.com/ubuntuguide/5.04/index.html)

I have used it loads of times, if you have any more problems or need help I will try to assist you, 

good luck

clinton

---

### Post by adkmom on 2005-05-08
Hi-

Yes, I went through the guide/forums a bit before but didn't see this same sort of scenario anywhere (as it seems in any issue I have-  :^P   
Most scsi posts have to do with either a true scsi drive or a scsi CD-ROM.

The drives are Windows- yes.  IDE 4 is the boot drive for XP, & it is partitioned into 2 parts.  IDE 3 is a data drive & is partitioned into 3 parts.

I have them set as NTFS- perhaps that's also an issue?  Though I've not had other live CD's choke on this configuration?  I've always had at least read access?

Tracy

---

### Post by clb137 on 2005-05-08
[QUOTE=adkmom]Hi-

Yes, I went through the guide/forums a bit before but didn't see this same sort of scenario anywhere (as it seems in any issue I have-  :^P   
Most scsi posts have to do with either a true scsi drive or a scsi CD-ROM.

The drives are Windows- yes.  IDE 4 is the boot drive for XP, & it is partitioned into 2 parts.  IDE 3 is a data drive & is partitioned into 3 parts.

I have them set as NTFS- perhaps that's also an issue?  Though I've not had other live CD's choke on this configuration?  I've always had at least read access?

Tracy[/QUOTE]

hi Tracy,

have you tried the following? 

[http://www.frankandjacq.com/ubuntuguide/5.04/index.html#automountntfs](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#automountntfs)

in the guide you may have to change the 'hda'   for your info hd is the harddrive and 'a' is the 1st one.

can you also post the results of this command 'sudo fdisk -l' you need to run it in a terminal window, any probs send me an email or reply in here

thanks

clinton

---

### Post by adkmom on 2005-05-08
Thanks for that- I'm apparently blind (or too distracted to read properly- ;^)
-can I blame my kids?-

I'm sharing my PC today so will try these commands asap- & will post back to let you/everyone know the outcome.

Tracy

---

### Post by migo on 2005-05-09
I'm having the same problem, my internal IDE drive (FAT32, 1 partition) won't show. I followed the instructions listed on the site you linked and nothing seems to have changed.

---

### Post by clb137 on 2005-05-09
[QUOTE=migo]I'm having the same problem, my internal IDE drive (FAT32, 1 partition) won't show. I followed the instructions listed on the site you linked and nothing seems to have changed.[/QUOTE]


have you followed this?

[http://www.frankandjacq.com/ubuntuguide/5.04/index.html#automountfat](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#automountfat)

no real reason why it should not work any problems please come back

good luck

clinton

---

### Post by migo on 2005-05-09
Yep, those were the aforementioned instructions I followed.

---

### Post by clb137 on 2005-05-10
[QUOTE=migo]Yep, those were the aforementioned instructions I followed.[/QUOTE]


Can you post me any error messages and an more info,

thanks

clinton

---

### Post by migo on 2005-05-10
No error messages, hda1 just never shows up.

---

### Post by geovino on 2005-05-12
Why is it so hard to show the hda icon on the desktop? 
this is the reason I dumped ubuntu two months ago and went to Mepis3.3. 
why is this distro so popular? I'm open to trying it but so far it's not as smooth as mepis. Please explain! Thanks.

---

