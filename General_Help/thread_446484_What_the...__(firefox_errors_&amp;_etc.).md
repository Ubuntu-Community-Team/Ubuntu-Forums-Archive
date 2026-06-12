---
title: "What the...?  (firefox errors &amp; etc.)"
date: 2007-05-17
forum: General Help
---

### Post by Culito on 2007-05-17
Hello all,
Recently I've been messing around with flash and firefox (because I still don't have sound with flash 9.xx...reverting to flash 7 and giving up.)
Anyway, I go to start firefox and it never starts.  I think I might have been messing around with firefoxrc...So, I start it from the command line and I get:

Illegal instruction (core dumped)

So I uninstalled and reinstalled firefox using apt-get several times.  Same result.  Opera still works, but I have never liked it because it is noticeably way slower than swiftfox.

What gives?

---

### Post by kerry_s on 2007-05-17
Did you try deleting the .mozilla folder with the settings?(in nautilus ctrl+h to see the hidden files)

Have you tried any speed settings for opera, opera can be customized and tweaked just like firefox. I got mine at least twice as fast as any firefox or firefox spun versions, currently have swiftweasel. It took me a while to get it right though.

---

### Post by Culito on 2007-05-19
Huh, I deleted the .mozilla directory, uninstalled and reinstalled, same result:

Illegal instruction (core dumped)

I really like my firefox.  Just a personal preference, I guess.  How can I get it back?

---

### Post by Culito on 2007-05-19
Anyone?  Bueller?

---

### Post by kerry_s on 2007-05-20
Can you open a terminal and type> firefox, then copy and paste it here so we can see the whole error. left click drag to highlight and middle click to paste.

Also use synaptic to uninstall and install, when you uninstall select the remove completely from the right click.

---

### Post by Culito on 2007-05-20
> **kerry_s said:**
> Can you open a terminal and type> firefox, then copy and paste it here so we can see the whole error.

Ok.

cully@Culito:~$ firefox
Illegal instruction (core dumped)
cully@Culito:~$

That's it!   I uninstalled completely and re-installed in synaptic.  Same thing.  I'm stumped.

---

### Post by kerry_s on 2007-05-20
Are you the only user on that system?

Try uninstalling with synaptic again, but this time use sudo nautilus to make sure there are no firefox folders left, check /etc/firefox, /usr/lib/firefox, /usr/share/firefox and /usr/bin/firefox, also delete that hidden .mozilla folder. That should make sure everything is brand new.

Also i want you to install firefox from a different repo. In terminal do> sudo gedit /etc/apt/sources.list  <and add this->

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse

---

### Post by Culito on 2007-05-23
Thanks for all your help, kerry.
I just did a clean install - it was long overdue.

I think swiftfox was causing the errors, even though I uninstalled it....

---

