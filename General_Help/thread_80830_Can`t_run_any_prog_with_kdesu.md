---
title: "Can`t run any prog with kdesu"
date: 2005-10-23
forum: General Help
---

### Post by drolyk on 2005-10-23
Hi All!
I`m new with ubuntu and it`s my first post in this forum :)
My problem is kdesu. I can`t run any prog with that from ordinary user, eg when I launch "Adept" from kde menu it asks me a pass but when I enter root`s pass it gives me an error "Incorrect password; please try again".

Any help would be great :)

---

### Post by sightless on 2005-10-23
I ran into the same problem on a computer at work. What I did was I disabled the Kwallet. 

Go to the KDE control senter then Security & Privacy. You'll find Kwallet there.

---

### Post by drolyk on 2005-10-23
[QUOTE=sightless]I ran into the same problem on a computer at work. What I did was I disabled the Kwallet. 

Go to the KDE control senter then Security & Privacy. You'll find Kwallet there.[/QUOTE]

I just add in my sudoers file string like this:
drolyk  ALL=(ALL) ALL

and now I can get it work :)

---

### Post by daller on 2005-10-23
You entered the root pass???

In (K)ubuntu it is possible to use su without activating the su pass....

Per default, you are infact a sudoer!!!

run kdesu application, and use your normal password!

---

### Post by yhotg on 2005-10-23
same problem here, nothing with kdesu works.
i put my user in sudoers 
ALL= (ALL) ALL
but still the same.

any idea?

update
when doing kdesu <program> in the terminal i get this message:
kdesu_stub: user no does not exist!

it mean something to anybody?

---

### Post by mervc on 2005-10-26
[QUOTE=sightless]I ran into the same problem on a computer at work. What I did was I disabled the Kwallet. 

Go to the KDE control senter then Security & Privacy. You'll find Kwallet there.[/QUOTE]

No need to disable Kwallet, not for me anyway, I find it useful.  The main problem with Ubuntu for experienced users is the lack of a root user, but it keeps confounding newbies also.

The easiest solution is make root active by supplying a root password.  You must be the first user created, only that one has administrator privileges.  

sudo passwd root

and answer the prompts.

'su -'   and  kdesu will work flawlessly.

Since my documents, user config files etc., have been used on other distros I need to supply a different U.I.D. than the the one the admin user has.  Additional users do not have admin privileges by default.  For awhile I had the default user session running and another session for me.  However it was inconvenient and slow changing back and forth for all the system config changes I was making.  Adding myself to the admin group did not solve my sudo problems.  Hence my enabling 'root'.

Good luck

---

### Post by guess on 2005-12-11
I found the below to to be very useful from 
[http://consistencies.net/20051018/fixing-kdesu-problems-in-kubuntu/](http://consistencies.net/20051018/fixing-kdesu-problems-in-kubuntu/)

Fixing kdesu problems in Kubuntu

There seems to be a bug in kdesu causing problems when using sudo instead of su.

Symptom: When trying to switch to admin mode in one of kcontrol’s (or systemsettings) modules, the process fails and presents you kcontrol’s main window (or the same grayed-out module in systemsettings).

To solve this more elegant than just calling kcontrol manually using kdesu (which actually works), you can do the following:

    * set password for root (sudo passwd)
    * add


      [super-user-command]
      super-user-command=su

      to either

      ~/.kde/share/config/kdeglobals

      or

      /usr/share/kubuntu-default-settings/kde-profile/default/share/config/kdeglobals 

I also posted this to the ubuntu-forums, maybe someone else finds this useful.

---

