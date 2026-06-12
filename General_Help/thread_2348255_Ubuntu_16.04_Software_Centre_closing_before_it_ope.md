---
title: "Ubuntu 16.04 Software Centre closing before it opens"
date: 2017-01-02
forum: General Help
---

### Post by pcal on 2017-01-02
Hi guys,

Have been having issues for a little while on an AMD 64bit desktop 16.04 installation (ever since upgrading from 14.04) where the Software Centre took ages to do anything. It would open, but have no contents for a long while (4 or 5 minutes) while it was "loading". Then any search for anything would have a similar long delay. But at least, it did work.

For the last couple of weeks however, the Software Centre won't open at all. Occasionally, it's window will flash on the screen for no more than a second before closing itself, but more often than not, it's icon on the unity panel will flash, and then just stop flashing with nothing on screen at all.

Not sure if it's related, but more often than not I'm also getting an Error message shortly after booting citing an "Internal Error in Ubuntu" and asking permission to make a report about it. The system still seems to be working after making its report, but for the Software Centre issue above.

Any clues?

---

### Post by sudodus on 2017-01-02
Please install the Synaptic package manager

```
sudo apt-get install synaptic
```

and try if it works better than the Software Center. That way you can determine if the problem is with the Software Center or with the updating software under the hood or maybe the server, that you are using for updating/upgrading. And maybe you will get a tool that works.

---

### Post by pcal on 2017-01-02
> **sudodus said:**
> Please install the Synaptic package manager

```
sudo apt-get install synaptic
```

and try if it works better than the Software Center. That way you can determine if the problem is with the Software Center or with the updating software under the hood or maybe the server, that you are using for updating/upgrading. And maybe you will get a tool that works.

Thanks sudodus.

Synaptic installed and ran fine, but did report several errors trying to connect to the repositories...

```
The repository 'http://extras.ubuntu.com/ubuntu xenial Release' does not have a Release file.Data from such a repository can't be authenticated and is therefore potentially dangerous to use.See apt-secure(8) manpage for repository creation and user configuration details.
[http://downloads.makerbot.com/makerware/ubuntu/dists/xenial/Release.gpg:](http://downloads.makerbot.com/makerware/ubuntu/dists/xenial/Release.gpg:) Signature by key ABB736EB5F9C4CF4A25277973D019B838FB1487F uses weak digest algorithm (SHA1)GPG error: 
[http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2F683C52980AECFThe repository 'http://download.virtualbox.org/virtualbox/debian xenial InRelease' is not signed.Data from such a repository can't be authenticated and is therefore potentially dangerous to use.See apt-secure(8) manpage for repository creation and user configuration details.
Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/xenial/main/source/Sources](http://extras.ubuntu.com/ubuntu/dists/xenial/main/source/Sources)  404  Not Found [IP: 91.189.92.152 80]Some index files failed to download. They have been ignored, or old ones used instead.
```

The Makerbot and Virtualbox repositories are no big deal as I need to do them manually anyway, but the Ubuntu repositories not being available is a little more concerning...

---

### Post by sudodus on 2017-01-02
You can try with another server. ***In Synaptic:*** select the pull-down menu

Settings - Repositories - tab Software for Ubuntu

Download from: *select another server.* It might work better.

---

### Post by pcal on 2017-01-29
Sorry it took a little while to reply. My daughter is actually getting married next weekend and life is bedlam right now - but finally found a few moments to have another go at it.

After deleting the error causing repositories from the Synaptic setup, I was able to do an update (4 figure sum of files to be updated), after which, the Software Centre is working again! :)

Will have to wait an see if the "internal error" also stops happening after boot...

Thanks for your help.

Pcal

---

