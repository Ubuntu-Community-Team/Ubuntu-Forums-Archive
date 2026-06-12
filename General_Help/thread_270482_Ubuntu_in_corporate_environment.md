---
title: "Ubuntu in corporate environment"
date: 2006-10-03
forum: General Help
---

### Post by Bavo on 2006-10-03
Hi all,

first of all i'd like to say that I really love Ubuntu, and i think that it is quite ready for a personal desktop.
However I think that there is still quite some work to do to use it in a corporate environment.

I'm a network administrator and i'm planning to migrate all the desktop pc's here to Ubuntu (they are currently running Gentoo). But i've come across quite some problems and limitations already.

First of all the most important thing (at least for me). Ldap integration. We are using an ldapserver over a secure connection to manage the useraccounts. It's not to hard to implement user authentication with ldap, but it doesn't feel right, i think that it should be better implemented.
I still have a major problem with the ldap user-authentication, whenever i lock the screen in gnome, it gets locked, and you can't unlock it, it keeps saying wong password. (the only way to unlock it is to kill gnome-screensaver from a console)
KDE's lock seemed to have the same problem, but that was fixed by making /etc/libnss-ldap.conf and /etc/pam_ldap.conf world readable, witch is something you really don't want to do since it contains a password to connect to the ldapserver.
As long as i can't get this fixed, i cant start to deploy my ubuntu installation.

I also had some comments about configuring and locking the desktop and menu, but i just started testing out sabayon, i'll get back to this later. But so far this looks like a real good tool.

Another thing i have yet to do some research for is an easy way to install new packages/ updates on all the clients.
What i have in mind is setting up a local repository and apt-get update & apt-get upgrade in a cron job every night. I could do this from the official repo's. But considering the fact that some recent updates broke some desktops, i'd like to test updates before installing them on all the clients.
Is there an easy way to do this? 

So in short what i think is needed for buisnesses to use ubuntu as their desktops is:
- Better ldap-integration
- An easy and safe way to update all clients
- Documentation on how to integrate ubuntu in an existing network configuration

---

### Post by Bavo on 2006-10-03
It looks like sabayon can't be used to change the menu.

Is there any sane way to create and arrange the menu so that it is the same for every user (in gnome)?

I'm not exactly keen on the idea to edit all the *.desktop-files in order to arrange the menu the way i'd like to see it.

Any suggestions?

---

### Post by Ocxic on 2006-10-03
well if you made a custome menu, with the .desktop-files and if your keeping every installation the same, then you should just be able to copy the files to every new machien.

or better yet, make the computers thin/thick clients that use a NFS root, that way there is only one root partiton you have to manage and everyone can run off of a central server, then you only have to configure a minimal number of systems, while making administration, and updating easier.

---

### Post by Bavo on 2006-10-04
I haven't made a cutom menu yet. I'd first like to know if there is any other way to do it than to edit .desktop-files.

However I might have a look at the idea to have an nfs root. The home directories are on nfs already, so it shouldn't be to hard to implement. But using an NFS-root also causes some problems, you'll need to mount / read-only, so there has to be a other partition for at least /etc and /tmp, which means that if a configfile needs to be updated, it has to be updated on every single machine somehow. Most configfiles will be the same for every machine but some will/must be different (xorg.conf, network configuration files, ...)

---

