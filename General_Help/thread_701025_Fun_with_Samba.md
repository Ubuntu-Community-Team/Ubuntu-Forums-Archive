---
title: "Fun with Samba"
date: 2008-02-18
forum: General Help
---

### Post by Tyke91 on 2008-02-18
My goal is to use samba to create a shared file in my home folder. This folder would then be shared with all of my friends (or at least the friends who have the ability to run samba). It will need to work in windows and ubuntu (my friends are split half and half) and it needs to work even if my own computer is turned off.

My 4 questions:

1.is this possible?

2. there is no question 2.

3.how hard would this be to set up?

4.would my friends need to have alot of tech know-how to do this?

---

### Post by Sokertes on 2008-02-18
> **Tyke91 said:**
> My goal is to use samba to create a shared file in my home folder. This folder would then be shared with all of my friends (or at least the friends who have the ability to run samba). It will need to work in windows and ubuntu (my friends are split half and half) and it needs to work even if my own computer is turned off.

My 4 questions:

1.is this possible?

2. there is no question 2.

3.how hard would this be to set up?

4.would my friends need to have alot of tech know-how to do this?

Yes and NO

Yes to this can be done with Samba but the shared folder has to be on a computer that is on and running to access the shared folder.

No to it is not hard to set up. Your friends that are running linux can use Linneighborhood to access the shared folder(s) and your MS friends can use Network Nieghborhood to access the shared folder(s).

All in all it is not all that hard to do. After all you are running linux so you already have the battle beat.

---

### Post by Tyke91 on 2008-02-19
very cool ^^ thanks

have you come across any good how-tos?  The ones that I've found with google are quite complex, and I'd rather just sit down and do it. (If I need to pour over a manual for hours I will, but I don't have the time to at the moment). Also, I've set aside a computer that I can use to host this, it can remain on for quite some time (last time I had it just running ubuntu as a desktop i think i turned it off maybe once or twice a month)

also, will I be able to lock this with a password?

---

### Post by Iowan on 2008-02-19
Just my opinion, but I'd build a separate folder to share.  You can password protect stuff, but it will still be visible in the folder.  Yes, it's gonna take some work to set up a file server.  There are several good how-to's on [howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu") Check some of **dmizer**'s posts to find some sample smb.conf files.

---

### Post by Tyke91 on 2008-02-19
again, thanks :guitar:

---

### Post by Iowan on 2008-02-19
Maybe you've already seen it, but [this]("http://ubuntuforums.org/showthread.php?t=202605") is another good one.

---

### Post by Sokertes on 2008-02-19
I used this HOWTO years ago and it got me up and going.
l[http://justlinux.com/nhf/Networks/Samba.html]("http://justlinux.com/nhf/Networks/Samba.html")

I still go back from time to time at justlinux.com for the HOWTO's

---

