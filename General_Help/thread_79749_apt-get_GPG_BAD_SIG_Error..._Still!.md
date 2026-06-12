---
title: "apt-get GPG BAD SIG Error... Still!"
date: 2005-10-20
forum: General Help
---

### Post by gbusse on 2005-10-20
Greetings,

I know, I am getting tired of this too, but there has to be something wrong. I have read ALL of the posts I can find and have tried ALL of the suggestions I could find. My repo's originally all had a "ca." in front of them which WAS working fine up until about a few days ago. I have tried removing the "ca." from in front where ever it had existed but I am still getting these GPG BAD SIG errors.

The error always seems to be on the SAME repo. I have checked and double checked my configuration. The repo that seems to always have the problem is:

[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates

None of the other ones have ever, to my knowledge, produced this error. Something must be wrong with this repo. Something has to have gone wonky with it. I have even tried re-installing Breezy again from scratch as this is how annoying this is. I like a smoothly running OS and hate seeing errors like this that I cannot seem to do anything about. 

This is the first time EVER using Ubuntu that I have not been able to fix a problem with my system and it is totally driving me up the wall. 

I know bug reports have been submitted about this but has anything been done about it, do they even care?

Should I send an email to the address [email]ftpmaster@ubuntu.com[/email] that is mentioned in the error message?

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

It is ALWAYS this same error...

FWIW, here is my sources.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
# deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras-staging main restricted universe multiverse

Is there anything wrong with it?

Ok rant mode off... back to beating on my computer... :???: 

Later,
Gordo

---

### Post by hajk on 2005-10-21
Looking at your sources.list.... I don't think there are breezy-updates for universe and multiverse; and no breezy-security for multiverse either.:confused:

---

### Post by sanitys3j on 2005-10-21
See mine here, exactly the same.

[http://ubuntuforums.org/showthread.php?t=80120&highlight=breezy-updates+Release+key]("http://ubuntuforums.org/showthread.php?t=80120&highlight=breezy-updates+Release+key")

I've attempted taking out ALL universe & multiverse to no avail.  I did find a temp work around here though....

[http://www.ubuntuforums.org/showthread.php?p=416599&posted=1#post416599]("http://www.ubuntuforums.org/showthread.php?p=416599&posted=1#post416599")

Hope this does it for you, at least for now.

Universally,
3j

---

