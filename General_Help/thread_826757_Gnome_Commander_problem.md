---
title: "Gnome Commander problem"
date: 2008-06-12
forum: General Help
---

### Post by cessite on 2008-06-12
I love Gnome Commander but it has stopped working for me.

I was FTP-ing some files and then disconnected. When I tried to connect again it seemed to have lost all the FTP profiles I had saved. I thought I would restart Gnome Commander and maybe it would reload its settings. When I tried to restart it wouldn't launch. So then I tried from the command line and got this error:

** (gnome-commander:8486): CRITICAL **: void gnome_cmd_con_ftp_set_host_name(GnomeCmdConFtp*, const gchar*): assertion `host_name != NULL' failed

** (gnome-commander:8486): CRITICAL **: void gnome_cmd_con_ftp_set_user_name(GnomeCmdConFtp*, const gchar*): assertion `user_name != NULL' failed
Segmentation fault

I tried uninstalling and reinstalling but it comes up with the same error. I can't seem to find any settings or configuration file for Gnome Commander where I can manually edit settings.

Can anyone help?

---

