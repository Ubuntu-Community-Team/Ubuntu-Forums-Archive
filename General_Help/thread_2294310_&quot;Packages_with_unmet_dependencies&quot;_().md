---
title: "&quot;Packages with unmet dependencies&quot; (??)"
date: 2015-09-10
forum: General Help
---

### Post by logie on 2015-09-10
I'm not an absolute beginner, but pretty close.  I have an Intel NUCi3 minicomputer, with an Intel i3 chip, running Ubuntu 14.04.  It worked OK for a few months, but then started to send  error messages while booting: two windows, both similar.  
  I have found this error message:

E: Encountered a section with no Package: header
     E: Problem with     Mergelist/var/lib/apt/lists/
gb.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en
     E: The package lists or status file could not be     parsed or opened.

"This usually means that your installed packages have unmet dependencies"

   


If I open the Package manager, I get a repeat of the error message, with the addition:
 E:_cache ->open() failed, please report.
 

I cannot connect the emergence of the fault with anything particular that I did, and I'd be grateful for any help.  For example: would it help to re-install Ubuntu 14.04, or a later version, and then be careful about adding things (such as GIMP)?

 (Really, ANY help!)

---

### Post by Bashing-om on 2015-09-10
logie; Hello;

The more likely cause of this situation is a corrupt control file.
Try this:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade #only installs new software for this install version 

```

Reboot the system to see the total effect .

[INDENT][INDENT]all good now
[/INDENT][/INDENT]

---

### Post by logie on 2015-09-12
Many thanks for your help: it worked right away.

---

### Post by Bashing-om on 2015-09-12
logie; Great !

Pleased ya up and all good now .

As this situation is now under control:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]and Happy trails to You
[/INDENT][/INDENT]

---

### Post by Bearly Able on 2015-09-16
Thanks, Bashing-om.  I just encountered the same issue and your solution has solved it.

---

### Post by Bashing-om on 2015-09-16
Bearly Able; Good deal !

> **Bearly Able said:**
> Thanks, Bashing-om.  I just encountered the same issue and your solution has solved it.

The better thing about this forum, the ability to search and see a solution.

It is rare indeed that there is
[INDENT][INDENT]something new under the sun of 'buntu
[/INDENT][/INDENT]

---

