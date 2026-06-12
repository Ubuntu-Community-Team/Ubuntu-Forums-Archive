---
title: "Totem wmv files"
date: 2005-04-02
forum: General Help
---

### Post by Jujimufu on 2005-04-02
How do you get Totem to play wmv's?

---

### Post by bored2k on 2005-04-02
[QUOTE=Jujimufu]How do you get Totem to play wmv's?[/QUOTE]
 [http://ubuntuguide.org/temp/#codecs](http://ubuntuguide.org/temp/#codecs)

---

### Post by Jujimufu on 2005-04-02
> root@____:/home/___ # sudo apt-get install w32codec
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

?? Where did it go? :)

---

### Post by lgb on 2005-04-02
Did you update your repository list?

---

### Post by wapowell on 2005-04-03
[QUOTE=Jujimufu]?? Where did it go? :)[/QUOTE]

Make sure you are searching for w32codecs.  Your screenshot shows w32codec.

Also, I got the same error until I added  deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main to my repositories AND added the keys just like it said to in the guide.

---

### Post by Jujimufu on 2005-04-03
Ah yeah, that worked!  Thanks a lot guys! I didn't expect I'd have to do anything like that to get wmv's to play, but I was wrong.  Thanks again.  : )

---

### Post by rduch on 2005-04-07
[QUOTE=wapowell]Make sure you are searching for w32codecs.  Your screenshot shows w32codec.

Also, I got the same error until I added  deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main to my repositories AND added the keys just like it said to in the guide.[/QUOTE]

I just tried to add the keys and got an error for the second line....

sudo: apt key: command not found
gpg: [stdout]: write error: Broken pipe
gpg: iobuf_flush failed on close: file write error

I double checked to see if typed the command as written in the guide and everything checked out Ok. Any ideas? 

BTW I added the codecs per a version of the guide that I printed fairly recently and it did not have the add keys commands in that version. Lesson: keep checking the guide for updates if you are having a problem.

---

