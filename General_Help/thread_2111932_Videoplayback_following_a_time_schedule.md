---
title: "Videoplayback following a time schedule"
date: 2013-02-03
forum: General Help
---

### Post by Gaute91 on 2013-02-03
Hello,

As the title says, is there a program or an easy way to set up a Videoplayback that follows a timeschedule? Like if it starts playing one file 15:00, and when that file is done, it starts a loop with videofiles until 17:00 when it starts another file, and so on.

I know this might be possible in VLC with some scripting, or is there maybe a complete solution for this already?

Thanks!

---

### Post by Hadaka on 2013-02-03
Hi, you can create crontab jobs ,here is a nice "how to" with examples
[http://www.thegeekstuff.com/2009/06/15-practical-crontab-examples/](http://www.thegeekstuff.com/2009/06/15-practical-crontab-examples/)

also...if you use gedit as your editor, crontab doesnt use gedit by default.
to set gedit as your crontab editor,append the following to .bashrc in your
home directory. *Note the "."  .bashrc    hidden file..to view
```
ls -al .bashrc
cat .bashrc
``````
#sets gedit as default for crontab
export EDITOR=gedit
 
```have fun !

---

