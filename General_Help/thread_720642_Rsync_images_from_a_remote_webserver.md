---
title: "Rsync images from a remote webserver"
date: 2008-03-10
forum: General Help
---

### Post by engberg on 2008-03-10
Hello

I need to know how to make rsync work with a standard free webhotel..

I know that I could use:
rsync -avz --delete [email]user@www.engberg.it[/email]:/srv/www/htdocs /Slide

- to initiate rsync on my local machine, and sync with a useraccount on a webserver, but could it be done without having to set up a new user-account?

Like perhaps...:
rsync -avz --delete [http://www.engberg.it/slideshow/images/](http://www.engberg.it/slideshow/images/) /Slide

---

