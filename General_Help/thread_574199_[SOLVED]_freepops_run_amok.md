---
title: "[SOLVED] freepops run amok"
date: 2007-10-12
forum: General Help
---

### Post by mandrill on 2007-10-12
I have freepops installed from their website, and everything was fine until yesterday. Now it consumes my cpu when accessing mail, and will not quit even after mail client closed. Have to manually stop process.Possibly to do with the latest updates yesterday? No clue. Also cannot seem to get terminal to uninstall it.  Anybody?

---

### Post by nikhilk on 2007-10-12
Have you have installed it from the deb provided on the freepops site? In that case I guess you installed it through dpkg. In that case you can uninstall it through dpkg -r <packagename>. Currently the package available on freepops is "freepops_0.2.5-1-bkm_i386.deb". Is this the package you installed?

---

### Post by mandrill on 2007-10-12
I am relatively certain that is the package, but do not remember precisely because it was over a month ago.

---

### Post by nikhilk on 2007-10-12
Just try
```
sudo dpkg -r freepops_0.2.5-1-bkm_i386.deb
```
It will throw an error if that is not the package you installed.

---

### Post by mandrill on 2007-10-12
got this: 

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
jim@monkey:~$  sudo dpkg -r freepops
(Reading database ... 118032 files and directories currently installed.)
Removing freepops ...
 * Stopping freepops daemon freepopsd                                           start-stop-daemon: warning: failed to kill 4966: No such process

so, it looks like it was removed. should re-install fix?

edit - it errored me on the package name, but....then I just ran it as freepops?

---

### Post by nikhilk on 2007-10-12
Yes, sounds like it has been uninstalled. Sure, you can give it one more try, see if installing it again fixes the problem.

---

### Post by mandrill on 2007-10-12
I appreciate your help, sir.....thank you!

---

### Post by nikhilk on 2007-10-12
You are welcome. Just doing my part for the community.

---

### Post by mandrill on 2007-10-12
Well - I uninstalled freepops. Then re-installed it from website. No go. Tried it from the repositories. Still no joy.
Why would it work for 5 weeks then go wonky?

Solved by dowloading gui updater and running updates

---

