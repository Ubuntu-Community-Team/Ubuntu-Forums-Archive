---
title: "clementine not working"
date: 2012-12-07
forum: General Help
---

### Post by chinmay3 on 2012-12-07
i have precise installed on mu HP-pavilion g series.  something gone wrong and clementine refused to launch. I purged & reinstalled it but no success. clicking on clementine doesn't show any sign of starting clementine. Output of commnat "clementine" in terminal is as follow.....

chinmay3@linuxbox:~$ clementine
16:01:45.513 DEBUG WorkerPool<HandlerType>:281      Starting worker 0x7f1d537933f0 "/usr/bin/clementine-tagreader" "/tmp/clementine_508716305" 
16:01:45.518 DEBUG WorkerPool<HandlerType>:281      Starting worker 0x7f1d537933f0 "/usr/bin/clementine-tagreader" "/tmp/clementine_1150202731" 
16:01:45.524 INFO  Database:548                     Updating "songs" for %allsongstables 
16:01:45.525 INFO  Database:548                     Updating "magnatune_songs" for %allsongstables 
16:01:45.526 INFO  Database:548                     Updating "jamendo.songs" for %allsongstables 
16:01:45.527 ERROR Database:595                     db error:  QSqlError(1, "Unable to execute statement", "duplicate column name: skipcount") 
16:01:45.527 ERROR Database:596                     faulty query:  "ALTER TABLE jamendo.songs ADD COLUMN skipcount INTEGER NOT NULL DEFAULT 0" 
16:01:45.527 ERROR Database:597                     bound values:  QMap() 
16:01:45.527 ERROR unknown                          Unable to update music library database 
16:01:45.528 INFO  main:46                          TagReader worker connecting to "/tmp/clementine_508716305" 
16:01:45.529 INFO  main:46                          TagReader worker connecting to "/tmp/clementine_1150202731" 
Aborted (core dumped)

searched different threads but not found any working solution. Desperately want clementine to play music.

---

### Post by stinkeye on 2012-12-07
You could try starting clementine with fresh settings.
Rename the folder **~/.config/Clementine** to **~/.config/Clementine.old** and try starting clementine.
You will have to add your library and do your preferences again.

---

### Post by Yellow Pasque on 2012-12-07
> **stinkeye said:**
> You could try starting clementine with fresh settings.
Rename the folder **~/.config/Clementine** to **~/.config/Clementine.old** and try starting clementine.
You will have to add your library and do your preferences again.
That's one possible solution, but the first thing I would try is disabling the jamendo plugin, since that looks to be causing the error. I'm not sure how to disable plugins in clementine off the top of my head. I'm playing with it in a n Ubuntu VM now. Let me get back to you on that..

---

### Post by chinmay3 on 2012-12-07
This worked fine. This seems that my old configuration files were the problem. But i have one question that previously I have removed clementine by 'purge' command then how my old configuration files  remained in my home folder?
Anyway  "THANKS A LOT"

---

### Post by stinkeye on 2012-12-08
> **chinmay3 said:**
> This worked fine. This seems that my old configuration files were the problem. But i have one question that previously I have removed clementine by 'purge' command then how my old configuration files  remained in my home folder?
Anyway  "THANKS A LOT"
Purge does not remove configs in your home folder. User configs are created in your home folder when you change preferences in the application.

---

