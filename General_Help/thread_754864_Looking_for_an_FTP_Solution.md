---
title: "Looking for an FTP Solution"
date: 2008-04-14
forum: General Help
---

### Post by monteros on 2008-04-14
Hey folks, I was hoping someone might have some pointers for a ftp solution for the company I work for.  To many of the people that we are working with outside the company are not savvy enough to follow instructions to use the ftp server I have setup. I was hoping that someone either knows of or has an idea of something I could look into to provide an either web based simple form ftp solution or something similar.

Thanks.

---

### Post by gsmanners on 2008-04-14
Probably the simplest client to use would be filezilla or gftp. For setting up an ftpd on your server, you can set up proftpd. Here's a simple introduction to proftpd:

[https://help.ubuntu.com/community/ProFTPD?action=show](https://help.ubuntu.com/community/ProFTPD?action=show)

---

### Post by chilinski on 2008-04-14
If your clients are only uploading to you, you might want to consider putting in a PHP fileupload script on a web page. Secure it with .htaccess.

---

