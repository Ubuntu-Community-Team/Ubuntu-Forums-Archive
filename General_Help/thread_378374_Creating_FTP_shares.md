---
title: "Creating FTP shares"
date: 2007-03-07
forum: General Help
---

### Post by mattmac24 on 2007-03-07
ok this may seem insecure to people, but this is what i need to do.

i have a music server set up with mpd and a web client all working well. i just need a way of uploading and managing the music to my server.

i have installed vsftpd and can log in fine, i see my home directory. but only read access

my question is how do i login and make my home dir "/" with full read write access.

i can login as root by removing root from /etc/ftpusers. but then i just see no files and when i enter "ls" i get nothing.

or if anybody knows how to easily set this up using simba or a similiar service please let me know.

Thanks,

matt:)

---

### Post by etank on 2007-03-07
Look in the /etc/vsftpd.conf file for lines like this
```
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES

```
If they say NO then change them to a yes. The local enable allows the users listed in /etc/passwd to log in and the write_enabled allows write access.

I hope this helps.

---

### Post by mattmac24 on 2007-03-07
thanks, those where set like that by default. but by changing chroot_local_user=YES to chroot_local_user=NO. and then by logging in as root, all works the way i want. just a couple of things have stuffed up permissions, but all else works great.

thanks 4 pointing me in the right direction.

Matt:)

---

