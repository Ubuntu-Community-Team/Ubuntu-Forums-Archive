---
title: "Stop Samba from writing to auth.log"
date: 2020-10-13
forum: General Help
---

### Post by jrmymllr on 2020-10-13
I'm using Samba 4.3.11, and I'd like to make it stop writing these meaningless messages to /var/log/auth.log:

Oct 12 17:43:30 DIS smbd: pam_unix(samba:session): session closed for user nobody
Oct 12 17:43:30 DIS smbd: message repeated 2 times: [ pam_unix(samba:session): session closed for user nobody]
Oct 12 19:23:50 DIS smbd: pam_unix(samba:session): session closed for user <redacted>
Oct 12 20:37:57 DIS smbd: pam_unix(samba:session): session closed for user nobody
Oct 12 21:12:34 DIS smbd: pam_unix(samba:session): session closed for user <redacted>
Oct 12 21:12:35 DIS smbd: pam_unix(samba:session): session opened for user <redacted> by (uid=0)
Oct 12 23:25:52 DIS smbd: pam_unix(samba:session): session closed for user <redacted>
Oct 13 07:02:46 DIS smbd: pam_unix(samba:session): session opened for user <redacted> by (uid=0)
Oct 13 07:20:35 DIS smbd: pam_unix(samba:session): session closed for user nobody

I don't need these as this is being run in a residential environment. Can these be stopped? I've spent some time researching this and there doesn't seem to be a straightforward way to do this. Right now, my smb.conf is not specifying a log level which as I understand, is already at minimum, and affects only /var/log/samba messages.....I think? There must be a way simple way to do this!

---

