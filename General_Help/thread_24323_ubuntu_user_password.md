---
title: "ubuntu user password"
date: 2005-04-06
forum: General Help
---

### Post by karl_kashofer on 2005-04-06
Hi !

I run the live-cd on an apple mac, and have set up a samba share.

When I try to access it from another computer it asks for the password for the user ubuntu.

A password seems to be set for the ubuntu user, as passwd asks for one.

Can anyone here please post the password for the ubuntu user set by default on the live-cd?

Thanks,
Karl

---

### Post by Gandalf on 2005-04-06
[QUOTE=karl_kashofer]Hi !

I run the live-cd on an apple mac, and have set up a samba share.

When I try to access it from another computer it asks for the password for the user ubuntu.

A password seems to be set for the ubuntu user, as passwd asks for one.

Can anyone here please post the password for the ubuntu user set by default on the live-cd?

Thanks,
Karl[/QUOTE]
 there's no passwd by default, try to do
guest ok = yes
only guest = yes

in the smb.conf file under the directory you're trying to share
don't forget to restart samba [color=blue]sudo /etc/init.d/samba restart[/color]

---

### Post by karl_kashofer on 2005-04-06
Hi !

Thanks for the help, however when I open a console and type "passwd" it asks for a password, and just pressing enter does not work.

So there must be some kind of password right ?

Cheers,
Karl

---

### Post by Gandalf on 2005-04-06
[QUOTE=karl_kashofer]Hi !

Thanks for the help, however when I open a console and type "passwd" it asks for a password, and just pressing enter does not work.

So there must be some kind of password right ?

Cheers,
Karl[/QUOTE]
 well if you login and it doesn't ask for a password then there's no password and when you type passwd it asks you for a new password, not the old

---

### Post by karl_kashofer on 2005-04-06
Hi !

The live-cd seems to login as user ubuntu without asking for a password.

Just boot from the live-cd, on the desktop choose Applications,System,Terminal:

>ubuntu@ubuntu:~$ passwd
>Changing password for ubuntu
>(current) UNIX password:                  # I pressed enter
>passwd: Authentication failure
>ubuntu@ubuntu:~$

This does indicate to me at least that there is some password ?

Any clues ?

Cheers,
Karl

---

### Post by Gandalf on 2005-04-06
nope sorry don't have a clue of what's happening... :'(

---

### Post by scottlc on 2005-04-07
[QUOTE=karl_kashofer]Hi !

The live-cd seems to login as user ubuntu without asking for a password.

Just boot from the live-cd, on the desktop choose Applications,System,Terminal:

>ubuntu@ubuntu:~$ passwd
>Changing password for ubuntu
>(current) UNIX password:                  # I pressed enter
>passwd: Authentication failure
>ubuntu@ubuntu:~$

This does indicate to me at least that there is some password ?

Any clues ?

Cheers,
Karl[/QUOTE]
 Try:

sudo passwd ubuntu

---

### Post by karl_kashofer on 2005-04-09
Thanks ! That worked !

Cheers,
Karl

---

