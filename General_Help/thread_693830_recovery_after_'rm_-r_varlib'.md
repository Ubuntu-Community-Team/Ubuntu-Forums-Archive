---
title: "recovery after 'rm -r /var/lib/*'"
date: 2008-02-11
forum: General Help
---

### Post by arthurzhang on 2008-02-11
Hi All,

Just accidently 'rm -r /var/lib/*', now my Ubuntu 6.06 can't display any chars. I guess I lost the font setting or fontset.

I can login and Gnome started. But all chars are blank.

Besides suggestion like this thread, any other idea?

[http://ubuntuforums.org/showthread.php?t=342993](http://ubuntuforums.org/showthread.php?t=342993)

Thanks.

---

### Post by y-lee on 2008-02-11
I hate to break it to you but i think you made a bad mistake. If you have no backups I would think you are going to have to reinstall. I'm running dapper and I have 52 folders in that directory, 9748 items at 152,8 MB. That is alot of stuff to lose and I see alot of stuff in there that looks important. I doubt your system will work right without it. reinstall would be the simplest way to fix it :(

maybe the stuff is in your trash can, I don't know. You can try to look maybe using a livecd. But honestly I would reinstall myself and take it as a lesson on how dangerous rm -r is or on the necessity of backups if you have none (and i don't myself but i know i **should**. lol)

---

### Post by chrisccoulson on 2008-02-11
For one thing, you've lost your /var/lib/dpkg directory, which contains the list of all the packages installed on your system. Without this, apt and dpkg won't work.

I'd be tempted to do a reinstall tbh

---

### Post by TheBoat on 2008-02-11
+1 for a reinstall of the box

---

### Post by johnnyb1726 on 2008-02-11
> **chrisccoulson said:**
> For one thing, you've lost your /var/lib/dpkg directory, which contains the list of all the packages installed on your system. Without this, apt and dpkg won't work.

I'd be tempted to do a reinstall tbh

+1

---

### Post by fmartinez on 2008-02-11
i'm gonna 3rd the reinstall.... you may as well have run $rm -rf /*    remove everyting starting from the root directory DOWN....

---

### Post by arthurzhang on 2008-02-11
Got it, so I will go to recovery console and copy my stuff out and install Eubuntu 7.10. This mistake gave me 1) a lessen, 2) a forums account, 3) a chance to upgrade to 7.10 for a lazy guy ;-)

Thanks everyone. BTW, (I know this is another dumb q) where is the 'thanks' button/link to give thanks to you guys.

---

### Post by arthurzhang on 2008-02-11
Pls ignore the 2nd q. I found the 'thanks', it is a icon, not link or button!!

---

### Post by danwood76 on 2008-02-11
to the left of the quote button!
hehe :P

---

