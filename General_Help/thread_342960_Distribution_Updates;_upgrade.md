---
title: "Distribution Updates; upgrade?"
date: 2007-01-20
forum: General Help
---

### Post by Steve S. on 2007-01-20
Ok, this is new in Edgy that I didn't see in Dapper, so bear with me.

When the computer runs automatic updates and tells me "You have new packages to install/update!" or whatever it says, it lists out the ones that it is going to update, each one checked in the gui.

But there is also a category labelled: Distribution Updates.  None of these are checked and they never get updated, and the list is getting longer.

The question is, how do I update these items on the list?

I DON'T want to upgrade to Feisty, as Edgy upgrade was a big enough headache, and I like how it is settup now.  So, if that is my only option, then I'll just let the list get bigger.

Anyone else wondering about this?  How can it be fixed?

---

### Post by yopnono on 2007-01-20
What happens if you open synaptic and click "mark all upgrades" then click apply?

---

### Post by Steve S. on 2007-01-20
> **yopnono said:**
> What happens if you open synaptic and click "mark all upgrades" then click apply?

Nothing.  Actually, it does what it's supposed to do, just no other updates (namely the ones that I'm speaking of) are updated.  It seems I've marked all I can for upgrade via that route...good suggestions, though.

I even went so far as to check my /etc/apt/sources.list to see if I had for some reason left something commented out, but all is set to be updated.

So, up to this point, I have been running sudo aptitude update and going back to the "Mark all Upgrades" button to see if I might take care of those that I'm speaking of, to no avail.

Thanks for the suggestion...what else can we try?

---

### Post by yopnono on 2007-01-20
And if you run sudo aptitude update and then sudo aptitude upgrade

---

### Post by Steve S. on 2007-01-20
> **yopnono said:**
> And if you run sudo aptitude update and then sudo aptitude upgrade

I haven't run sudo aptitude upgrade 'cause I don't know what that does.

Does it upgrade the distro?  I have run sudo aptitude dist-upgrade when I was upgrading a distro...is this the same thing?

I REALLY _don't_ want to upgrade to Feisty...so I'm just being overly cautious.

Can you tell me exactly what sudo aptitude upgrade does that is different than sudo aptitude update?

---

### Post by dschaller on 2007-01-20
You won't upgrade to Feisty by accident. If your sources.list file shows all Edgy, even doing a dist-upgrade will only bring you to the latest Edgy.

Running 'update' checks the repositories for new or updated software. It does not install anything. Running 'upgrade' installs the latest versions of packages. Running 'dist-upgrade' installs new packages and tries to resolve any dependency problems by adding/removing whatever other packages are necessary.

Sometimes, packages are intentionally held back on an upgrade. I think this is what you're seeing in your "distribution update" section. Look here under "Notes":
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

I have a few in my "distribution update" list too. If you really care about upgrading them, you might be able to uninstall those packages using apt-get and then reinstall them -- depending on what the packages are. Although if your system works fine as it is, I wouldn't bother.

---

### Post by Steve S. on 2007-01-20
> **dschaller said:**
> You won't upgrade to Feisty by accident. If your sources.list file shows all Edgy, even doing a dist-upgrade will only bring you to the latest Edgy.

Running 'update' checks the repositories for new or updated software. It does not install anything. Running 'upgrade' installs the latest versions of packages. Running 'dist-upgrade' installs new packages and tries to resolve any dependency problems by adding/removing whatever other packages are necessary.

Sometimes, packages are intentionally held back on an upgrade. I think this is what you're seeing in your "distribution update" section. Look here under "Notes":
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

I have a few in my "distribution update" list too. If you really care about upgrading them, you might be able to uninstall those packages using apt-get and then reinstall them -- depending on what the packages are. Although if your system works fine as it is, I wouldn't bother.

Great explanation.  I had read the man pages on aptitude and apt-get and it didn't give a very clear distinction.  You explained it perfectly...

