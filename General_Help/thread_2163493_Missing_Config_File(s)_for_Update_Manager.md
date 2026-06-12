---
title: "Missing Config File(s) for Update Manager?"
date: 2013-07-18
forum: General Help
---

### Post by BuntuSeriously on 2013-07-18
Good day.

Was interested to know where the run prefs (as shown in the "Software Sources" dialog) for Update Manager are stored on 12.04.

Dug until my fingers bled with both Catfish and GConf Editor; with no success...

Any ideas?

Thanks --

---

### Post by gifford on 2013-07-18
Try /etc/apt/sources.list.d
Is this what you were looking for?

---

### Post by BuntuSeriously on 2013-07-18
@gifford:

Thanks for the input!

However, there's nothing in /etc/apt/sources.list.d on my side :???:

Browsing /etc/apt/apt.conf.d did unearth a couple of files; but nothing akin to what I think is a fit...

Specifically, I was interested in determining where the checkbox- and dropdown-based option choices, as shown on the "Ubuntu Software," "Other Software," and "Updates" tabs of the "Software Sources" dialog, could be found...

Thanks again ;)

---

### Post by BuntuSeriously on 2013-07-18
OK.  Got a free moment to shoot a couple more things (as clues?) out onto the table...

Again, here's what I'm trying to do:

I was interested in determining where the checkbox- and dropdown-based  option choices, as shown on the "Ubuntu Software," "Other Software," and  "Updates" tabs of the "Software Sources" dialog, could be found.

So, just guessing this might be the neighborhood where such things live, here's what the content of my /etc/apt/apt.conf.d folder looks like:

00trustcdrom
01autoremove
10periodic
15update-stamp
20archive
20dbus
50unattended-upgrades
70debconf
99synaptic
99update-notifier

Again, can't seem to see anything which would look like a good old-fashioned ini file to set the selections/prefs on the "Software Sources" dialog.

Am I missing something?  Is this the wrong tree???

:-?

Thanks again . . .

---

### Post by steeldriver on 2013-07-18
Like gifford says, afaik it's just reading the same files that commandline apt-get would i.e. your /etc/apt/sources.list file plus whatever additional repositories you have in /etc/apt/sources.list.d

e.g. if I look at my 'partner' repositories

```

$ grep partner /etc/apt/sources.list
## 'partner' repository.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner
deb http://archive.canonical.com/ precise partner
deb-src http://archive.canonical.com/ precise partner

```

and then if I fire up update manager and check the previously deselected 

[INDENT][FONT=fixedsys][B]Canonical partners
[/B]Software packaged by canonical for their partners
[/FONT][/INDENT]
[FONT=fixedsys] [/FONT]
item (plus source), then immediately those additional sources become uncommented in /etc/apt/sources.list

```

$ grep partner /etc/apt/sources.list
## 'partner' repository.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner
deb http://archive.canonical.com/ precise partner
deb-src http://archive.canonical.com/ precise partner

```

---

### Post by BuntuSeriously on 2013-07-19
@steeldriver:

Thank you for the information.

However, I'm not concerned entirely with changing the repository preferences (although this is quite helpful); I also need to change some other selections on the aforementioned UI tabs.

Here's another example of what I'm looking for:

Anyone who has access to the box sits down & clicks the "Settings" button on the Update Manager applet.  The user is presented with a tabbed-dialog that contains choices which govern whether or not the user is bugged by daily, weekly, or no nags regarding updates which are in the chute.  I'm looking for the config file which tracks this stuff as well...

;)

---

### Post by steeldriver on 2013-07-19
Those would be in the dconf database (not a 'file' as such) - you can access it via gsettings or dconf (iirc requires installation of the dconf-tools package)

```

$ gsettings list-recursively com.ubuntu.update-notifier
com.ubuntu.update-notifier auto-launch true
com.ubuntu.update-notifier end-system-uids 500
com.ubuntu.update-notifier hide-reboot-notification false
com.ubuntu.update-notifier no-show-notifications false
**[COLOR=#0000cd]com.ubuntu.update-notifier regular-auto-launch-interval 0[/COLOR]**
**[COLOR=#0000cd]com.ubuntu.update-notifier release-check-time uint32 1373342054[/COLOR]**
com.ubuntu.update-notifier show-apport-crashes true

```

```

$ dconf dump /com/ubuntu/update-notifier/

[/]
[B][COLOR=#0000cd]regular-auto-launch-interval=0
release-check-time=uint32 1373342054[/COLOR][/B]

```

---

### Post by BuntuSeriously on 2013-07-20
@steeldriver:

Thanks a bunch for the skinny on this.

Have a great weekend . . .

:)

---

