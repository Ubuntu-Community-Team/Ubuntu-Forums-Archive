---
title: "apt-get corrupted.  Can't install"
date: 2008-03-30
forum: General Help
---

### Post by Ralph Boland on 2008-03-30
I tried to install java 1.6 (using apt-get install .... I have lost the exact command executed)
When I got a window asking me to read sun's installation agreement 
the window would not respond to my keyboard or mouse.  
Since I was unable to confirm my acceptance
I eventually had to kill the window and start over.

But my second attempt failed.  
A lock file in /var/lib/dpkg seemed to be in the way so I moved it.

My third attempt went further but in the end I got messages like:

E: /var/cache/apt/archives/sun-java6-bin_6-03-0ubuntu2_i386.deb: subprocess pre-installation script returned error exit status 1
E: /var/cache/apt/archives/sun-java6-jre_6-03-0ubuntu2_all.deb: subprocess pre-installation script returned error exit status 1

(Here I tried to reinstall sun-java6-bin and sun-java-jre from the synaptic package manager)

Now I can't even install other packages. 
Furthermore, once a package install fails I cannot remove the package either.

How do I clean up this mess?

Thanks

Ralph Boland

---

### Post by -grubby on 2008-03-30
I can't exactly solve your problem , but, when the dialog box comes up, press any of your arrow keys to select

---

### Post by kellemes on 2008-03-30
```
sudo apt-get -f install
sudo apt-get update
```

---

### Post by Ralph Boland on 2008-03-30
as adviced I ran

       sudo apt-get -f install

It returns a pile of stuff (see attachment) ending with:
                       E: Sub-process /usr/bin/dpkg returned an error code (1)

This leaves a lock file in /var/lib/dbkg which I moved.
I then ran:

     sudo apt-get update

It runs without complaint but leaves the lock file again.
I moved the lock file again and again tried:

       sudo apt-get -f install

I get the same result, including the reported error and a leftover lock file.


If I move the lock file and try to install, say lyx,  then I get a pile of stuff
followed the same error as
the  "sudo apt-get -f install command.

So thanks for the useful advice but I am still in need of help.

What do I try next?

Ralph

---

### Post by Wicked-Cricket on 2008-06-26
I am getting the same issue... was this resolved somehow?

Thanks

---

