---
title: "Will I be able to transfer my e-mail from Windows Eudora?"
date: 2007-05-03
forum: General Help
---

### Post by swarup on 2007-05-03
I have Windows 98 on my old laptop (celeron 433, RAM 288 mhz) and am thinking to put Ubuntu (or Xubuntu/Gnome) on it. I have an external HD which connects by PCMCIA, on which I will have my old Eudora program with all its e-mails, addresses, etc. Will I be able to pull the data from that hard drive onto the new linux desktop and bring it somehow into the new linux e-mail program. 

One important question here is, will the linux system on my internal HD be able to see the date on my external PCMCIA hard drive i.e. in the Eudora program there?

Thanks,
Swarup

---

### Post by aysiu on 2007-05-04
Based on [this post](http://ubuntuforums.org/showthread.php?p=591450&highlight=eudora#post591450), it would seem that you can import from Eudora on Windows to Thunderbird on Windows.

If that's true, transferring Thunderbird on Windows to Thunderbird on Xubuntu is easy: copy C:\Documents and Settings\swarup\Application Data\Thunderbird to /home/swarup/.mozilla-thunderbird

---

