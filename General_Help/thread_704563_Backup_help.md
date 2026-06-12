---
title: "Backup help"
date: 2008-02-22
forum: General Help
---

### Post by UK-Wobbie on 2008-02-22
I have made a backup of my Ubuntu computer system with Remastersys,
The ISO image size of the system is 9.8 GB, I can not burn the ISO to a CD or a DVD as CD is 700 MB and a DVD is 4.7GB.

So i have put the ISO on to a server, But i need a tool what will yet me install the ISO from the server from a live CD?

Do any one know of a tool what will yet you install ISO's from Servers? 
Thanks :)

---

### Post by kwilliam on 2008-02-22
Lol, sounds like that might not have been the best backup plan. ;-)

What you're looking for is a network install.  I've never done it but plenty of others have.  See if [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot) will get you started.

---

### Post by wjston on 2008-02-24
> **UK-Wobbie said:**
> I have made a backup of my Ubuntu computer system with Remastersys,
The ISO image size of the system is 9.8 GB, I can not burn the ISO to a CD or a DVD as CD is 700 MB and a DVD is 4.7GB.

So i have put the ISO on to a server, But i need a tool what will yet me install the ISO from the server from a live CD?

Do any one know of a tool what will yet you install ISO's from Servers? 
Thanks :)

Did you include a lot of audio/video files in your backup? If so try backing those up to your server first, and then I would delete them from your existing system (including trash can) prior to making the new image. Once the new image is created, burn that to DVD (provided it is 4.7GB or less), test it to make sure it works and then restore the audio/video files to your system. If you ever have to restore your system, you will only need to transfer the files from your server once you have your system up and running again.

---

