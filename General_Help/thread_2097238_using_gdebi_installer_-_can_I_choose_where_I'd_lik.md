---
title: "using gdebi installer - can I choose where I'd like to install?"
date: 2012-12-22
forum: General Help
---

### Post by listerdl on 2012-12-22
What I mean is - I am trying to download and install a program called "Dragon Disk" - basically it manages buckets like Amazon S3.

Anyway the download is a .deb file so all good there.

I have gdebi installer which is really simple to use. The only thing is that Id like to choose where Id like to place the install. By default it seems to place the program it /etc/ which is ok but id prefer to place it in /opt/ - 

Should I install using a different method to have more control?

Thanks

---

### Post by mc4man on 2012-12-22
Where files from a .deb package are installed is set in the package itself, not how/what you use to install that package.

If you want different then you need to build the source yourself & adjust the install dir(s) in the configure or whatever

---

