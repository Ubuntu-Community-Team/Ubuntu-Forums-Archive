---
title: "I knackered my system with fsck"
date: 2007-07-10
forum: General Help
---

### Post by benmarvin on 2007-07-10
Ok, I'm not completely new to Ubuntu or Linux, I've been using it for a few months now. I was trying to figure out how to run fsck on a removable drive and I ended up accidentally running it on my main hard drive, now I get all kinds of errors when I boot up, things are missing and the system keeps trying to perform "maintenance" of some kind, but it can't even find apt-get.  I'm at a loss for the correct way to fix this. All I've seen just say "DONT DO IT!". Well, I knew that, I just didn't want to do it. I can get to the command line and login upon boot up. Any help is appreciated.

---

### Post by atlfalcons866 on 2007-07-10
where the volumes unmounted? you shouldnt run fsck on a mounted volume as it might destroy data

---

### Post by benmarvin on 2007-07-10
> **atlfalcons866 said:**
> where the volumes unmounted? you shouldnt run fsck on a mounted volume as it might destroy data

Yup, it was mounted, and I'm pretty sure data was destroyed, that's exactly the problem. It gave the warning as usual, and me being the idiot, I just immediately hit yes, but then literally 2 seconds later, I realized I screwed up and I killed it. I thought I saved it, but upon the next reboot is when I started getting all these errors.

---

