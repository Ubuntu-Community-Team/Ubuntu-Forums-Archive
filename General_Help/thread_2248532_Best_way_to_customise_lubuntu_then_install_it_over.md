---
title: "Best way to customise lubuntu then install it over the network to 20+ pcs"
date: 2014-10-15
forum: General Help
---

### Post by JazzPotato on 2014-10-15
Hi there,
My organisation is currently undergoing a switch from windows to linux for all office pcs. The next phase of the project is to actually roll out the new pcs with linux.
I need to customise a lubuntu iso so that it comes with all of our chosen packages (thunderbird, libreoffice, xcowsay, the essentials) the iso must also be customised to such an extent that our custom wallpaper, plymouth theme, thunderbird mail accounts, lxde configuration and even location of shortcuts on the desktop is the same out of the box. This is because we have a window of one working day to get this going to cause minimum disruption to business.
I have already configured a lubuntu 14.04 virtual machine on my laptop to the management's specifications.

All of this needs to be installed concurrently over the network to 20+ pcs.

Essentially, when the staff rub their starry eyes on monday morning and switch on their pcs, this is what they need to see:
[ATTACH=CONFIG]257233[/ATTACH]
And I really don't want to have to go around to each pc and configure things 20 times.

So, what is the best tool to take an image of my virtual machine and make it into a netbootable image?

Thanks alot,
Gary

---

### Post by TheFu on 2014-10-15
Perhaps cobbler is what you really want? [http://www.cobblerd.org/](http://www.cobblerd.org/)

Then you'll want something like ansible to maintain the systems. [http://docs.ansible.com/intro_getting_started.html](http://docs.ansible.com/intro_getting_started.html) - there is a great quickstart for Ansible video.

To me, managing images is NOT the best way to address Linux systems.  I have a minimal install with ssh-server, then use ansible for everything.

It may be that cobbler is too complex for just 20 systems. We can use almost any of the partition cloning tools to load images - clonezilla, partimage, .... these can be scripted from a floppy or flash media to use the network as a loading method too.

Disclosure:  I don't manage desktops, only servers and haven't needed to have 20 brought up in 1 day.  1 a week is about the max here.

Oh - an you probably want an apt-cacher-ng server on the network to limit WAN bandwidth.  Get that setup and tested before you start anything.

Also - you can use NFS + LDAP + Kerberos with dynamically mounted HOMEs so that any system self-configures per userid. Then you can swap out PCs and the replacement system becomes the users immediately at login.  A good storage network is needed for this, of course. 100Mbps is fine, unless video is part of your core business.

This sounds like tons of fun to me!

---

### Post by JazzPotato on 2014-10-15
What about drbl? Ever used that?

---

### Post by TheFu on 2014-10-15
Never used it.  Looks like it uses NIS - which is NOT secure enough to be used inside my house, much less inside any business.

Of course, other people may have different ideas about "secure enough" than I.

NIS+ should be fine, but the only servers I know are Solaris.

---

