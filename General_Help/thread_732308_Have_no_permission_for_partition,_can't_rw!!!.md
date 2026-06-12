---
title: "Have no permission for partition, can't r/w!!!"
date: 2008-03-22
forum: General Help
---

### Post by JuricaG on 2008-03-22
I'm using Gutsy Gibbon 7.10, and I've formated an empty partition to ext3 so I can use it as a home directory. After formating with GParted, there's nothing on it but lost+found folder and I can't do anything, not even write on it becase I don't have permission.

I've tried some of the solutions found on this forum but now I can't even mount the partition, the message says " Cannot mount volume" - special device dev/hda3 does not exist.

How is this possible? How can I solve this problem???

HELP!!!!

---

### Post by logos34 on 2008-03-22
it's **[COLOR="Red"]/[/COLOR]**dev/hda3

read this guide:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by JuricaG on 2008-03-24
Thank you very much, that solved my problem!

---

