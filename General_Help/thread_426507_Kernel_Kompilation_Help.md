---
title: "Kernel Kompilation Help"
date: 2007-04-28
forum: General Help
---

### Post by nullfactor on 2007-04-28
When attempting to recompile my 2.6.20-15-generic kernel, I do a make install and get the following:

Can't open /usr/src/linux-headers-2.6.20-15-generic/arch/i386/boot/install.sh

Sure enough... that file does not exist.  Any idea as to where I can get it, or what I have to do to where I can compile my kernel?

Thanks for the help, in advance!

---

### Post by pseudonym on 2007-04-28
make install? I don't think you need to run that when building an Ubuntu/Debian kernel. This howto - [http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel+compile]("http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel+compile") has all the steps you need to follow (indeed more than that - it's not really necessary to build either the headers or modules_image package, even though most of the guides out there tell you to).

---

### Post by nullfactor on 2007-04-28
Thanks, Pseudonym... if, indeed, that is your REAL name... ;)

I'll check that link out and give 'er a try.  Thanks, again!

---

### Post by pseudonym on 2007-04-28
> **nullfactor said:**
> Thanks, Pseudonym... Glad I could help.

Now, I don't suppose you could shed any light on my problem - [http://ubuntuforums.org/showthread.php?t=426511]("http://ubuntuforums.org/showthread.php?t=426511")? :confused: 
> **nullfactor said:**
> if, indeed, that is your REAL name... ;) well, it's my real false name ;)

---

### Post by dreadlord_chris on 2007-04-28
> **pseudonym said:**
> Glad I could help.

Now, I don't suppose you could shed any light on my problem - [http://ubuntuforums.org/showthread.php?t=426511]("http://ubuntuforums.org/showthread.php?t=426511")? :confused: 
 well, it's my real false name ;)

LOL... I have a friend named Alias - real, real first name.....

---

### Post by pseudonym on 2007-04-28
> **dreadlord_chris said:**
> LOL... I have a friend named Alias - real, real first name..... hehe, that'd look weird filling out a form - Name: Alias :)

That was one of my other choices for a username, btw. That and 'nom de plume', but I thought that was too fancy. So I settled on pseudonym, which is somewhere in the middle. :)

---

