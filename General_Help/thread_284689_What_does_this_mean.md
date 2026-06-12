---
title: "What does this mean?"
date: 2006-10-26
forum: General Help
---

### Post by helmeteye on 2006-10-26
I have "edgy" and did the gedit sources.list and this is what I got along with a sources.list:  What does it mean?

(gedit:8978): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by aysiu on 2006-10-26
Did Gedit open when you got that message?

Read the bottom of this page (actually, read the whole page):
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by helmeteye on 2006-10-26
yea.  The list did open but I still am not knowledgeable enough to know exactly what it meant.  I will now read that link you supplied and see if I am anymore knowledgeable.  

     Everything seems ok then. I think.  Can't wait till I am more knowledgeable.  I have read the stuff and this paragraph is an edit since then.

---

### Post by helmeteye on 2006-10-26
This is my sources list.  Is there anything wrong with it?


deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by aysiu on 2006-10-26
I think it should be okay.

---

### Post by nikhilk on 2006-10-26
@helmeteye

Have you recently changed your hostname?
If yes make sure that the hostnames in "/etc/hosts" and "/etc/hostname" match.

---

### Post by helmeteye on 2006-10-27
> **nikhilk said:**
> @helmeteye

Have you recently changed your hostname?
If yes make sure that the hostnames in "/etc/hosts" and "/etc/hostname" match.

     I know this will sound really bad, but, I don't even know how to get to that.  I typed gedit /ect/hosts and it gave me IP stuff.

     What I get is:  localhost
                     my host name

     My host name is underneath the local host should there be a local host or should they both me my host name.

---

### Post by nikhilk on 2006-10-27
The contents of the file on my machine are like
127.0.0.1 localhost.localdomain localhost hostname

Where obviously hostname will be the actual hostname you have selected.
If this file is really the source of the problem you should be facing difficulties while running anything with "sudo".

---

