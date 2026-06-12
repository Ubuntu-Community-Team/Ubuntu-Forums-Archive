---
title: "Update manager download speeds"
date: 2007-07-11
forum: General Help
---

### Post by Tomlin on 2007-07-11
I received an "update notification" icon this morning. I believe there were 19 files. Fifteen are OpenOffice files (totalling 74 MB). I have a 1Mb/s connection and normally can download from the repositories at that speed. Today however, the speed is averaging around 20kB/s.

I can download other files (the latest Firefox and Abobe Reader, for instance) at my normal 1Mb/s speed.

Is it possible they're having problems with the servers today?

I'm running Dapper.

Here's my sources.list (nothing's been changed since I ran it last):

# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted

---

### Post by smoker on 2007-07-11
if you are in the usa or canada, i believe there are problems, there is a thread about it in the cafe.

sorry, it was mover to 'installations and updates', here's the link:
[http://ubuntuforums.org/showthread.php?t=498386](http://ubuntuforums.org/showthread.php?t=498386)

---

### Post by Tomlin on 2007-07-11
Thanks for the reply.

I guess I'll wait and see if it clears up.

---

### Post by AlexThomson_NZ on 2007-07-11
I noticed odd speeds as well (here in NZ using NZ servers).

Thankfully the oo-core download (the biggest one) was pretty nippy, but some of the others were strangly very slow.  Weird.

---

### Post by jspangler on 2007-07-11
I also had real slow downloads of those packages in Austria from Austrian server.

---

### Post by Tomlin on 2007-07-12
Everything was fine today.

All 74MB downloaded at 131kB/s.

---

