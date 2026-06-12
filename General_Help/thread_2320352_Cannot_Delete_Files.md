---
title: "Cannot Delete Files"
date: 2016-04-13
forum: General Help
---

### Post by paul1945 on 2016-04-13
Copied some files from a CD to a directory, about 400 mb of them, but cannot delete these no matter what I try. Tried changing permission and sudo, but no dice. 
No doubt there is a simple solution, but I am stumped, so please let me now. Paul.:confused:

---

### Post by Bucky Ball on 2016-04-13
I'm presuming you mean you can't delete them from the hard drive, not the CD.

Open a terminal and, if you're using Ubuntu:

```
gksudo nautilus
```

If you're not, replace 'nautilus' with the name of your file manager. That will open the file manager as root. Try changing the permissions of ONLY that folder there. Once done, shut the window. Don't hang about in a file manager as root. You can create some serious breakage.

---

### Post by paul1945 on 2016-04-14
Hello Bucky Ball, Thanks for that, yes, they were on the hard drive, I have never had a problem deleting files from a CD or DVD, I have a sturdy thredder that does this for me ;-)
Anyhow, when I brought up Nautilus from the command line, I noted that it looked very much like the Ubuntu file system, so I decided to try gksudo on Krusader instead to avoid the serious breakage you spoke about. 
This worked a treat, thank you. I have since made a special launcher for Krusader that includes gksu in the command line, with an appropriate red icon to warn of the danger.

---

