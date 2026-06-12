---
title: "Securing personal documents"
date: 2005-10-21
forum: General Help
---

### Post by cparsons on 2005-10-21
is there any way to password protect folders of private files?

---

### Post by poptones on 2005-10-21
How secure do you want them? There is a loopback tool you can use to make an encrypted "folder" of fixed size (if it gets filled just make another larger one and move the stuff to it and delete the old folder). But iencrypting just a few files or folders on your drive does nothing to secure those files from being disovered - for example, opening one will leave its name and path in your recent documents list - and because most applications use the /tmp folder to work on data, odds are good a copy of it wouod end up there where it could be discovered by a knowledgable user.

Encryption, if it's not deployed properly, can be quite dangerous as it gives one a false sense of security. If these are just files you don't want other users to be able to access, put them in a hidden folder (one that starts with a period . ) and give "execute, read and write" permissions on that folder only to yourself.

---

### Post by cparsons on 2005-10-22
basically, i am the only person using my laptop, but i leave it on my work station un-atteneded, and i would like a something along the lines of a password to open the folder. 

I don't need a "110%-secure-lock-down" of my files, but i would just like the password to basically remind people that those are my personal files. 

at the end of the day, i am confortable with my work environment, and i trust that that sould be enough to keep people away from a select few of my files.

---

