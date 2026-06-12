---
title: "Unable to migrate the site"
date: 2015-12-10
forum: General Help
---

### Post by rkrp on 2015-12-10
My site <snip> and <snip> are with Digital Ocean and using Ubuntu 14.04 - 64 bit but when I now try to migrate to my other new host it i'm unable to find the correct ssh command. I have to use ssh only as digital ocean does not provide me any control panel. please help.

---

### Post by SeijiSensei on 2015-12-10
Can you log into the site with SSH and get a command prompt?  If so, I'd use tar to archive the site, and scp to copy it to the new location.  Something like:
```

$ cd /path/to/your/site
$ tar cvzpf mysite.tgz .
$ scp mysite.tgz user@newsite:/path/to/new/site

```
You'll need a valid login on both servers of course.

Another option, if the site has only HTML/CSS and graphics, is to suck the entire site over with wget from the new server:
```

$ cd /path/to/your/new/site
$ wget -r http://sitename/

```

---

