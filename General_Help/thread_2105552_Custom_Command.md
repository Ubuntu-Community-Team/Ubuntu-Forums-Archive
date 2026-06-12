---
title: "Custom Command"
date: 2013-01-16
forum: General Help
---

### Post by jasper580 on 2013-01-16
Hi,
So, I'm repairing my nephew's laptop, by installing Linux on it. Because he is 9, I want to make everything easy to use. One of those things is converting rpm files to deb files automaticly.
I figured out already how to open a sh file, but how do I say like:
alien -d 'File'
What should 'File' be?
Thx in advance

---

### Post by Vaphell on 2013-01-16
if you want it to be easy, why don't you stick to the official repos and native debs in the first place?

---

### Post by percent20 on 2013-01-16
I would think 'File' would be the name of the rpm file.

[http://www.thegeekstuff.com/2010/11/alien-command-examples/](http://www.thegeekstuff.com/2010/11/alien-command-examples/)


That said why are you converting an RPM file to .deb? Are the packages you are after not in an apt repository?

---

### Post by jasper580 on 2013-01-16
> **Vaphell said:**
> if you want it to be easy, why don't you stick to the official repos and native debs in the first place?
Because I want it to be possible ;) I don't want them to ask me to come around, to find out that it would be something such stupid and simple, while I could've fixed it before I brought his laptop back.

> **percent20 said:**
> I would think 'File' would be the name of the rpm file.

[http://www.thegeekstuff.com/2010/11/alien-command-examples/](http://www.thegeekstuff.com/2010/11/alien-command-examples/)


That said why are you converting an RPM file to .deb? Are the packages you are after not in an apt repository?

It's more that I want him to be possible to install RPM packages without using the terminal.

But that was not really what I meant: I want that when he clicks the rpm file, an sh file executes that command (plus a few others), and that he doesn't need to type commands. So that command would be in an external sh file, so 'File' has to be like a variable which defines that filename. Does something like that exists?

---

