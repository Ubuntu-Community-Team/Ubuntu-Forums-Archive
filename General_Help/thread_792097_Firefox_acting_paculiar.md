---
title: "Firefox acting paculiar"
date: 2008-05-12
forum: General Help
---

### Post by jeff.sadowski on 2008-05-12
So during my troubleshooting of my apache install I discovered most of my problem was in firefox. when I point firefox at [http://127.0.0.1](http://127.0.0.1)
or any directory there in it prompts me to download a phtml file
looking at the file afterwards it is what was suppose to show on the page.
konqueror displays it correctly. Does anyone know why firefox would act like this?
I am using ubuntu 8.04 I downgraded firefox 3b5 to 2.0.0.14 because firefox 3b5 was driving me batty with its dowload issues (plugins that request downloads often crash 3b5) and its mess ups with check boxes.

If I point firefox at [http://127.0.0.1/index.html](http://127.0.0.1/index.html) it works correctly

---

### Post by GurneyHalleck on 2008-06-01
I'm glad I found this post, because I'm seeing very similar behaviour from Firefox 3, and it's got me flummoxed. (Though I'm on the edge of becoming frustrated and then annoyed.)

I've finally got Apache 2.0 and PHP 5 compiled, built, installed, and working, and now my local files are being served correctly.

Except in Firefox 3, which keeps asking for the /index.html file to be downloaded, just as you describe. The only difference is that it asks for a download even if I type [http://127.0.0.1/index.html](http://127.0.0.1/index.html), and that it offers a download of an HTML file, not a PHTML file.

What's really bizarre is that, if I copy index.html and call it testing-apache2.html, that file displays perfectly, PHP and all. But as index.html, Firefox 3 just doesn't seem to know what to do with it.

I've tested in Lynx and Opera, and using lwp-request, and all correctly receive and render /index.html without any mention of a download.

I've modified the root .htaccess file, commented everything out, renamed it, nothing works to appease Firefox.

Did you ever find out what was causing this problem?

---

### Post by GurneyHalleck on 2008-06-02
Found a solution after some amount of web searching.

Clear your cache in Firefox, and suddenly everything seems to work fine.

---

