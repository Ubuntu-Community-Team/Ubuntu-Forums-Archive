---
title: "Cloning an installation - without copying everything"
date: 2014-09-04
forum: General Help
---

### Post by peter.h.m.brooks on 2014-09-04
I've got a working system at home, and a broken one at a remote location - it's slow and expensive to copy files there.

What I'd like to do is get an apt-get summary of my machine, so I can just run it on the remote machine and, when it is finished, know that the two have the same base software - then all I have to copy is the config and database files.

Is there an easy way to do this?

If I can, then I was thinking to just copy things that aren't there already - a find on each system and a diff should do the trick.

Does this make sense? I've had a look at apt-get and apt-cache, but it's not obvious to me where the version directory is - presumably copying that and then doing an apt-get update on the remote machine should do it -- or is there more to it than that?

---

### Post by lukeiamyourfather on 2014-09-04
You can get a list of everything installed ever with this command. If you want you can redirect it to a text file to reference later. 

```
dpkg --get-selections | grep -v deinstall
```

Most of the configuration files for services are in /etc so if you backup that you should be able to get most of what you need. I don't know if I'd blanket copy everything over to another system but figure out exactly the services you want to setup and then just copy those over.

---

### Post by papibe on 2014-09-04
Hi peter.h.m.brooks.

You can use the 'get and set selections' method. [Here]("http://askubuntu.com/questions/32007/how-to-find-manually-installed-packages")'s how to do it.

Regards.

EDIT: if you have PPAs you may also want to make a look at this: [How To Backup Your Ubuntu Software]("http://www.matthartley.com/how-to-backup-your-ubuntu-software/").

---

### Post by peter.h.m.brooks on 2014-09-10
Thank you!

---

### Post by peter.h.m.brooks on 2014-09-10
Perfect, thank you!

---

