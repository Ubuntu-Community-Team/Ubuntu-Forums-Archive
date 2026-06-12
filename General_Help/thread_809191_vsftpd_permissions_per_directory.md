---
title: "vsftpd permissions per directory"
date: 2008-05-27
forum: General Help
---

### Post by michal_seidl on 2008-05-27
Is it possible to set up vsftpd in that way that one user is able to write files but not delete files to one directory and to other dir can do both?

As I went through vsftpd.conf manual i found there setting *write_enable=YES/NO* which does not make differenc between write and delete ftp command and more there is no way to set it for specific directory.

I have idea to do that with *_umask* or *file_open_mode* but again how to apply these setting just to specific directory.

Any help? Thanks Michal

---

### Post by Grognot on 2008-05-27
You can setup vsftpd to use virtual users which does exactly this.

The rather crude but actually very good docs on how to do this can be found here:

[Setting up virtual users](ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.6/EXAMPLE/VIRTUAL_USERS/README)

[Configuring permissions](ftp://vsftpd.beasts.org/users/cevans/untar/vsftpd-2.0.6/EXAMPLE/VIRTUAL_USERS_2/README)

---

### Post by michal_seidl on 2008-05-28
I have already looked into this documentation, but as I understand it, it is about per-user configuration not about user/per-directory. If I am wrong, pleace send more specific info.

Thanks Michal

---

### Post by michal_seidl on 2008-05-28
I have spend some time on it, and I am nearly sure there is now standard way how to do that. Let me know if I am wrong.

Michal

---

### Post by Monicker on 2008-05-28
> **michal_seidl said:**
> I have spend some time on it, and I am nearly sure there is now standard way how to do that. Let me know if I am wrong.

Michal

Remember, there are also group permissions what you can work with.

---

