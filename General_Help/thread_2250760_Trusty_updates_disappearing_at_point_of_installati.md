---
title: "Trusty updates disappearing at point of installation...!?"
date: 2014-10-30
forum: General Help
---

### Post by Mike_Walsh on 2014-10-30
Evening, all.

Got a mystery..!

I've been away for a couple of days, so when I got back on here about an hour ago, I clicked on 'Software Updater' in the launcher, to see if there was anything to install.

There was:- 

[ATTACH=CONFIG]257621[/ATTACH]

So, I clicked on install, and sat back to let the old girl (stats below, in my signature) get on with it.....always, up till now, hassle-free.

Up comes the installation window:-

[ATTACH=CONFIG]257622[/ATTACH]

Less than 5 seconds later, the window simply vanishes; no updates, no error messages.....nothing. Took a bit of rapid work to catch this with a screenshot before it disappears..!

I've tried this half-a-dozen times, and it's a repeat performance EVERY time. I'm mystified! I've checked every folder I can think of (including my /home folder, which is in its own separate partition, shared with my Lubuntu install. 30 GB+ to spare. Everywhere else, there's plenty of room to spare.....so it's certainly not a space issue.

Is this just me, personally.....or has anybody else noticed this happening over the last couple of days? If it's happening to others, then perhaps it's a problem starting to rear its head.

Any thoughts, please?


Regards,

Mike.

---

### Post by Mike_Walsh on 2014-10-31
_***Update***_

I tried all my other distros for updates too, last night. Zorin quit on me as well; so did Lubuntu & Kubuntu. Xubuntu, however, went ahead and installed the available updates, sweet as a nut.

So; this morning, I tried the others. Started with Ubuntu.....still wouldn't play ball. Then tried Zorin; and it behaved itself! So, too, did Kubuntu & Lubuntu. I then went back to Ubuntu, and this time there was no problem...

I have, through experimentation, and liberal use of the 'ping' test, discovered that 'ubuntu.datahop.net' is the best mirror for my location, here in the UK; so I have all my sources set to that one. It's been consistently reliable.

What appears to have happened is that every time the update process was set in motion, it would quit JUST prior to asking for authentication. Whether or not this was a temporary glitch in the server's software, or interference on the line, I don't know. But it's resolved itself for now.

So if anybody else has had this problem over the last few days, my advice is just to be patient.....and keep trying. It WILL work sooner or later.

Regards,

Mike. ;)

---

### Post by oldos2er on 2014-10-31
I would run ```
sudo apt-get update && sudo apt-get upgrade
``` in a terminal and see if throws any clueful errors.

---

### Post by Mike_Walsh on 2014-10-31
@oldos2er;

I might do that. It's strange how that mirror's been providing my data perfectly for months...and then this. Mind you, I had a little bit of warning on Tuesday, before I went away for a couple of days; I tried updating Kubuntu that afternoon, and it was playing up then.....kept saying the downloads had 'failed due to system errors', but wouldn't tell me what the errors were!

Still, it's working at the moment. I'll just keep my fingers crossed....!

Regards,

Mike.

BTW: Explain one thing to me? What exactly does the 'apt-get upgrade' command do? I always understood this is what upgraded your OS to the next version; and while I'm sure Utopic's very good, I'd much rather stick with Trusty.....I've just got EVERYTHING working the way I want it..!

---

### Post by plucky on 2014-10-31
> BTW: Explain one thing to me? What exactly does the 'apt-get upgrade' command do? I always understood this is what upgraded your OS to the next version; and while I'm sure Utopic's very good, I'd much rather stick with Trusty.....I've just got EVERYTHING working the way I want it..! 

Open a terminal and run ```
man apt-get
``` will give you a description about the "apt-get " commands.

Apt-get is the command line version of the Software Updater.

It will not upgrade to a new Ubuntu version.

Apt-get upgrade will just upgrade currently installed packages.

To install new kernels,you need to use ```
sudo apt-get dist-upgrade
``` command.

The command to upgrade to a new Ubuntu version is ```
sudo do-release-upgrade
```

Good Luck

---

### Post by oldos2er on 2014-10-31
*apt-get upgrade* upgrades packages on your currently installed version of Ubuntu (it has the exact same function as Update Manager). Neither it nor *apt-get dist-upgrade* will update you to a newer version of Ubuntu, as plucky noted. It's important to run it occasionally because it provides security and bug fixes.

---

### Post by sammiev on 2014-10-31
```
sudo apt-get update && sudo apt-get dist-upgrade
```

My usual way of updating.

---

### Post by Mike_Walsh on 2014-10-31
Thanks for the replies, everybody.

That's cleared another little Linux 'mystery' up! Thanks for the info; I shall make a point of incorporating those commands into my normal maintenance routine from now on. Much appreciated.

I'll mark this one as 'Solved', then. Cheers, all!

Regards,

Mike.

---

