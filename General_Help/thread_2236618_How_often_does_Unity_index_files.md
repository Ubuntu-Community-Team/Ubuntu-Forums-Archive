---
title: "How often does Unity index files?"
date: 2014-07-27
forum: General Help
---

### Post by Roasted on 2014-07-27
Hello friends. I tried to Google around but I got a bunch of different hits with other things named Unity so the search was a bit of a bust. Just curious, how often does Unity index files? I noticed yesterday that on my relatively new 14.04.1 install that I could not find files via the dash. If I opened the file, closed it, then it suddenly became accessible in the dash, but as I located files I hadn't opened yet that had synchronized from cloud services, those in particular did not show up.

Tonight I ran through that little test again by finding older files I haven't opened but synchronized down from cloud services. I noticed that these files were accessible in the dash, which got me wondering if Unity had done some sort of index of my files. So, anybody have an idea?

(this is all assuming that Unity does indeed index the files on your hard drive... I never received a notification that it was working, such as what OSX does in Spotlight when you try to search for a file there and it says it's currently indexing)

Thanks!

---

### Post by vanadium on 2014-07-28
Unity uses various sources. It uses zeitgeist. This logs your activity. Files you did not yet handle will not show up in zeitgeit. Additionally, Unity uses the results from "locate". This classical utility uses a database to quickly locate files. However, this database is updated daily (I think this is set up with a cron job). You can update the database yourself (as administrator though) with the command "sudo updatedb".

Unity only searches your home directory. I think it does not results for attached drives.

---

### Post by buzzingrobot on 2014-07-28
As I recall, Spotlight indexes the content of files as well as the file name. The 'locate' command in Linux indexes file *names* only.

Indexing file contents is more demanding task than indexing file names and can take noticeable resources when a large filesystem is initially indexed.

---

### Post by Roasted on 2014-07-28
Ah, this all makes sense. I always thought the osx index was really slow but I didn't know it was scanning contents. Likewise that makes sense as to how unity didn't see files one day but saw them the next. 

Appreciate it!

---

### Post by buzzingrobot on 2014-07-28
I believe Spotlight's indexing is adjustable -- like, don't index backup drives or don't automatically start indexing any temporarlly attached and mounted drives -- but I don't recall a GUI being available for that. Once the first index was completed, I never noticed incremetal indexing. 

KDE has had full-content indexing for a long time. It produced a lot of complaining over the years for bugginess and sluggishness.  The indexing engine has been redone and seems to be doing better recently.

There is also the "recoll" tool, which does full-content indexing.  I've used it and like it.

---

