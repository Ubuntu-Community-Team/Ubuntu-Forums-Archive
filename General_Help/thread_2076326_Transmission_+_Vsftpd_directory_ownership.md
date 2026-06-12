---
title: "Transmission + Vsftpd directory ownership"
date: 2012-10-25
forum: General Help
---

### Post by LouieK on 2012-10-25
I'm a complete noob to linux but I managed to setup transmission on a headless server with the help of this [tutorial]("http://rickylford.com/ubuntu/installing-transmission-on-ubuntu-server-12-04-lts/") I also have vsftpd setup and I followed [this]("http://www.noob2geek.com/linux/setup-vsftpd-debian-ubuntu/") tutorial. 

When I try to upload using filezilla I get
550 Create directory operation failed & 550 Failed to change directory erros. I believe it's because I never set the chown 
```
sudo chown -R ftpuser /var/www/path/to/your/dir
``` command for the ftpuser to my download directory. If I set the owner to my ftpuser will transmission still be able to download and seed? Or will I need to change it back every time?

I hope I explained it well enough, sorry I'm a complete noob.

---

