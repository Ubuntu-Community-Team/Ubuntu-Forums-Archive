---
title: "Newby cant install Samba (broken packages error libcupsys2-gnutls10)"
date: 2007-02-10
forum: General Help
---

### Post by BodleyTunes on 2007-02-10
Hi all,

I'm a Linux newby trying to install Samba on my ubuntu box.  The server is running webmin and I want to be able to manage my samba through that.

Anyway when using the command:

apt-get install samba

I get the following error:

[IMG]http://pics.bodleytunes.com:81/samba.gif[/IMG]

Can anyone help me I'm pulling my hair out!  :(  I think its something to do with libcupsys2-gnutls10 or whatever that is!

Kind regards,

Jon.

:)

---

### Post by dannyboy79 on 2007-02-10
well, all you really have to do is read the error and perform what it wants you to. so install what samba depends on according to the error, libcupsys2-gnutls10.

so try sudo aptitude install libcupsys2-gnutls10 and then try to install samba. also I would always suggest  using aptitude over apt-get because aptitude can handle REMOVING dependent programs when they were installed where as apt-get can't and doesn't uninstall dependent programs which will and does leave unneeded apps or libs on your computer.

---

### Post by BodleyTunes on 2007-02-10
Thanks matey, I normally do use aptitude, its just I follow lots of howto's blindly like a novice and end up using both :)

I'll try what you suggested.

Ta,

Jon.

---

### Post by BodleyTunes on 2007-02-10
tried installing libcupsys2-gnutls10 with aptitude and get this:

[IMG]http://pics.bodleytunes.com:81/samba2.gif[/IMG]

It looks like its not actually installed anything.  Samba still doesnt install afterwards either :(

---

### Post by dannyboy79 on 2007-02-10
again, simply read the error and try to fix it based on what it says. it appears as though you need a later version of libcupsys2-gnutls10 but aptitude is trying to download a earlier version?
this this first

sudo aptitude update

you always need to run the update prior to ever trying to install stuff. I am guessing that you didn't do this and that's why aptitude can't find the later version of the libcupsys2 blah blah.

 if that doesn't work have you tried to use the -f option which force a fix of dependencies? be careful though, read exactly what it states before saying yes or no. I have used the -f once and it then all of a sudden uninstalled a bunch of stuff I didn't want it to. so try this

sudo aptitude install -f libcupsys2-gnutls10
and then the same thing with samba.

---

### Post by BodleyTunes on 2007-02-10
Okay, thanks matey, I will try that.

Jon.

---

### Post by BodleyTunes on 2007-02-10
Still problems, I get this when trying to install libcup...


The following packages have unmet dependencies:
  libcupsys2: Conflicts: libcupsys2-gnutls10 (<= 1.1.23-11) but 1.1.23-10ubuntu4 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
libcupsys2-gnutls10 [Not Installed]

Score is -1

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
root@jmc-ubuntu:/home/jon#

Seems to have not done anything?

---

### Post by dannyboy79 on 2007-02-10
did you try EVERYTHING i suggested? if so than I can't help you anymore.

---

