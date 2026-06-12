---
title: "List Installed deb packages that has been installed outside of a repository"
date: 2016-07-21
forum: General Help
---

### Post by Jason_Hunter on 2016-07-21
If I download 10 debs from website, ie not from a repository and install them, is there any way to differentiate between them?

Ie, is there any way to list debs' which has been installed manually and not from a repository?

---

### Post by &amp;KyT$0P# on 2016-07-21
Synaptic package manager has a section "Installed (local or obsolete)" where you can see a list of all such packages

---

### Post by Jason_Hunter on 2016-07-24
It does?

Where, on this screenshot? ([http://imgur.com/a/bPmpL](http://imgur.com/a/bPmpL))

[IMG]http://imgur.com/a/bPmpL[/IMG]

---

### Post by &amp;KyT$0P# on 2016-07-24
That's not Synaptic.  I have no idea what that application is :confused:

Are you able to install Synaptic?
```
sudo apt-get --no-install-recommends install synaptic
```
Once you run Synaptic, click the "Status" button (if it's not already selected) and you'll see it.

---

### Post by Jason_Hunter on 2016-07-24
right, excellent; thanks, that worked. 

Is there any way to list these on the command line?

---

### Post by vasa1 on 2016-07-24
> **Jason_Hunter said:**
> It does?

Where, on this screenshot? ([http://imgur.com/a/bPmpL](http://imgur.com/a/bPmpL))

[IMG]http://imgur.com/a/bPmpL[/IMG]

If you don't mind, please use the forum's attachment facility accessible via the paperclip icon *above* the posting area (You may first have to click "Go Advanced" *below* the posting area to make more options visible). See _#4_ in "When asking for technical support" along with other helpful points in [Posting tips and guidelines]("https://ubuntuforums.org/showthread.php?t=2158945")  > If you include screenshots, use the forum attachment system rather than an offsite host such as imgurThanks!

> **halogen2 said:**
> That's not Synaptic.  I have no idea what that application is :confused:
...
Seems to be some sort of "software center" or software boutique

---

### Post by &amp;KyT$0P# on 2016-07-24
> **Jason_Hunter said:**
> Is there any way to list these on the command line?
Looks like [FONT=Courier New]aptitude[/FONT] can do it

```
sudo apt-get install aptitude aptitude-doc-en
```

```
aptitude search '?obsolete'
```

---

### Post by vasa1 on 2016-07-24
Or```
apt list --installed | grep local
```

I've so far avoided installing aptitude even though it has some nifty features:```
$ apt install --no-install-recommends -s aptitude
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  aptitude-common libcwidget3v5
Suggested packages:
  apt-xapian-index aptitude-doc-en | aptitude-doc debtags tasksel libcwidget-dev
The following NEW packages will be installed:
  aptitude aptitude-common libcwidget3v5
0 upgraded, 3 newly installed, 0 to remove and 16 not upgraded.
Inst aptitude-common (0.7.4-2ubuntu2 Ubuntu:16.04/xenial [all])
Inst libcwidget3v5 (0.5.17-4ubuntu2 Ubuntu:16.04/xenial [amd64])
Inst aptitude (0.7.4-2ubuntu2 Ubuntu:16.04/xenial [amd64])
Conf aptitude-common (0.7.4-2ubuntu2 Ubuntu:16.04/xenial [all])
Conf libcwidget3v5 (0.5.17-4ubuntu2 Ubuntu:16.04/xenial [amd64])
Conf aptitude (0.7.4-2ubuntu2 Ubuntu:16.04/xenial [amd64])
$ 
```

---

### Post by Jason_Hunter on 2016-07-25
Great; got it; thanks;)

---

