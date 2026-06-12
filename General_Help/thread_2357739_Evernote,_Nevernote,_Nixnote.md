---
title: "Evernote, Nevernote, Nixnote"
date: 2017-04-05
forum: General Help
---

### Post by webmanoffesto on 2017-04-05
I'm a heavy Evernote user, I use the web interface. I am looking for an Ubuntu Evernote client, mainly because I think that's the only way I can back up my Evernote notes.
I got this message when I tried to install Nevernote. Is there a better client to use? 

```
$ sudo add-apt-repository ppa:vincent-c/nevernote
This PPA publishes stable releases of Nixnote (formerly Nevernote). If you prefer, you may also pick up Debian packages from upstream, at http://nevernote.sourceforge.net/.
(This PPA is no longer supported and updated; package libssl0.9.8 is not available on Ubuntu releases since Vivid/15.04.)
Please note that I merely provide ready-to-install packages for Ubuntu. I'm not the upstream author; if you have any comments, suggestions, or even a few words of thanks, please contact Randy Baumgarte <randy [at] fbn.cx> directly.

```

---

### Post by dragonfly41 on 2017-04-05
I use [cherrytree]("http://www.giuspen.com/cherrytree/") as my note manager.   It is in Ubuntu Centre.
It is rich in import features but I don't see Evernote import.
Possibly export your files from Evernote in some intermediate common format which can be imported into cherrytree?

---

### Post by ajgreeny on 2017-04-05
Try the download from [http://nevernote.sourceforge.net/](http://nevernote.sourceforge.net/)
That will give you a package of **nixnote2-2.0_amd64.deb**, note the name change, which needs two dependencies on my Xubuntu 16.04, libpoppler-qt5-1 and tidy, both in the repos.

Install gdebi as the best way of installing .deb packages that you have downloaded, trust, and want to install manually; it automatically gets dependencies from the repos if they're needed.

I do not use evernote so will not be able to try this to see if it works, nor do I know anything more about the devs of the application, but assuming it does what it says it does, it should be worth trying yourself.
You will probably have to keep manually checking for upgrades of the package.

---

