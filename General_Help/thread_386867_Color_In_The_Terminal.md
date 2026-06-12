---
title: "Color In The Terminal"
date: 2007-03-17
forum: General Help
---

### Post by Ek0nomik on 2007-03-17
I've seen people color their terminal and I was wondering if you can do it without having to install another program?  For an example:

[COLOR="MediumTurquoise"]fleur[/COLOR]@[COLOR="Blue"]fleur-laptop[/COLOR]:~$

Is there an easy way to do it?

Thanks!

---

### Post by llamakc on 2007-03-17
Yes, research "bash color prompt".

I use this:

```
PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h \T\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
```in my .bashrc. Mine is just one color though.

Which looks like this, btw:

```

[COLOR=Lime] ken@lken@llamakc 03:31:21[/COLOR]:[COLOR=Blue]~[/COLOR]$ 

```

---

### Post by hikaricore on 2007-03-17
You'll need to search around for posts and howtos about: .bashrc

Here's one I tracked down:

[http://ubuntuforums.org/showthread.php?t=229991&highlight=.bashrc+colors](http://ubuntuforums.org/showthread.php?t=229991&highlight=.bashrc+colors)

---

### Post by strabes on 2007-03-17
[http://strabes.wordpress.com/2006/11/17/change-the-color-of-your-username-in-the-terminal-in-ubuntu/](http://strabes.wordpress.com/2006/11/17/change-the-color-of-your-username-in-the-terminal-in-ubuntu/)

---

### Post by Ek0nomik on 2007-03-18
Thanks for the responses chaps.  I appreciate it.  ;)

---

### Post by nerdman978 on 2007-03-18
mine came with the themes I got it was a black background with green writing. It had a cool matrix feel

---

