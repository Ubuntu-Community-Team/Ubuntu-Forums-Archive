---
title: "Command Line - cloud based backups"
date: 2020-02-21
forum: General Help
---

### Post by Frank P on 2020-02-21
I have been backing up my server - Ubuntu 16.04lts, to a NAS device. I'd like to change to backing it up on a cloud service. Is there any I can access using the command line - I don't want to install a GUI on the server.
Thanks

---

### Post by CelticWarrior on 2020-02-21
Dropbox, Yandex, Mega, etc. etc. Most offer that option. All you have to do is a google search ;).

---

### Post by Frank P on 2020-02-21
Thanks. I did do a google search. Even bought Kindle book about cloud storage :-) It covered Dropbox and a bunch of others but it only mentioned GUI interfaces. I'll look a litle deeper.

---

### Post by CelticWarrior on 2020-02-21
RE: Dropbox:

> (...)
Next, run the Dropbox daemon from the newly created .dropbox-dist folder.
~/.dropbox-dist/dropboxdIf you&#8217;re running Dropbox on your server for the first time, you&#8217;ll be asked to               copy and paste a link in a working browser to create a new account or add your server to an               existing account. Once you do, your Dropbox folder will be created in your home directory.               Download this [Python script]("https://www.dropbox.com/download?dl=packages/dropbox.py") to control Dropbox from the command line. For easy access,               put a symlink to the script anywhere in your PATH.



Source: [https://www.dropbox.com/install-linux](https://www.dropbox.com/install-linux)

YANDEX Disk: [https://yandex.com/support/disk/cli-clients.html](https://yandex.com/support/disk/cli-clients.html)

etc, ...


If you need/want other solution I suggest googling "[cloud service] linux cli".

---

