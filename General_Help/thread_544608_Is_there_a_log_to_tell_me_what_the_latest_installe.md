---
title: "Is there a log to tell me what the latest installed packages were?"
date: 2007-09-06
forum: General Help
---

### Post by LodeRunner on 2007-09-06
I've been running [Interactive Brokers']("http://www.interactivebrokers.com/") TraderWorkstation software for a year now with no problems (other than easily solved ttf-gujarati-fonts package issue) until yesterday, when it mysteriously stopped working.  Instead of launching the GUI login window, it just sits there in bash, doing nothing visible.  This behavior started happening on my desktop and my laptop at the same time, and it persists even when using an alternate internet connection.

The only thing I can think of is that a recent system update has affected it--that would explain why both computers were affected. Trouble is, I haven't logged into TWS in about a week so I don't recall which updates I've been installing lately.  Is there some way for me to list the most recently installed packages?  If not, does anyone know of a recent update likely to affect Java?

Running Feisty on both boxes with the repository list from the [Ubuntu Guide ]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories").

---

### Post by pmg on 2007-09-06
The default log file is **/var/log/dpkg.log** and it rotates monthly, so last months file is /var/log/dpkg.log.1.  Also, the default can be changed in the file /etc/dpkg/dpkg.conf (in case you don't see it in the above location.)

---

### Post by LodeRunner on 2007-09-08
Thanks, exactly what I needed.  I kept looking for a way to do it with dpkg-query...

[my problems have [multiplied]("http://ubuntuforums.org/showthread.php?p=3330441#post3330441"), however...]

---

