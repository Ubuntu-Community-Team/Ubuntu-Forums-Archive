---
title: "Migrating from old Courier-imap to Gmail"
date: 2012-10-24
forum: General Help
---

### Post by lildoggie on 2012-10-24
Hi,

I've got an old Dapper (6.06) installation running courier-imap that we've been using for a long time, and it's on its last legs.  We've decided to move all our email to a Google Apps setup.

I have been able to migrate some of the email by connecting to both the local server and the gmail imap server, and then dragging messages from one to the other.  Unfortunately, there are some of the messages that just won't transfer (and there are many other folks reporting the same issue).

It appears that the best solution is to install imapsync.  When I try  sudo apt-get install imapsync, I am told that it needs to install several additional packages such as libio-socket-ssl-perl.  Sure, no problem.  However, those packages aren't available, so the installation fails.  

Where would I get those needed files?

Here's my edited sources.list:```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb http://flomertens.free.fr/ubuntu/ dapper main main-all


deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
```
Any help is much appreciated!

---

### Post by suppo84 on 2013-06-11
This is old thread but i had similar problem couple days ago. I need move our company employees mailboxes to new server. I just find program called Mailbox Ranger from Ubuntu software center and it made my day easily!

---

### Post by fantab on 2013-06-11
> **suppo84 said:**
> This is old thread but i had similar problem couple days ago. I need move our company employees mailboxes to new server. I just find program called Mailbox Ranger from Ubuntu software center and it made my day easily!

Start your own thread with an appropriate title and detail out YOUR problem. Also tell us what all you have done to resolve the issue.

---

