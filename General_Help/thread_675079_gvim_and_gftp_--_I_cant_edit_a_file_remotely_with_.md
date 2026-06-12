---
title: "gvim and gftp -- I cant edit a file remotely with gvim"
date: 2008-01-22
forum: General Help
---

### Post by WinterWeaver on 2008-01-22
I've recently started using gVim and I'm really loving it!! Learning a bit more everyday.

I have one issue tho. I cant seem to edit remote files with gVim. In particular with gFTP.

I connect to the remote FTP and edit the file (I've set the options to use gvim for editing). It opens the file with gVim normally, and I can change everything. But when I save and quit, the file is not updated on the remote server.

If I tell gFTP to use gEdit instead of gVim, then, after I save and close gEdit, it uploads the modified (temp) file to the server to replace the original. Why isn't gVim doing this?

Is there any solution for me to do this?

Thanks,

WW

---

### Post by archuser on 2008-04-03
Not sure if you fixed this yet, but I solved the issue by adding the -f option to gvim in the gFTP config. This enables gvim to run in the foreground, a requirement of gFTP.

---

