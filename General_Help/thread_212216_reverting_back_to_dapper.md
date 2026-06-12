---
title: "reverting back to dapper"
date: 2006-07-09
forum: General Help
---

### Post by insane_alien on 2006-07-09
ok, i was a retarded oaf and decided to have a go at beta testing edgy. it didn't go well. all my menus constantly flicker and are unusable.:oops: 

to revert back to dapper, do i just change my sources.list back to the dapper repos and do 'sudo apt-get dist-upgrade' or what?

---

### Post by mlind on 2006-07-09
I've never tried *downgrading* a whole distro, but use aptitude instead. It can downgrade packages. I don't think dist-upgrade is going to work here.

Try reinstalling ubuntu-minimal, ubuntu-standard and ubuntu-desktop. And you must install 2.15.xx kernel.

---

### Post by insane_alien on 2006-07-10
umm i've never really used aptitude. i always assumed it was identical to apt-get. what should i type into the command console?

---

### Post by mlind on 2006-07-10
> **insane_alien said:**
> umm i've never really used aptitude. i always assumed it was identical to apt-get. what should i type into the command console?

```

sudo aptitude reinstall *package*

```

or when you try to remove a package that's dependency for other, aptitude usually offers downgrade as a resolution too.

If you feel brave, you could just purge everything else except ubuntu-minimal, downgrade all necessary ubuntu minimal packages (those which are not on Dapper repository), then install ubuntu-standard and ubuntu-desktop back.

Then use deborphan to look any obsolete packages left by edgy.

---

### Post by panurge77 on 2006-07-10
This is said to work
[http://www.ubuntuforums.org/showthread.php?t=212526](http://www.ubuntuforums.org/showthread.php?t=212526)

---

### Post by insane_alien on 2006-07-10
just gave it a try, screen had big black chunks of missing graphics everywhere(i don't have a clue what caused this) so i just reinstalled and everything is now up and running.

---

