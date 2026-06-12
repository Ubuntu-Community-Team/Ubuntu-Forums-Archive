---
title: "unable to sudo, not a member of admin group"
date: 2007-07-28
forum: General Help
---

### Post by YaronSh on 2007-07-28
Hmmm well after a lot of searching Ive decided to join the forum and ask the question myself...
I don't know what I was thinking but im in a major problem...

Well... I was searching through the forums to find a solution to add my user to a group
The answer I found was usermod -G username group, which is not the ideal solution apparently

I usermoded my own user (the only user except for root) this way, now Im not part of any group besides the vboxuser group (thats the reason I got into this mess in the first place)

you probably already noticed the awkward mistake I did...
The thing is not only im not a member of the admin group im also not able to login as root with the su command because I havent changed my root password and now I can't passwd my root account because I can't sudo!!!

I would consider that as an easy problem relatively because im still logged into my account (I don't know how to call it exactly but I can still see the GNOME interface)
I guess that if i'll log out I won't be able to login again since my account is not registered in any group..

Some important info about other general problems with this computer that prevent me from getting closer to solving the case:
(This is a Dell Inspiron 8100 laptop)
The slim DVD drive does not work correctly (sometimes it works and sometimes not)
So I can't boot from it...

The floppy drive is fine but I cannot find a floppy image that will help me to restore my password or change the /etc/sudoers or any other administrative file that will help me add myself back into the admin group

Network boot is not an option, I tried and its very difficult doing it using a Windows XP machine (which is my main computer)

I saw a solution suggesting to gpasswd my user in order to restore the privileges, not working, needs sudo access as well...


Well this is a very complicated situation as you can probably see...
Im out of ideas
PLEASE HELP!!!

---

### Post by benson444 on 2007-07-28
Hi,

I had exactly the same problem a month or so back. Did you run a command from Linux Format magazine, which removed you from all groups but vboxuser?

You need to boot into recovery mode or use a LiveCD, giving you root access, and edit the file /etc/group. There will be a line that says something like "admin:x:116:username". Your username will be missing, so just add it after the colon. You will also need to add yourself to other groups like audio, mail, cdrom and so on.

---

### Post by YaronSh on 2007-07-28
thanks a lot for the quick answer
just one more thing...
how do I log into the recovery console?

---

### Post by benson444 on 2007-07-28
You need to reboot and choose recovery mode from the GRUB boot menu.

---

### Post by YaronSh on 2007-07-28
Thank you very much
I'll do my best to prevent such idiotic mistakes in the future!

---

### Post by benson444 on 2007-07-28
No problem mate. Glad it worked out ok. Making mistakes is a great way of learning. Well, that's what I tell myself anyway...

---

