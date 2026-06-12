---
title: "Install Flash on Vivaldi"
date: 2017-08-21
forum: General Help
---

### Post by earthtoaccess on 2017-08-21
So. Newbie Ubuntu user-- currently using it via VirtualBox VM.
Trying to install Flash onto [Vivaldi Browser]("http://vivaldi.com"), but there's an issue.

See, to install, I need to input this code into Terminal;

```

sudo add-apt-repository "deb http://archive.canonical.com/ubuntu `lsb_release -cs` partner"
sudo apt update
sudo apt install adobe-flashplugin

```

Problem is, when I attempt to do ***that***, I am greeted with the following error within the first command entry:

```

sudo: error in /etc/sudo.conf, line 0 while loading plugin `sudoers_policy'
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins

```

I can't use anything Flash Player is required, such as I usually test Flash Player's performance on VMs by making a song via [AudioSauna]("http://audiosauna.com/studio").
How would I even fix such a thing? **[FONT=courier new]sudo chmod[/FONT]** isn't doing much help either.

---

