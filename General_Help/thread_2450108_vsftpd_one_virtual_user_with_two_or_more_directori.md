---
title: "vsftpd one virtual user with two or more directories"
date: 2020-09-07
forum: General Help
---

### Post by lafayettes on 2020-09-07
Hello,

I have configured a vsftpd service for 2 virtual users: admin user and standard user. The admin user has access to all folders.  The folder structure is:

```
/shared
        |-> /in
        |      |- /Folder_A
        |      |- /Folder_B
        |      |- /Folder_C       
        |
        |->/out
                |- /Folder_A
                |- /Folder_B
                |- /Folder_C


```

The standard user has been configured in /etc/vsftpd.conf:

```
user_config_dir=/etc/vsftpd/vsftpd_user_conf

```
I have created a file /etc/vsftpd/vsftpd_user_conf/standar_user

and inside the file:
```
local_root=/shared/in/Folder_A

```
How can I assign the standard_user virtual user to both directories at the same time
```

/shared/in/Folder_A
/shared/out/Folder_A

```
without having access to the rest of the folders?

Thanks!

---