I checked out that sight...it says some may be held back, but doesn't really say why or if there is any reason to it...I'm sure that is what is happening.

I ran sudo aptitude upgrade and sudo apt-get upgrade (I know the difference, but I wanted to see if there was any difference in the result).  I got this both times:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  eric libggi2 mplayer python-adns python-clientcookie python-crypto
  python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools
  python-egenix-mxtools python-gadfly python-htmlgen python-htmltmpl
  python-jabber python-kjbuckets python-ldap python-mysqldb python-pam
  python-pexpect python-pgsql python-pylibacl python-pyopenssl python-pyxattr
  python-qt3 python-qtext python-reportlab python-simpletal python-soappy
  python-sqlite python-syck python-xmpp
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
```

This is the same list of items that is under the "Distribution Updates" category in the gui.

This is nothing I need to be concerned with, huh?

---

### Post by Steve S. on 2007-01-20
Oh, and here is a picture of the gui, just for the sake of records:

---

### Post by yopnono on 2007-01-22
You can always just simply remove the packages, then install them again.

```
sudo aptitude remove eric libggi2 mplayer python-adns python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools
python-egenix-mxtools python-gadfly python-htmlgen python-htmltmpl
python-jabber python-kjbuckets python-ldap python-mysqldb python-pam
python-pexpect python-pgsql python-pylibacl python-pyopenssl python-pyxattr
python-qt3 python-qtext python-reportlab python-simpletal python-soappy
python-sqlite python-syck python-xmpp
```


```
sudo aptitude install eric libggi2 mplayer python-adns python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools  python-egenix-mxtools python-gadfly python-htmlgen python-htmltmpl
python-jabber python-kjbuckets python-ldap python-mysqldb python-pam
python-pexpect python-pgsql python-pylibacl python-pyopenssl python-pyxattr
python-qt3 python-qtext python-reportlab python-simpletal python-soappy
python-sqlite python-syck python-xmpp
```

---

### Post by gercokees on 2007-01-23
Googling, i found this...:
[http://www.debian-administration.org/articles/69](http://www.debian-administration.org/articles/69)

intresting article

---

### Post by Steve S. on 2007-01-23
> **gercokees said:**
> Googling, i found this...:
[http://www.debian-administration.org/articles/69](http://www.debian-administration.org/articles/69)

intresting article

Good article!  Although I'm still a little scared to run dist-upgrade...I know what the logic is, but it is still a little nerve wracking...

I tried the uninstall, install route (thanks yopnono), but it got some of them, not all...I may try again.

That article does provide some ideas, though.

---

### Post by Steve S. on 2007-01-26
Well, feeling in an impulsive mood, scrunching my face up in anticipation of the impending doom and back-lash, I quickly typed this in and hit enter:
```
sudo aptitude update && sudo aptitude dist-upgrade
```

And to my surprise and strained releif, the computer did not colapse in on itself and melt into a pool of goo, nor did it install Feisty.

It worked perfectly and fixed the problem.

Thanks to all of you for your help and your input.:D

---

### Post by amadeov on 2007-04-03
I had been having a similar problem after upgrading to edgy... and the solution proposed in this thread finally worked for me. =)

The answer that finally worked for me was typing:

```
sudo aptitude update && sudo aptitude dist-upgrade
```

I had a similar problem to the one described in this thread: a mix of packages that included a lot of python related packages were all being "kept back" repeatedly.  

I'm glad to see that done with! =)

---

### Post by Steve S. on 2007-04-03
> **amadeov said:**
> I had been having a similar problem after upgrading to edgy... and the solution proposed in this thread finally worked for me. =)

The answer that finally worked for me was typing:

```
sudo aptitude update && sudo aptitude dist-upgrade
```

I had a similar problem to the one described in this thread: a mix of packages that included a lot of python related packages were all being "kept back" repeatedly.  

I'm glad to see that done with! =)

;-) The beauty of the forum....glad to see it worked!

---

