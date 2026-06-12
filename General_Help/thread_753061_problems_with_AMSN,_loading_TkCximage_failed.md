---
title: "problems with AMSN, loading TkCximage failed"
date: 2008-04-12
forum: General Help
---

### Post by Starlight on 2008-04-12
Hi! I'm having strange problems with aMSN. I had one installed by some script some time ago because the Ubuntu repositories didn't have the new version, but now they do, so I decided to install it from there... however, when I try to run aMSN, I get the "Loading TkCximage failed" error message. I've tried removing and purging amsn and all versions of tk and tcl which I have installed, but it didn't fix anything. When I was looking around the forums I found a link to a package with amsn 0.98, here's the link: [http://www.mediafire.com/?6l2dxbrbkmn](http://www.mediafire.com/?6l2dxbrbkmn) But when I install it, I get the error "/usr/local/amsn/bin/wish8.6: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory". I have that file, so I tried making a link to it in /usr/local/amsn/lib. Now aMSN tells me that the file has a "wrong ELF class: ELFCLASS64".

Is there some way I could install aMSN on my computer using packages, not scripts, so that it works?

---

### Post by Starlight on 2008-04-12
bump?

---

### Post by Claus7 on 2008-04-13
Hello,

yup! There are a lot of packages out there! Check this post to decide on your own!
[http://ubuntuforums.org/showthread.php?p=4555010#post4555010](http://ubuntuforums.org/showthread.php?p=4555010#post4555010)

EDIT: From the link I provide the ones that will fit to you are my installation and from the rest the 4th and the 5th! I do not think that you will have problems with mine because I donwload all the needed (at least the most important) libraries for amsn and I compile them in such a way that it can be done in every version of ubuntu. I haven't tested it in other distributions though.

EDIT2: I do not know for sure, yet, judging from the message you get, this might help you : 
```
sudo mv /usr/bin/wish /usr/bin/wish-backup
sudo ln -s /usr/bin/wish8.6 /usr/bin/wish
```

Hope this helped,
Regards!

---

### Post by tsktsk on 2008-07-18
That worked for me, thanks!! :popcorn:

---

