---
title: "deleted stuff in /bin/"
date: 2007-07-02
forum: General Help
---

### Post by box2 on 2007-07-02
aahhh, i thought i was in my chrooted environment /bin/ so i deleted a bunch of crap that i thought wasn't needed, only to find out it was my root /bin/ !

is there a way i can reinstall these binaries from the CD or something?  ... actually i think i rm'd mount too heh...

i have my ubuntu install CD with a bunch of .deb files of the different packages to be installed, but there are crazy tons of them and searching each package on google is yielding very little in the way of retrieving the tools that i've lost... hmmmm...

---

### Post by kerry_s on 2007-07-02
boot from the livecd and just copy /bin

---

### Post by box2 on 2007-07-02
ahhh, that's very good. thank you.

---

### Post by Brucevdk on 2007-07-02
> **kerry_s said:**
> boot from the livecd and just copy /bin

I'm wondering, it's possible doing so wouldn't restore everything that was deleted (for example packages that aren't installed on the LiveCD by default). I've only Googled around for a minute or so, but I'm wondering is there a better way to recover your system? Apart from creating and restoring backups that is. 

Is there for example an easy way to get apt-get to reinstall all installed packages? That would mean as long as your base system is intact, apt-get would restore it to the way it was before.

EDIT: here we go, first hit for *[apt-get "reinstall all packages"]("http://www.hantslug.org.uk/cgi-bin/wiki.pl?LinuxHints/DebianTips")*:
> 
Reinstall all packages

Sometimes there is a need to reinstall all packages currently on your system. This can be achieved by:

COLUMNS=200 dpkg -l | awk '/^ii/ {print $2}' | xargs apt-get --reinstall install

Note the use of the environment variable 'COLUMNS' which ensures that the package names are not truncated on output. A value of 200 is usually sufficient for those packages that have long names. 


Looks quite reasonable and logical to me.

---

### Post by kerry_s on 2007-07-02
interesting :popcorn:

---

