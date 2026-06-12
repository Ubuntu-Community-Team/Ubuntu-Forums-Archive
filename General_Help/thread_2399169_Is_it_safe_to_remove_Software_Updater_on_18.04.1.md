---
title: "Is it safe to remove Software Updater on 18.04.1 ?"
date: 2018-08-22
forum: General Help
---

### Post by pretty_whistle on 2018-08-22
I have Ubuntu 18.04.1.

I want to remove Software Updater (update notifier) but is it safe to do so considering it removes these as well:

[IMG]https://imgur.com/a/JfaDY27[/IMG][IMG]https://imgur.com/a/JfaDY27[/IMG]ubuntu-desktop
ubuntu-release-upgrader-gtk
update-manager

??

Thanks for the help!

---

### Post by TheFu on 2018-08-22
yes.  I assume you want to manually patch.
Just be certain to do manual patching weekly.

BTW, I think that stupid every-day repo checker task will still try to run, but it won't be able to do anything, which it good, IMHO.

Personally, if I wanted updates or patches forced on my systems, I'd still be using a different OS that forces exactly that.  Ok, maybe that's a lie. ;)

---

### Post by &amp;KyT$0P# on 2018-08-22
You can do it, but I think you would lose the ability to [phased updates]("https://wiki.ubuntu.com/PhasedUpdates").

Why do you want to remove Software Updater?

---

### Post by pretty_whistle on 2018-08-22
> **halogen2 said:**
> You can do it, but I think you would lose the ability to [phased updates]("https://wiki.ubuntu.com/PhasedUpdates").

Why do you want to remove Software Updater?

Correct, I would lose the ability to phased updates as it says here :

> [COLOR=#333333][FONT=&quot]Update Manager is currently the only package manager that supports phased updates. Any other update mechanism installs [/FONT][/COLOR]*all*[COLOR=#333333][FONT=&quot] updates regardless of the Phased-Update-Percentage.[/FONT][/COLOR]

As to why I want to remove it, it wouldn't stop alerting me to updates in the last LTS I had, even after applying fixes, so I removed it. I just don't want more trouble again.

---

### Post by TheFu on 2018-08-22
You can always put it back later.

---

### Post by pretty_whistle on 2018-08-22
Well, to refine my question a bit more what is "ubuntu-desktop" (it's the first on the list of what's removed that I mentioned above)? It sounds important, or is that just me?[COLOR=#000000]
Here's a search on "ubuntu-desktop":

[https://packages.ubuntu.com/search?searchon=names&keywords=ubuntu-desktop](https://packages.ubuntu.com/search?searchon=names&keywords=ubuntu-desktop)

It says :

> [/COLOR]
[LIST]
[*][bionic (18.04LTS)]("https://packages.ubuntu.com/bionic/ubuntu-desktop") (metapackages): The Ubuntu desktop system 
1.417: amd64 arm64 armhf i386 ppc64el s390x
[/LIST]
[COLOR=#000000]
Looks important to me.[/COLOR]

---

### Post by TheFu on 2018-08-22
> **pretty_whistle said:**
> Well, to refine my question a bit more what is "ubuntu-desktop" (it's the first on the list of what's removed that I mentioned above)? It sounds important, or is that just me?

It isn't.   That is just a meta-package filled with other packages.  By removing any 1package from that meta-package, it is removed too, but all the other packages are still left on the system and work just as before.

---

### Post by pretty_whistle on 2018-08-22
> **TheFu said:**
> It isn't.   That is just a meta-package filled with other packages.  By removing any 1package from that meta-package, it is removed too, but all the other packages are still left on the system and work just as before.

Ok, thanks.

Time to remove the varmint. Thanks to everyone for your help. I'll mark this solved.

---

### Post by missmoondog on 2018-08-23
call me stupid, i guess, but why not simply open synaptic and under settings, tell it to never check for updates? that's what i've always done and i've NEVER seen my software updater telling me anything. i do manually check for updates, sometimes several times a day even, and install them then.

as far as what TheFu says, since when does ANY linux distro FORCE updates on you? that's one of the things i like about linux and it's NOT forcing updates like certain other OS's do!

---

### Post by &amp;KyT$0P# on 2018-08-23
> **missmoondog said:**
> why not simply open synaptic and under settings, tell it to never check for updates? 
Because that doesn't always work.  In my case I had to uninstall unattended-upgrades.

> since when does ANY linux distro FORCE updates on you?
Last I checked, snapd forces automatic updates.

---

