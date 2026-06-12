---
title: "DVD/CD don't mount??  No DVD drive support??"
date: 2017-05-08
forum: General Help
---

### Post by hrothgar2 on 2017-05-08
So, I've had basic usability issues with Ubuntu before, but this takes the cake...

Ubuntu 16.04 installed on a Lenovo G505 laptopt and inserting a CD or DVD does absolutely nothing. The thing cant even play a music CD out of the box. This has got to be a joke, right? What kind of OS doesnt have DVD drive support? I'm seriously considering going back to Windows and dealing with the malware etc. At this point it would be easier than spending hours always trying to figure out why the simplest things dont work with Ubuntu -- like viewing a photo album thats on a DVD. Why even release an OS that doesnt have support for a DVD rom? I have to vent because this is simply beyond me.

---

### Post by Perfect Storm on 2017-05-08
Hi,

You properly need to install some packages, open the terminal and type;
```
sudo apt install ubuntu-restricted-addons ubuntu-restricted-extras libdvd-pkg
```

---

### Post by hrothgar2 on 2017-05-08
Those are installed and no change; DVD doesn't mount. But why wouldn't that be installed already anyway? Even windows 95 has support for cdroms.

---

### Post by QIII on 2017-05-08
CD ROMs do, in fact, work.  DRM protected DVDs don't work out of the box because using unlicensed codecs is illegal in some jurisdictions.

---

### Post by Perfect Storm on 2017-05-08
It's licens issue. If they were included we had to pay for ubuntu.

Have you tried with different DVDs? Some DVDs are so protected that they hardly run.

---

### Post by hrothgar2 on 2017-05-08
The dvds aren't protected. They are home burnt copies of family photo albums. 
Even if they were protected, I'd at least expect them to mount, for Ubuntu to show a DVD/cdrom icon with a mounted disc.

---

### Post by hrothgar2 on 2017-05-08
> **Artificial Intelligence said:**
> It's licens issue. If they were included we had to pay for ubuntu.

Have you tried with different DVDs? Some DVDs are so protected that they hardly run.

The Discs I'm trying are not protected.

---

### Post by QIII on 2017-05-08
Then *you* have a problem with *your* system or the format you have used on your media that is not representative of Ubuntu.  If you will amend your attitude, you might get a better response.

---

### Post by hrothgar2 on 2017-05-08
> **QIII said:**
> Then *you* have a problem with *your* system or the format you have used on your media that is not representative of Ubuntu.  If you will amend your attitude, you might get a better response.

The system is fine, everything works in Windows. The format of the disc is not the problem. As I've said, not a single cd or DVD mounts. It's as if Ubuntu thinks that there is no drive installed at all. 
I can't help but be frustrated. This is an Ubuntu problem. Not being able to read discs is ludicrous. This has got to work out of the box.

---

### Post by QIII on 2017-05-08
For the vast majority of us it does work.  This is not a generalized systemic problem with Ubuntu or there would be thread after thread with this complaint.  That said, problems do occur.  But don't project a problem you are encountering on the whole population of machines running Ubuntu.

It certainly is frustrating when things do not work.  But demonstrating a poor attitude is not likely to garner sympathy or draw willing helpers.

There are Windows support forums aplenty.  Windows is not perfect, either.

---

### Post by hrothgar2 on 2017-05-08
Well then, guess you better help someone with better attitude.

---

### Post by ian-weisser on 2017-05-08
How strange. Data CDs and data DVDs work on my system just fine. All my systems. Since the first release of Ubuntu.

There are two, and only two, possibilities.
1) You have (perhaps unintentionally)  changed your system to disable CD/DVD compatibility.
2) Your Lenovo hardware is defective, or Lenovo has installed a component that is incompatible with Linux.

Since we are not psychic, your best path forward is to consult Lenovo support and/or tell us which occurred.

QIII makes a valid point: By the standards of this community, your initial post was rather rude. 
Perhaps that was not intended. We are volunteers. We are nice to people who are nice to us. We ignore people who are not.

---

### Post by lisati on 2017-05-08
It could be anything. For example, have the DVDs been finalised?

---

### Post by Autodave on 2017-05-08
Is this a dual-boot system? If so, does the drive work in Windows?  If not dual-boot, how did you install Ubuntu onto the machine: thumb drive or USB stick?

---

### Post by oldos2er on 2017-05-08
Closed for staff review.

This thread will remain closed. We expect all forum members, both new and old, to abide by the [Code of Conduct]("https://ubuntuforums.org/misc.php?do=showrules") they agreed to when joining the forum, particularly "The purpose of the Ubuntu Forums is to provide support for Ubuntu. We  also want this to be a place where community can develop and we can  enjoy one another's company. To achieve this, we strive to maintain an  atmosphere that can be enjoyed by all and we ask all members of the  community to be respectful at all times. This means please use etiquette  and politeness. Treat people with respect. If you do this, the rest of  the code of conduct won't need more than a cursory mention" and "If the thread turns into an argument, it can be closed to further  comment or removed without notice."

Thanks to everyone who participated in a positive way.

---

