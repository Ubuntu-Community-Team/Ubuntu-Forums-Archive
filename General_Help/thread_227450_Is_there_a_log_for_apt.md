---
title: "Is there a log for apt?"
date: 2006-08-01
forum: General Help
---

### Post by TeeAhr1 on 2006-08-01
Backstory: I was asked on the [Gimmie]("www.beatniksoftware.com/gimmie/") mailing list what libraries I installed to get Gimmie working (had a lot of trouble with it, someone else had too), and I realized I wasn't sure.  It was several, some I probably didn't need to, over a few days of messing with it.

Which made me realize that I find myself in that position a lot, which made me wonder if there was a log for apt, so I could see what I installed and when.  I looked in /etc/apt and didn't find anything, and a google search likewise yielded no joy.  What say you, friends?

regards-
p.

---

### Post by halfvolle melk on 2006-08-01
There's /var/log/dpkg.log and /var/log/dpkg.log.1 but they don't date back very long. Maybe you can configure dpkg to remember stuff longer. man dpkg has this to say about that
> --log=filename
              Log  status change updates and actions to filename.  This
              can be given multiple times.  Log  messages  are  of  the
              form    &#8216;YYYY-MM-DD   HH:MM:SS   status   <state>   <pkg>
              <installed-version>&#8217; for status change updates; &#8216;YYYY-MM-
              DD  HH:MM:SS  <action>  <pkg> <installed-version> <avail&#8208;
              able-version>&#8217; for  actions  where  <action>  is  one  of
              install, upgrade, remove, purge; and &#8216;YYYY-MM-DD HH:MM:SS
              conffile  <filename>  <decision>&#8217;  for  conffile  changes
              where <decision is either install or keep.

---

