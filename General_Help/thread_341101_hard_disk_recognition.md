---
title: "hard disk recognition"
date: 2007-01-18
forum: General Help
---

### Post by heracles on 2007-01-18
For some reason my current linux system will not see the second drive on my computer. My main drive is Ubuntu linux edgy and is ide the second drive is sata and is also linux edgy but with a version on which will only let me reboot to a text line login I just need to copy the thunderbird files over , But my main system does not see the drive. Its there because the BIOS recognises there are two there.

---

### Post by JamieC on 2007-01-18
Hey there, could you please open a new terminal, run and paste the output of the following command:
```

sudo fdisk -l

```

---

### Post by Jussi Kukkonen on 2007-01-18
> For some reason my current linux system will not see the second drive on my computer.
Details, please. 
* Is the actual drive found? Check with ***sudo fdisk -l***
* If yes, have you tried mounting a partition on it? If you need help with that, just ask...

---

### Post by kidders on 2007-01-18
Hi there,

What do you mean when you say it doesn't "see" it? Does it not appear when you do something like **ls /dev/sd*** ?

---

### Post by heracles on 2007-01-18
Thanks for the replies I solved it by downloading the programme Storage Device manager through Synaptic. Elsewhere on the forum it said that this utility was downloaded with previous ubuntu versions but not in edgy. Once downloaded it recognised the Serial SDA 1 partition. It was then just a matter of transferring the files from my old system . NOTE I must remember to back up to a removable usb device such files. One day I hope to be able to assist somebody else on the forum with a problem

---

### Post by kidders on 2007-01-18
> **heracles said:**
> One day I hope to be able to assist somebody else on the forum with a problem:-) Keep an eye out for problems you recognise!

Glad you solved your problem.

---

