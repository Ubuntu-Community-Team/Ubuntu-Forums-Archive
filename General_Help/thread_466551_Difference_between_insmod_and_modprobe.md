---
title: "Difference between insmod and modprobe?"
date: 2007-06-06
forum: General Help
---

### Post by jfinkels on 2007-06-06
Is there a significant difference between insmod and modprobe? Doing a simple insert of a module, does the one I use make a difference?

---

### Post by mitch.c on 2007-06-08
In a nutshell... modprobe is smarter.

modprobe checks the specified modules dependencies and loads required modules first.

Generalization: insmod is to modprobe what dpkg is to apt-get
[URL="http://ubuntuforums.org/showthread.php?t=377083"]
[COLOR="Red"]UAResolved[/COLOR][/URL]

---

### Post by jfinkels on 2007-06-08
> **mitch.c said:**
> In a nutshell... modprobe is smarter.

modprobe checks the specified modules dependencies and loads required modules first.

Generalization: insmod is to modprobe what dpkg is to apt-get
[URL="http://ubuntuforums.org/showthread.php?t=377083"]
[COLOR="Red"]UAResolved[/COLOR][/URL]

Thanks, friend. And I appreciate what you're doing with the unanswered posts team.

---

