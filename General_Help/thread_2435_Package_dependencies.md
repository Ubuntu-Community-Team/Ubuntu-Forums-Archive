---
title: "Package dependencies"
date: 2004-10-28
forum: General Help
---

### Post by krojc on 2004-10-28
I use apt-get tu update or synaptic for that matter and I like as little packages installed as possible, which is a problem since I need to check every single one manually...
Is there a way to see which packages depend on one selected package?
All I get is packages that this certain package has dependencies to. If I want to know which depend on this one I need to try to remove it for synaptic to get a  responce and give me the answer.

In addition to this question: Is there a software that would sort packages in some kind of multi-tree way.

Thanks

---

### Post by Rancoras on 2004-10-28
In synaptic, just look at the properties sheet of the package.  The dependencies should be listed in there.

---

### Post by krojc on 2004-10-28
Exactly. There are packages that are predependent not "after" dependent. Am I right or not?

---

### Post by Rancoras on 2004-10-28
Sorry, I misread your post.  There may not be a way in synaptic to do that, I'm not sure.  There may be a way with apt from the command line, but, I confess, I'm not as up on the command line options for apt as I probably should be.

---

### Post by Juergen on 2004-10-28
I think you want 'apt-rdepends -r packagename'

---

### Post by krojc on 2004-10-29
I get an error command not found.  apt does not have that command. on ap<tab>

---

### Post by jdong on 2004-10-29
[http://64.233.167.104/search?q=cache:UetmzCYIzHsJ:www.die.net/doc/linux/man/man8/apt-cache.8.html+apt+reverse+dependencies&hl=en](http://64.233.167.104/search?q=cache:UetmzCYIzHsJ:www.die.net/doc/linux/man/man8/apt-cache.8.html+apt+reverse+dependencies&hl=en)

The apt-cache command is the one you want. Linked is a highlighted manpage.

---

### Post by Juergen on 2004-10-29
[QUOTE=krojc]I get an error command not found.  apt does not have that command. on ap<tab>[/QUOTE]

You have first to 'sudo apt-get install apt-rdepends'  ;-)
Look in synaptic at all entries starting with apt, there are some more interesting commands to find

---

