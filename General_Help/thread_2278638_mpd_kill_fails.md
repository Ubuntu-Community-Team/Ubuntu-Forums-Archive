---
title: "mpd: kill fails"
date: 2015-05-18
forum: General Help
---

### Post by MJae on 2015-05-18
I'm not sure I should put this in this board but I'm having a bit of trouble with MPD. When I first set it up, I was able to make it run and make it work together with Ario. After rebooting, though, Ario wouldn't play anything. When I go to the terminal and type mpd I get:
```
Failed to bind to '[::]:6600': Address already in use
```

I read that I'm supposed to use mpd --kill but that only gets me:
```
daemon: no pid_file specified in the config file
```

So, I checked the config file in /etc/mpd.conf and it does have a pid_file line.

I found this bug file in musicpd.org: [http://bugs.musicpd.org/print_bug_page.php?bug_id=3054](http://bugs.musicpd.org/print_bug_page.php?bug_id=3054). It says I should, "Configure with --sysconfdir=/etc if you want MPD to look in /etc by default." But that gets me:
```
** (mpd:20804): CRITICAL **: option parsing failed: Unknown option --sysconfdir=/etc
```

I'm must be doing something wrong.

I don't know where to look next. Please, help. What do I need to do to make mpd run again?

---

