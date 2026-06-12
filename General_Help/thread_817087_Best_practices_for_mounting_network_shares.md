---
title: "Best practices for mounting network shares"
date: 2008-06-03
forum: General Help
---

### Post by StooJ on 2008-06-03
This isn't a problem, it's more a question on best practices when using Linux.

I have a fileserver that provides two samba shared folders to all my machines: Music & Files

I used to mount them as /Music & /Files, but when I was using Hardy beta I decided it would be better to mount them in my home directory, as this seems a little more logical to me and in line with linux filesystem philosophy: /home/user/Music & /home/user/Files.

I'm really just wondering where they should be - the best practices for mounting external folders. Should they be mounted in the home folder for each user, or in the root?

---

### Post by bingoUV on 2008-06-03
Best practices depend upon your needs. But the most common practice is to mount such folders under /media (in somewhat older systems, it will be /mnt).

Reasons : 

1. You might want to backup /home or /home/<username> periodically. This backup script will try to backup your mounted directory which you may not want. If you know remotely mounted stuff is in /media, it is easier to exclude it from backup script.

2. You might have a desktop search engine like google desktop linux, beagle, tracker etc. They will always try indexing your home directory. Though you can configure them to exclude some particular directories from /home, and include some directories not in /home.

3. / feels more manageable if not cluttered. Just my personal feeling. Since you may mount a number of devices, / will get cluttered with these things. Things like NFS/samba mounts, your mobile phone, few pen drives, few external drives etc.

---

