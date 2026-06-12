---
title: "OwnCloud in Ubuntu 14.04"
date: 2014-11-08
forum: General Help
---

### Post by Kandoni on 2014-11-08
Hi,

I am trying to install the Owncloud client version in my laptop (running a Ubuntu 14.04 64 bit distro) in order to use an Owncloud account in an external server. I follow [the instructions in the Owncloud documentation]("http://doc.owncloud.org/desktop/1.6/installing-linux.html#installing-linux"). I have tried [both ways]("https://software.opensuse.org/download/package?project=isv:ownCloud:desktop&package=owncloud-client") the normal way running 
```
sudo sh -c "echo 'deb http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/xUbuntu_14.04/ /' >> /etc/apt/sources.list.d/owncloud-client.list"
sudo apt-get update
sudo apt-get install owncloud-client
```

and the optional way downloading the apt-key for the Ubuntu repository:
```
wget http://download.opensuse.org/repositories/isv:ownCloud:desktop/xUbuntu_14.04/Release.key sudo apt-key add - < Release.key
```

But I get the same error in the terminal:
```
[COLOR=#ff0000]W: Duplicate sources.list entry http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/xUbuntu_14.04/  Packages (/var/lib/apt/lists/download.opensuse.org_repositories_isv:_ownCloud:_desktop_xUbuntu%5f14.04_Packages)
W: Duplicate sources.list entry http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/xUbuntu_14.04/  Packages (/var/lib/apt/lists/download.opensuse.org_repositories_isv:_ownCloud:_desktop_xUbuntu%5f14.04_Packages)
W: Tal vez quiera ejecutar «apt-get update» para corregir estos problemas[/COLOR]

```

If I run again > sudo apt-get update I get the same message at the terminal

How could I solve this error about the duplicate sources list?

Thanks in advance, I appreciate any help to solve it.

Kandoni

---

### Post by nerdtron on 2014-11-08
Post the contents of the /etc/apt/sources.list.d/owncloud-client.list here.

Since you ran the echo command more than once with the >> operator, the lines will be appended and you'll have a duplicate entry.

---

### Post by Kandoni on 2014-11-08
> **nerdtron said:**
> Post the contents of the /etc/apt/sources.list.d/owncloud-client.list here.

Since you ran the echo command more than once with the >> operator, the lines will be appended and you'll have a duplicate entry.

The *owncloud-client.list* file content is:
```
deb http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/xUbuntu_14.04/ /
deb http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/xUbuntu_14.04/ /
deb http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/xUbuntu_14.04/ /
```

And there is another file in the same folder named *owncloud-client.list.save* with this content:
```
deb http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/xUbuntu_14.04/ /
# deb http://download.opensuse.org/repositories/isv:/ownCloud:/desktop/xUbuntu_14.04/ /
```

---

### Post by nerdtron on 2014-11-08
You have duplicate entries on your owncloud-client.list. Just edit the file directly and leave only the first line.

owncloud-client.list.save is probably a temp file for your editing program.

---

### Post by Kandoni on 2014-11-08
> **nerdtron said:**
> You have duplicate entries on your owncloud-client.list. Just edit the file directly and leave only the first line.

owncloud-client.list.save is probably a temp file for your editing program.

That worked!!

Thanks a lot **nerdtron**!! ;)

---

