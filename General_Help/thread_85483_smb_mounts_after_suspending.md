---
title: "smb mounts after suspending"
date: 2005-11-02
forum: General Help
---

### Post by finster on 2005-11-02
Hi all,

I have recently installed breezy on my laptop (Dell Inspiron 6000). Nearly everything is working perfectly (centrino wireless, CPU scaling, touchpad, bluetooth, media buttons, suspend to RAM, screen resolution etc.).

However - I am having a small problem. I have my files on a smb server, so have added 3 lines to my /etc/fstab to mount directories on my server onto mount points in /media. Everything works great until I suspend my laptop and then resume. At this point, my network mounts stop working. Things just pause, and then I get an error in /var/log/messages saying "smb_add_request: request timed out".

If I "umount" them one by one, and then do a "mount -a", I can see them again from within a terminal.

However, from within Nautilus I still can't see them - I get the message "Nautilus cannot display /media/dirname - please select another viewer and try again".

I have searched for similar problems, and can only find one - [http://www.ubuntuforums.org/showthread.php?t=38374]("http://www.ubuntuforums.org/showthread.php?t=38374") (from Hoary), but unfortunately there is no solution.

Does anybody have any ideas why I should lose my smb mounts after a suspend/resume, and why nautilus can't see them even after I remount them?

Thanks in advance.

---

### Post by ideasman42 on 2007-10-07
I had this exact same problem in ubuntu gutsy - just to let people know its still there :/

---

### Post by jokester01au on 2007-12-03
Yes, I have this problem in gutsy too. Very frustrating.

---

