---
title: "[SOLVED] CIFS VFS: server not responding"
date: 2008-03-26
forum: General Help
---

### Post by MountainX on 2008-03-26
I'm seeing these message when I shut down or reboot Hardy beta

CIFS VFS: server not responding
CIFS VFS: no response for cmd 50 mid xxx 
where xxx is some digit such as (584) the last time

There are also other errors, but I haven't found the shutdown messages log file yet so I can't say exactly what they are

---

### Post by MountainX on 2008-03-26
I submitted a bug report here:
[https://bugs.launchpad.net/ubuntu/+bug/207517](https://bugs.launchpad.net/ubuntu/+bug/207517)

I'd be interested if anyone can confirm this. Thanks.

---

### Post by rabid9797 on 2008-03-26
1) read the sticky before posting. the general help forum is not yet for hardy.

2) i have the same problem, but with gutsy.

---

### Post by MountainX on 2008-03-26
> **rabid9797 said:**
> 
2) i have the same problem, but with gutsy.

Maybe we can help each other find a solution. When I had Gutsy on this computer, I didn't have the same problem. I didn't use an encrypted file system with Gutsy. 

When I installed Hardy today, I did a clean install and I encrypted /, /home and swap, but not /boot. I used LVM.

I may either reinstall Gutsy tomorrow or I may install Hardy without encryption.

P.S. Since this isn't an issue that is limited to Hardy, I think it is OK to continue this discussion here (if I understand the sticky correctly).

---

### Post by MountainX on 2008-03-27
I found some relevant links. I'm going to test this tomorrow:

[http://ubuntuforums.org/showthread.php?t=171958&highlight=cifs](http://ubuntuforums.org/showthread.php?t=171958&highlight=cifs)
[http://ubuntuforums.org/showthread.php?t=293513](http://ubuntuforums.org/showthread.php?t=293513)

---

### Post by MountainX on 2008-03-27
Following the advice at the following link to rename files appears to have fixed the issues I was seeing when rebooting:

[http://ubuntuforums.org/showpost.php?p=4150826&postcount=49](http://ubuntuforums.org/showpost.php?p=4150826&postcount=49)

I haven't tested it a lot yet because rebooting takes a while and I have other things I need to do. But I do believe it is solved -- and if it isn't I'll report back.

---

