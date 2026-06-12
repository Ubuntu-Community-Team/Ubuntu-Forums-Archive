---
title: "BitchX package comes preconfigured to connect to irc.ubuntu.com"
date: 2007-12-01
forum: General Help
---

### Post by Stuart Morrow on 2007-12-01
The Ubuntu (universe) package of BitchX is configured by default to connect to irc.ubuntu.com when it is initialised, or when it reconnects after losing its connection.

"rgrep irc.ubuntu.com /usr/lib/bitchx" and "rgrep irc.ubuntu.com /etc/bitchx" both return no lines, which gets me thinking that this is a compiled-in option.

It's irritating when I turn on my computer, ssh into my server and reattach to BitchX, and then find that during the night my ADSL has disconnected then reconnected, and the BitchX's joined irc.ubuntu.com instead of where I was already at.

How should I disable this "feature"?

---

### Post by huwnet on 2007-12-01
Have you checked these files (if they exist)?

~/.bitchxrc
~/.ircservers

---

### Post by Stuart Morrow on 2007-12-03
Neither of those files exist, because so far I've not had to use per-user preferences for it.

I googled the problem, and it turns out that the autojoining is hardcoded behaviour (see [https://bugs.launchpad.net/ubuntu/+source/xchat/+bug/52690](https://bugs.launchpad.net/ubuntu/+source/xchat/+bug/52690) (BitchX uses ircii-pana))

Therefore the solution is to build BitchX from its source code, sans that autojoining option..
```

su     # or sudo -s
mkdir /usr/src/ircii-pana
cd /usr/src/ircii-pana
apt-get source ircii-pana
cd ircii-pana-1.1/debian
vim rules     # or $EDITOR rules

```
In the editor, delete the CONFARG "--with-default-server=irc.ubuntu.com:6667 \", because it's evil lock-in.
```

dch -i

```
$EDITOR comes up.  After the asterisk, write "Removed CONFARGS = --with-default-server=irc.ubuntu.com:6667" if you want to.
```

cd ../..
dpkg-source -b ircii-pana-1.1 ircii-pana_1.1.orig.tar.gz     # This creates the new .dsc file for pbuilder.
pbuilder build ircii-pana_1.1-4ubuntu5.dsc     # Filename may differ for other people at other times.

```

That's how far I get into the rebuilding process, then pbuilder complains that it can't locate the package gdk-imlib1-dev.  aptitude search gdk-imlib1-dev reports that the package exists, and is a virtual package pointing at gdk-imlib11-dev.  gdk-imlib11-dev was already installed on my system.  apt-get install gdk-imlib1-dev does nothing useful, either.  Pay attention to the number of "1"s in the package names in that paragraph.

So far, I have not tried using something like apt-build to recompile it without that CONFARG.  Would apt-build be easier?

---

### Post by hellonull on 2008-04-30
I know this is a bit late, but...

The "problem" you are describing not a problem, but rather behavior that would be expected from any program: a hard-coded default for when the user has not yet set any preferences. To set your startup server preferences, you have to create an .ircservers file.

You can also specify a nick and server when you launch from the command line. For example:
```
$ bitchx NickGoesHere irc.freenode.net:6667
```
Note: the ":6667" is not necessary. I just put it here for illustrative purposes. Bx will assume 6667 as the port unless you specify otherwise.

---

### Post by Stuart Morrow on 2008-04-30
nah, I just switched to Irssi in the meantime. :) Thanks anyway.

---

