---
title: "Opening a single terminal emacs instance with download Filezilla files...?"
date: 2021-08-12
forum: General Help
---

### Post by dbee on 2021-08-12
How do i open a single terminal emacs instance with downloaded Filezilla files?

I've followed some online tutorials but haven't been able to do it properly.

I can open a GUI emacs and do a 'M-x server-start' which opens all new downloaded ftp files in a single instance.

But when i try to do this automatically by adding a (server-start) to my 'touch /home/dara/.emacs' newly created file. It doesn't work.

My file extension settings in Filezilla look like this...

```

php /usr/bin/emacsclient %f
css /usr/bin/emacsclient %f
js /usr/bin/emacsclient %f
html /usr/bin/emacsclient %f

```

---

