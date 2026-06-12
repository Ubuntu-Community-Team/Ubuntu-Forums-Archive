---
title: "Best way to replace Gaim with Pidgin?"
date: 2007-07-04
forum: General Help
---

### Post by ricardisimo on 2007-07-04
[LIST=1]
[*]Source
[*]GetDeb
[*]Debuntu repository
[*]Wait for Gutsy
[/LIST]
Also, do I have to uninstall Gaim first? If so, how do I get around the ubuntu-desktop dependency issues to do that? Thanks in advance for any help.

---

### Post by linuxwizard on 2007-07-04
[https://help.ubuntu.com/community/InstallPidgin2%2e0](https://help.ubuntu.com/community/InstallPidgin2%2e0)

---

### Post by dpar on 2007-07-04
You know, I don't understand why they say on that link to make sure Gaim is not installed. I have them both installed and they both work just fine.

---

### Post by Wiebelhaus on 2007-07-04
what's the advantage to installing pidgin over using a working just fine version gaim?

---

### Post by dpar on 2007-07-04
Curiosity. I installed it a while ago to see if there was a difference. Just never bothered to uninstall.:biggrin:

---

### Post by r0ck80y on 2007-07-04
I didn't find many differences between the two except for some additional protocol support in pidgin: google talk, msn, QQ, Sametime, XMPP etc. And yes, backup your .gaim/ folder if you're keepin gaim before running pidgin for the first time.

---

### Post by Wiebelhaus on 2007-07-04
> **r0ck80y said:**
> I didn't find many differences between the two except for some additional protocol support in pidgin: google talk, msn, QQ, Sametime, XMPP etc. And yes, backup your .gaim/ folder if you're keepin gaim before running pidgin for the first time.

wait a second? did you say googletalk support?


hella sweet... that's reason , thanks for the heads up.

---

### Post by Wiebelhaus on 2007-07-04
nm , my bad.

---

### Post by ricardisimo on 2007-07-05
I'm not seeing any resolution in these instructions for Gaim's dependency issues. Clearly I don't want to remove ubuntu-desktop just to be able to give Pidgin a whirl.

---

### Post by DreamtoStayAwake on 2007-07-06
New Ubuntu user here, with the exact same question. Do we really have to remove Ubuntu Desktop to replace Gaim with Pidgin? Seems nonsensical to me.

---

### Post by hikaricore on 2007-07-06
If by googletalk you mean gmail instant messaging, this has been possible in gaim since as long as I can remember using the Jabber protocol... in Pidgin they just require you to use a different protocol to connect.  Not worth it IMHO, I'm still aggrivated that I can't tell the difference between AIM contacts and other contacts without hovering over them.. >.<

---

### Post by DreamtoStayAwake on 2007-07-06
> **hikaricore said:**
> If by googletalk you mean gmail instant messaging, this has been possible in gaim since as long as I can remember using the Jabber protocol... in Pidgin they just require you to use a different protocol to connect.  Not worth it IMHO, I'm still aggrivated that I can't tell the difference between AIM contacts and other contacts without hovering over them.. >.<

Well that doesn't help those of us for whom GTalk on Gaim isn't working. I've done plenty of searches, read the various discussions about this problem on Google, Ubuntu, and other support sites, and have tried everything they've suggested. No luck. 

An example: [https://answers.launchpad.net/ubuntu/+source/gaim/+question/6858](https://answers.launchpad.net/ubuntu/+source/gaim/+question/6858)

But this really shouldn't be a thread about how to get Gaim to work with GTalk. Why in the world would anyone who is interested in Ubuntu need a reason to want the most up to date version of any given application? Gaim is now Pidgin. That's enough to want to install it. Can anyone help with that? Are there any answers for why it is that Ubuntu Desktop has to be uninstalled in order to uninstall Gaim? Once Gaim is uninstalled, installing Pidgin should be a piece of cake.

---

### Post by hikaricore on 2007-07-06
ubuntu-desktop is a meta package and pretty much safe to remove unless you're upgrading.

Someone mentioned that gtalk works in pidgin, and I thought it was worth mentioning it did in gaim as well.
This is the stock version of gaim that is in the repos.  I've setup gtalk on about 15 different systems using
this version wtih no trouble.  So I can't imagine what your issue might be.

---

### Post by ricardisimo on 2007-07-06
You're telling me that I can uninstall ubuntu-desktop without any consequences?

---

### Post by hikaricore on 2007-07-06
Yea that's what I'm saying.
You'll need to reinstall it before a distribution upgrade IE: Feisty->Gusty but that's about it.

It's not officially recommended to remove it, but it honestly won't hurt anything.

**_ubuntu-desktop:_**

Dependants: 0
Section: Meta Packages
Installed Files:
[I]
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/ubuntu-desktop
/usr/share/doc/ubuntu-desktop/copyright
/usr/share/doc/ubuntu-desktop/changelog.gz[/I]

> The Ubuntu desktop system 
This package depends on all of the packages in the Ubuntu desktop system

It is also used to help ensure proper upgrades, so it is recommended that
it not be removed.

---

### Post by reen254 on 2007-07-06
or still better configure gaim for gtalk as u like.. its very easy dnt just install pidgin cause u think gtalk dnt work on gaim
link..  [http://ubuntuforums.org/showthread.php?t=463175&highlight=5222](http://ubuntuforums.org/showthread.php?t=463175&highlight=5222)

---

### Post by seamus7 on 2007-07-13
I exited out of Gaim then compiled Pidgin from source. I then removed Gaim from my Applications/Internet menu and replaced it with Pidgin in my Sessions Startup list. All went well. I left Gaim installed for now.

Here's how to download, extract and compile Pidgin from the terminal:

1. ```
sudo apt-get build-dep gaim 
```

(see [[COLOR="DarkRed"]_Ubuntu Dependencies_[/COLOR]]("http://developer.pidgin.im/wiki/Installing%20Pidgin#IamonUbuntuhowdoIgetDEPENDENCYinstalledsoIcancompilePidgin"))

2. ```
wget http://easynews.dl.sourceforge.net/sourceforge/pidgin/pidgin-2.0.2.tar.bz2
```
3. ```
bzip2 -dc pidgin-2.0.2.tar.bz2 | tar xvf -
```
4. ```
cd pidgin-2.0.2
```
5. ```
./configure
```
6. ```
make
```
7. ```
sudo make install
```

Alt+F2 Pidgin (Pidgin will show up under Applications/Internet next time you log in)

---

### Post by Nessa on 2007-07-17
Works great. Thanks seamus7! :)

---

### Post by Christopher on 2007-07-17
> **seamus7 said:**
> I exited out of Gaim then compiled Pidgin from source. I then removed Gaim from my Applications/Internet menu and replaced it with Pidgin in my Sessions Startup list. All went well. I left Gaim installed for now.

Here's how to download, extract and compile Pidgin from the terminal:

1. ```
sudo apt-get build-dep gaim 
```

(see [[COLOR="DarkRed"]_Ubuntu Dependencies_[/COLOR]]("http://developer.pidgin.im/wiki/Installing%20Pidgin#IamonUbuntuhowdoIgetDEPENDENCYinstalledsoIcancompilePidgin"))

2. ```
wget http://easynews.dl.sourceforge.net/sourceforge/pidgin/pidgin-2.0.2.tar.bz2
```
3. ```
bzip2 -dc pidgin-2.0.2.tar.bz2 | tar xvf -
```
4. ```
cd pidgin-2.0.2
```
5. ```
./configure
```
6. ```
make
```
7. ```
sudo make install
```

Alt+F2 Pidgin (Pidgin will show up under Applications/Internet next time you log in)


Very nice, TY. :)

---

### Post by Dimitriid on 2007-07-17
> **sx66gns said:**
> wait a second? did you say googletalk support?


hella sweet... that's reason , thanks for the heads up.

Im using google talk with GAIM right now, just use Jabber and set the server to gmail.com and thats it.

What other functionality or differences this pidgin program offers besides that?

---

