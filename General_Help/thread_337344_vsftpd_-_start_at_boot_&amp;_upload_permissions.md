---
title: "vsftpd - start at boot &amp; upload permissions"
date: 2007-01-12
forum: General Help
---

### Post by dwightwatson on 2007-01-12
I have just installed vsftpd and set it up and there are two things I haven't been able to work out how to do.

Firstly, whenever a file is uploaded it has the permissions 0600 so it cannot be read from outside. I added the line "file_open_mode=0777" to the vsftpd configuration but this didn't do anything. Any ideas?

Secondly, how can I make it so that vsftpd will automatically run at boot?

Thanks](*,)

---

