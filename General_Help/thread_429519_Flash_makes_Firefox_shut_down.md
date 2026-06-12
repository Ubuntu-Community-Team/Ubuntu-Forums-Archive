---
title: "Flash makes Firefox shut down"
date: 2007-05-01
forum: General Help
---

### Post by radiors on 2007-05-01
I am still running Dapper and I have Firefox 2.0.0.3. Whenever I open a page that uses Flash, the page starts loading and then Firefox completely shuts down.  I have looked in the posts on this forum that talk about Flash causing Firefox to "crash" and I have tried all the applicable solutions presented there.  But nothing works. If I remove Flash from the plugins directory, then everything goes back to normal--except I don't have Flash, of course.

I have tried removing Flash and reinstalling it umpteen times, including uninstalling the "free" version.  My default color depth in xorg.conf is 24.  Basically, I think I have tried everything suggested on the Forum, but nothing works to solve the problem.

I have an nVidia 6200.  The driver is installed and working fine with other programs and games.

Any new ideas would be greatly appreciated?

---

### Post by taurus on 2007-05-01
What version of flash did you use?  Try to install the latest version, 9.0, and see if it still crashes your machine.

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by radiors on 2007-05-01
I guess I forgot to mention that I am already using Flash 9.

Thanks.

---

### Post by radiors on 2007-05-01
I haven't gotten much response to this question.  So I dug a little deeper and  found out something new.  When I start Firefox from inside Terminal I get the following error message after Firefox dumps:

/opt/firefox/run-mozilla.sh: line 131:  5965 Segmentation fault      "$prog" ${1 +"$@"}

Does anyone know what that all means?

Thanks..

---

### Post by steveneddy on 2007-06-05
I believe the answer is [here]("http://ubuntuforums.org/showthread.php?p=2787287#post2787287").

All three steps fixed my crash problem while surfing YouTube in Firefox.

Good Luck - SE

---

