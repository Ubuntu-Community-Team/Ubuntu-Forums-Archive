---
title: "root problems"
date: 2007-02-09
forum: General Help
---

### Post by Scooter7 on 2007-02-09
Hi, I just downloaded  and installed XAMPP ([www.apachefriends.org](www.apachefriends.org)).   When I went to replace the default files in the htdocs directory with my own website pages, I found I could not because the entire directory is owned by root.   I think this is dumb, because I'm the only user on the computer, and I have administrator access.   But it requires that root do all the stuff.   The only way I know how to do things as root is to type 'sudo' into the command line... and I don't know enough about the thing to do everything in it.   Is there a way I can do stuff like renaming and deleting folders and files that are owned by root?

I'm using Ubuntu 6.10, with KDE.

---

### Post by izblah on 2007-02-09
You could run: 'chown' to change the owner of the files in question to YOU! Would that solve your problem?

You can find 'chown' syntax here: [http://www.computerhope.com/unix/uchown.htm](http://www.computerhope.com/unix/uchown.htm)

---

### Post by Scooter7 on 2007-02-09
Thanks, I tried that, and got this:

> chown: changing ownership of `htdocs': Operation not permitted

So, can I not change the ownership of directories with that command?

-EDIT-

I also tried it on the index.html file... I got the same error as above.

---

### Post by melancholeric on 2007-02-09
did you use sudo?

---

### Post by Maestro23 on 2007-02-09
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Scooter7 on 2007-02-09
Oh, no, srry... normally I would think of that, but right now I'm soo tired. :)

Thanks again guys... it works! ^_^

---

