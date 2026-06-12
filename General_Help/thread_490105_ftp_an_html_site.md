---
title: "ftp an html site?"
date: 2007-07-02
forum: General Help
---

### Post by GabrielWolff on 2007-07-02
Hey, I got access to an html site that looks very much just like an ftp site: no graphics, only files and folders.

Now, I want, instead of just downloading single files, download whole folders.

1) Is that possible using the html format?
2) I tried it with some ftp client, and the answer I got was NOT: "this is not an ftp server", but rather "the passowrd you are using is wrong" while I was using the same user and pass as I did before and after within Firefox. How come?

G

---

### Post by dfreer on 2007-07-02
well, you can't use FTP to download if there is no FTP server in place.
you can try out wget, as it can download a website, scanning recursively into folders (check it's man page for correct syntax).

---

