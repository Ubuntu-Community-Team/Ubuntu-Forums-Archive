---
title: "gpg pinentry slow to show up (timeout/delay?)"
date: 2017-05-20
forum: General Help
---

### Post by deragon on 2017-05-20
Since a few weeks, whenever I call 'gpg --decrypt <file>', it takes exactly 25s for the pinentry GUI prompt to show up.  It used to be instantaneous.  Once gpg-agent has the password though, the next 'gpg --decrypt <file>' goes quickly.

Looking around the web, it seams that this is a GTK/DBUS related problem.  I am not the first suffering about this problem, but I have not found a solution on the web.

Here are some links related to the issue:

[LIST=1]
[*][gpg-agent prompt slow to show up]("https://lists.gt.net/gnupg/users/74005")
[*][systemd-logind delayed logins ~25 seconds]("https://ubuntuforums.org/showthread.php?t=2327694")
[/LIST]
...but none gives a solution.  The problem goes away when I configure *~/.gnupg/gpg-agent.conf* with *pinentry-program /usr/bin/pinentry-curses*.  The problem seams related to GTK.

Anybody has a clue what is going on, how to debug this and most of all, how to solve this?

Ubuntu 16.04 LTS, up to date as of 2017-05-20.
gpg-agent (GnuPG) 2.1.11
gpg (GnuPG) 1.4.20

---

### Post by eisd on 2017-05-25
The delay disappeared for me when switching from **pinentry-gnome3** to **pinentry-gtk2**, in my setup (with i3 instead of a full ubuntu/gnome desktop) this works fine and also caused **gnome-keyring** to be auto-removed. This is only a workaround and I may, as far as I know now, have the same trouble if I decide to use **gnome-keyring** for other purposes. I haven't tested out any further combinations.

---

### Post by deragon on 2017-05-26
I tried **pinentry-program /usr/bin/pinentry-gtk-2** in **~/.gnupg/gpg-agent.conf** but it did not work; I still get the 25s delay.  Thanks for the tip though.

---

### Post by deragon on 2017-07-13
Turns out that this is caused by a bug in gnome-keyring-daemon, causing many application including Chrome, Skype and Pinentry to wait for long times before becoming available for use.  This is causing a lot of headaches for many users.

See [Launchpad bug #1689825]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/1689825") for further details.

The workaround consist at running the following in the terminal, as your own user:

[FONT=Courier New]gnome-keyring-daemon --replace --daemonize --components=secrets,ssh,pcks11[/FONT]

---

