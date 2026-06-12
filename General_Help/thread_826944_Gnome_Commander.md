---
title: "Gnome Commander"
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

### Post by naimkazi on 2008-10-19
1.you need to go to your home folder
2. change directory  to  the hidden file .gnome-commander 
3. In this directory you will find a file called connections
4. edit and remove all the lines for ftp
5. save
6. now you can start gnome-commander

hope this helps

---

### Post by roland.b on 2008-11-24
This can happen if you accidentally add a Public FTP (anonymous user) using the Remote Server (CTRL+F) window with the wrong service type (FTP with login).

You can fix this by checking the file at ~/.gnome-commander/connections. All ftp:// line must have this format: ftp://<user>:<password>@<ipaddress>.

Fix anything that looks like ftp://<ipaddress> and change it to ftp://someuser:somepassword@<ipaddress>

or for example change it to ftp://anonymous:you%40provider@<ipaddress>

---

### Post by roland.b on 2008-11-24
This can happen if you accidentally add a Public FTP (anonymous user) using the Remote Server (CTRL+F) window with the wrong service type (FTP with login).

You can fix this by checking the file at ~/.gnome-commander/connections. All ftp:// line must have this format: ftp://<user>:<password>@<ipaddress>.

Fix anything that looks like ftp://<ipaddress> and change it to ftp://someuser:somepassword@<ipaddress>

or for example change it to ftp://anonymous:you%40provider@<ipaddress>

---

