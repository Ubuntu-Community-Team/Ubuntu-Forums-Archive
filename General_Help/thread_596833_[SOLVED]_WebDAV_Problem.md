---
title: "[SOLVED] WebDAV Problem"
date: 2007-10-30
forum: General Help
---

### Post by nowhere@cox.net on 2007-10-30
Hi all!

I'm trying to set up a good work flow for developing. I have a server set up and have WebDAV running. I can use the Connect to server menu option to connect to my folder just fine. I can drop my php files there and when I shell in and more them they are all fine.

However, when I dbl click em in the file browser or I set up a project pointing to the WebDAV folder and open the files, it looks like the web server is parsing them and the files have when opened in the text editor or bluefish just have the html with errors just like I would see in firefox.

What is wrong? Why can I post the files to the remote server but when trying to read them it allows them to be parsed?

Thanks a ton!

---

### Post by nowhere@cox.net on 2007-10-30
Well I just figured out why it's parsing. I needed

 ForceType text/plain

in the Directory directive. Problem now is that the web page is served that way too when browsing with Firefox. I guess I can create a sym link to the folder the web page is in and create a new directive for it for WebDAV. Is there a better way to do it?

Thanks!

---

### Post by solar george on 2007-11-13
Try adding,

```
 <FilesMatch \.php$>
    ForceType text/plain
</FilesMatch>
```

to a separate virtual host e.g. dav.myserver.org and you should be able to edit the files with nautilus/gnome and view the pages with firefox.

---

### Post by nowhere@cox.net on 2007-12-19
Thanks for the help all but I quit using WebDAV and just mount using ssh. Turns out WebDAV is blocked by work's proxy as well so there is no point for me to use it.

My only other option is to use corkscrew to bypass which I won't do since it is most likely against policy ;)

Thanks!

---

