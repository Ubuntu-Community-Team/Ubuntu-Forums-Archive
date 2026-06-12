---
title: "Preventing the OS from using concurrent FTP logins?"
date: 2008-01-17
forum: General Help
---

### Post by SupraBlur on 2008-01-17
So here's the deal -- when I do some PHP development from home, it's easy for me to just establish an SSH connection to my work server and work as if it's local.  That works great.

However, when I want to work on one of my personal sites hosted on GoDaddy, I have to use FTP instead of SSH (I only have hosting, no virtual or actual server), which was fine in Windows using either Homesite+, PSPAD, or any other editor with an FTP client built in.  I figured this should be the same as using SSH, so I point the 'Open' dialog in gPHPedit to my FTP site and am able to open the file I want to work on.  The problem is that this connection stays open even after I've opened the file, and when I go to save the file, it tries to open a second connection to the server, which is not allowed by GoDaddy (maximum 1 simultaneous connection per user).

Is there any way I can force Nautilus or whichever program is managing my FTP connection to use a maximum of 1 connection to the server, or to close the connection immediately after file transfer?

It would suck to have to open VirtualBox just to edit files.  Thanks in advance,

-Ray

---

