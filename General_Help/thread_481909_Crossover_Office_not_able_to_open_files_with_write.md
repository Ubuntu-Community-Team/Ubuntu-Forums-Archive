---
title: "Crossover Office not able to open files with write permission"
date: 2007-06-23
forum: General Help
---

### Post by Ng Oon-Ee on 2007-06-23
Hello all,

I'm new to Ubuntu and Linux in general, have already done two clean installs (messed up the first one with overambitious tweaking). Right now I've got Crossover Office working, but when I try to use it to open files on some of my mounted volumes, it opens them as read-only. I know I have write permission on those volumes, as I'm able to create new files and rename files there, but somehow Crossover Office doesn't seem able to open files with read permission.

To make things even more complicated, I AM able to save new files to the same volumes using Crossover Office.

Please advise.

---

### Post by Page on 2007-06-23
When you run everything through a compatibility layer like crossover (which is itself derived from wine) there are going to be a few problems.

Can you open and save the files in Openoffice?

---

### Post by Ng Oon-Ee on 2007-06-23
Yep I can, no problems with those.

I can print from Crossover Office, too. As well as full editing rights on files within my home/username folder, or within the virtual C drive created by Crossover Office.

Which, of course, doesn't help since the vast majority of my data is on a separate (internal) data partition.

Just to further elaborate, this occurs whether file permissions are set to 'root' or to my own username, and whatever the group permissions are.

---

### Post by Ng Oon-Ee on 2007-06-24
Anyone able to help?

---

### Post by Ng Oon-Ee on 2007-06-24
Oh nevermind, 'figured' it out....

Seems that deleting my bottle and reinstalling office XP using the default options (uses a win98 bottle, how counter-intuitive is that?) makes it work.

---

