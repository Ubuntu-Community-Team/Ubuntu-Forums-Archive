---
title: "ssh connection: Not all programs can use it?"
date: 2007-05-11
forum: General Help
---

### Post by ernstblaauw on 2007-05-11
I used Places --> 'Connect to server' to create a link to a ssh account. If I double click on the link, it opens nautilus. I thought it would be treated just as an ordinary folder. However, I wanted to edit a .tex file. Thus, I double-clicked on the .tex file but Kile (my default for tex) was not started, but instead gedit. I tried to start Kile with 'Open With' --> 'Open with another application', but then Kile is started wiithout the tex file opened. It seems Kile cannot see the ssh connection. 
Is there a possibility that I can use the ssh connection with Kile? It would save me a lot of copying...

---

### Post by baka_rob on 2007-05-13
That's what I've noticed; the "connect to server" does something that only seems to be available to [some?] other Gnome applications.  E.g. you can't use any command-line utilities or things like that, either.

I'd suggest taking a look at sshfs, and making sshfs mounts.  Then it looks the same as a 'normal' folder to any/all applications.  I have yet to set it up on ubuntu, but:

[http://en.wikipedia.org/wiki/SSH_Filesystem](http://en.wikipedia.org/wiki/SSH_Filesystem)

It would be nice if what Gnome does could be implemented in such a way, but I haven't looked into it that far, myself.

---

### Post by ernstblaauw on 2007-05-14
That's what I've been looking for! However, I can't get it to work; look here:
[http://ubuntuforums.org/showthread.php?t=430312&highlight=sshfs](http://ubuntuforums.org/showthread.php?t=430312&highlight=sshfs)

---

