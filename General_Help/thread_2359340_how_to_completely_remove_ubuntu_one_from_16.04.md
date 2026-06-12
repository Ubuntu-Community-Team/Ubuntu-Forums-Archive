---
title: "how to completely remove ubuntu one from 16.04"
date: 2017-04-22
forum: General Help
---

### Post by gibbywilson on 2017-04-22
Hello

I have 16.04 and in my top menu I have ubuntu one (a cloud icon)

I am correct that this is no longer a service?

How can I remove it from my computer?

Thanks

---

### Post by deadflowr on 2017-04-22
You can see what ubuntuone packages are installed with
```
dpkg -l | grep ubuntuone
```
Post the output so we can see what you have.

> I am correct that this is no longer a service?
Sort of.
The Ubuntu One file sharing service is done and gone.
But Ubuntu One is the name they call of the single sign-on utility used by all Ubuntu services, such as logging into these forums.

---

### Post by gibbywilson on 2017-04-23
Hello and thanks for your reply

```
$ dpkg -l | grep ubuntuone
ii  deja-dup-backend-ubuntuone                27.3.1-0ubuntu1                               all          Ubuntu One support for Déjà Dup
ii  python-ubuntuone-client                   13.10-0ubuntu1                                all          Ubuntu One client Python libraries
ii  python-ubuntuone-control-panel            13.09-0ubuntu1                                all          Ubuntu One Control Panel - Python Libraries
ii  python-ubuntuone-storageprotocol          13.10-0ubuntu1                                all          Python library for Ubuntu One file storage and sharing service
ii  rhythmbox-ubuntuone                       13.10-0ubuntu1                                all          Ubuntu One Rhythmbox plugin
ii  ubuntuone-client                          13.10-0ubuntu1                                all          Ubuntu One client
ii  ubuntuone-client-data                     15.10+15.10.20151007                          all          Data files for Ubuntu One
ii  ubuntuone-control-panel                   13.09-0ubuntu1                                all          Ubuntu One Control Panel
ii  ubuntuone-control-panel-qt                13.09-0ubuntu1                                all          Ubuntu One Control Panel - Qt frontend
```

---

### Post by deadflowr on 2017-04-23
I had a rather long post I was going to post, but decided the best method would be to try removing each of those packages one by one.
(there seems to have been an issue with the ubuntuone-client-data package that caused it to want to also remove the ubuntu-desktop metapackage, sometime around 14.04, might still affect 16.04)

you would also need to move a couple of folders to your trash.
those are 
.cache/ubuntuone
.config/ubuntuone
.local/share/ubuntuone
and Ubuntu One

the .cache .config and .local folders are hidden folders, not normally viewable.
To see them in Files press ctrl + H
Use Files to move to trash by right clicking on the folders and selecting move to trash 

These folders are all owned by you, so no need to use sudo or root.


Hope it helps

---

### Post by gibbywilson on 2017-04-24
Hi, where is that post on how to remove the above :)

---

### Post by deadflowr on 2017-04-24
> **gibbywilson said:**
> Hi, where is that post on how to remove the above :)

Try this command to remove most of it in one fell swoop:
first try with like this (with the -s (simulate) flag
```
sudo apt-get purge -s deja-dup-backend-ubuntuone python-ubuntuone-client python-ubuntuone-control-panel python-ubuntuone-storageprotocol rhythmbox-ubuntuone ubuntuone-client ubuntuone-control-panel ubuntuone-control-panel-qt
```
this will show you exactly what will be removed, so you can see if any packages not part of the list of packages in the list show and you can then avoid any catastrophes. 
if it looks good remove the -s flag and let it rip, like so
```
sudo apt-get purge  deja-dup-backend-ubuntuone python-ubuntuone-client python-ubuntuone-control-panel python-ubuntuone-storageprotocol rhythmbox-ubuntuone ubuntuone-client ubuntuone-control-panel ubuntuone-control-panel-qt
```

Note that in the list I held back the ubuntuone-client-data package since it seems to be tied to the ubuntu-desktop package, and removing that can break the desktop.(or just cause problems)
Hope it helps

---

### Post by gibbywilson on 2017-04-24
Worked

Thanks :)

---

